---
name: llama-box-assess-pool-risk
description: Score the risk (0-100) of a specific crvUSD pool, paying $0.005 per score through x402 on the Base Sepolia testnet or presenting an X-API-Key.
api: openapi/llama-box-crvusd-yield-optimizer-openapi.yml
operations: [list_pools_api_pools_get, pricing_api_pricing_get, risk_score_api_risk_score__pool_id__get]
---

# Assess a pool's risk (Chado Studio crvUSD Yield Optimizer)

Base URL `https://llama.box/yo`. The risk score is a PAID operation; everything before it is free.

## Steps
1. **list_pools_api_pools_get** — `GET /api/pools?chain=ethereum&limit=50` and pick the pool. Take its
   `pool_id` (12-char hash) or its `address` (0x...); both are accepted as `{pool_id}`.
2. **pricing_api_pricing_get** — `GET /api/pricing` once to confirm the current price list, network and
   `wallet`. On 2026-09-19 it stated `GET /api/risk-score/{pool_id}` at $0.005, USDC, "Base Sepolia testnet
   (eip155:84532)".
3. **risk_score_api_risk_score__pool_id__get** — `GET /api/risk-score/{pool_id}`.
   - Without payment you get **402** with an empty body and a `PAYMENT-REQUIRED` header (base64 JSON, x402
     v2): `accepts[0]` gives `scheme: exact`, `network`, `asset`, `amount` (base units), `payTo`,
     `maxTimeoutSeconds: 300`.
   - Sign the payment those parameters describe and resend the SAME request with an `X-PAYMENT` header
     (provider's how_it_works). A 200 returns `risk_score` (0-100, higher = riskier), `risk_level`,
     `factors[]` and `recommendation`.
   - Alternatively send `X-API-Key`; a bad key returns 401 `{"detail":"Invalid API key"}`. Key issuance is
     not published — contact api@chado.studio.

## Rules
- An unknown `pool_id` returns 404 `{"detail":"Pool not found: ..."}` BEFORE the payment gate, so validate
  ids for free by calling the endpoint once unpaid.
- Each paid call settles separately; there is no idempotency key. Do not retry a call that may have
  succeeded without accepting a second charge.
- The settlement network is a testnet; the value is faucet USDC, not real money — but treat the flow as
  production-shaped.
