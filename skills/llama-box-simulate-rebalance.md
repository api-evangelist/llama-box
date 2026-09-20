---
name: llama-box-simulate-rebalance
description: Submit a current crvUSD allocation and risk tolerance and receive a recommended rebalance (strategy, per-pool actions, blended APY) — a paid $0.01 simulation that moves nothing on-chain.
api: openapi/llama-box-crvusd-yield-optimizer-openapi.yml
operations: [list_pools_api_pools_get, simulate_rebalance_api_rebalance_post]
---

# Simulate a rebalance (Chado Studio crvUSD Yield Optimizer)

Base URL `https://llama.box/yo`. The simulation is advisory: it returns actions for you to take elsewhere
and never signs, deposits or withdraws anything.

## Steps
1. **list_pools_api_pools_get** — `GET /api/pools` to resolve the `address` and `chain` of each pool you
   currently hold.
2. **simulate_rebalance_api_rebalance_post** — `POST /api/rebalance` with the provider's own example shape:
   ```json
   {"current_allocation": [{"pool_address": "0x0655977FEb2f289A4aB78af67BAB0d17aAb84367", "chain": "ethereum", "amount_usd": 5000}],
    "risk_tolerance": "medium", "position_size": 10000}
   ```
   `current_allocation` is required; `risk_tolerance` defaults to `high` in the schema (the example uses
   `medium`, so set it explicitly); `position_size` defaults to 10000.
   - Unpaid: **402** with the x402 v2 challenge in the `PAYMENT-REQUIRED` header ($0.01 USDC on
     eip155:84532). Pay and resend with `X-PAYMENT`, or send a valid `X-API-Key` (the description says
     "Requires pro or enterprise tier").
   - 200 returns `strategy`, `actions[]` (`action`, `pool_name`, `pool_address`, `chain`,
     `current_amount_usd`, `suggested_amount_usd`, `apy`, `reason`), `current_total_usd`,
     `expected_blended_apy` and `rationale`.

## Rules
- Present the output as a recommendation with its `rationale`; the API has no view of gas, slippage or
  your wallet beyond what you sent.
- 422 `detail[]` on a malformed body (e.g. missing `current_allocation`). No idempotency key — a retried
  paid call is charged again.
- There is nothing to cancel or reverse: the call has no side effect.
