---
name: llama-box-ask-the-agent
description: Talk to the crvUSD Yield Optimizer as an A2A agent — read its card, send a natural-language or structured skill request over JSON-RPC (paid $0.01 via x402), and cancel a running task.
api: openapi/llama-box-crvusd-yield-optimizer-openapi.yml
operations: [agent_card__well_known_agent_json_get, a2a_endpoint_a2a_post, a2a_stream_endpoint_a2a_stream_post]
---

# Ask the agent over A2A (Chado Studio crvUSD Yield Optimizer)

## Steps
1. **agent_card__well_known_agent_json_get** — `GET https://llama.box/yo/.well-known/agent.json`. NOTE the
   location: legacy filename, under the `/yo` mount; the host-root paths 404. The card (A2A 0.2.5) lists
   four skills: `best-yield`, `pools`, `risk-score`, `rebalance`, with `defaultInputModes`
   `application/json` and `text/plain`, `streaming: true`, `pushNotifications: false`.
2. **a2a_endpoint_a2a_post** — `POST https://llama.box/yo/a2a` (NOT the card's `url` `https://llama.box/yo`,
   which 404s). JSON-RPC 2.0, methods per the contract: `message/send`, `tasks/get`, `tasks/cancel`
   (legacy aliases `SendMessage`, `GetTask`, `CancelTask`, `ListTasks`). Two request shapes the provider
   documents:
   - natural language: `{"jsonrpc":"2.0","id":1,"method":"message/send","params":{"message":{"role":"user","parts":[{"type":"text","text":"find best yield for 10000 crvUSD"}]}}}`
   - explicit skill: `{"jsonrpc":"2.0","id":1,"method":"message/send","params":{"skill":"best-yield","message":{"role":"user","parts":[{"type":"data","data":{"chain":"ethereum","top":5}}]}}}`
   Unpaid, the endpoint returns **402** with the x402 v2 challenge in `PAYMENT-REQUIRED` ($0.01 USDC,
   eip155:84532, `maxTimeoutSeconds` 300). Pay and resend with `X-PAYMENT`, or send `X-API-Key`.
3. **a2a_stream_endpoint_a2a_stream_post** — `POST https://llama.box/yo/a2a/stream` with the same body for a
   Server-Sent Events stream of task status updates (`message/stream`). Same 402 gate.
4. To stop a running task, call **a2a_endpoint_a2a_post** with `"method":"tasks/cancel"` and the task id
   returned by `message/send`. The contract states only "Cancel a running task" — no window is published.

## Rules
- The card declares no `securitySchemes` and no payment extension, so the 402 is the first place an agent
  learns that calls cost money. Budget $0.01 per `message/send`.
- The challenge's `resource.url` reads `https://llama.box/a2a` (without `/yo`); send the retry to the URL
  you actually called, `https://llama.box/yo/a2a`.
- No idempotency key: a re-sent `message/send` creates (and pays for) a second task.
