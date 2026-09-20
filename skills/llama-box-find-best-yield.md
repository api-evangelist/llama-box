---
name: llama-box-find-best-yield
description: Discover crvUSD yield pools across chains and sources and return the top candidates by APY, using only the free, unauthenticated operations.
api: openapi/llama-box-crvusd-yield-optimizer-openapi.yml
operations: [list_pools_api_pools_get, best_yield_api_best_yield_get]
---

# Find the best crvUSD yield (Chado Studio crvUSD Yield Optimizer)

Base URL `https://llama.box/yo`. Both operations here are free and need no header; the pool set is cached
after the first call (the first `/api/pools` observed took 4.5 s, the next call under 1 ms).

## Steps
1. **best_yield_api_best_yield_get** — `GET /api/best-yield?top=5` for the top-N pools by APY. Narrow with
   `chain` (ethereum, arbitrum, optimism, fraxtal), `source` (scrvusd, llamalend, boosted_lp, crvusd_mint)
   or `risk` as a MAXIMUM risk level (low, medium, high). `top` is 1-50.
2. **list_pools_api_pools_get** — `GET /api/pools` when you need the full set or different ordering:
   `min_apy`, `min_tvl` (USD), `sort_by` (apy, tvl, risk, name), `order` (asc, desc), `limit` 1-500 and
   `offset`. Read `total` to page.
3. Keep each pool's `pool_id` (12-char hash) or `address` — the paid risk and rebalance skills take them.

## Rules
- APY figures include `reward_apy` that may depend on token incentives; `base_apy` is the organic part.
  Convex `boosted_lp` entries carry `extra.il_risk`. Do not present `apy` as guaranteed.
- `tvl` can be tiny (one observed top pool had $1,116 TVL at 41% APY) — filter with `min_tvl` before
  recommending anything sized in the thousands.
- Errors: 422 with `detail[]` when a parameter is out of range. No rate-limit headers are returned.
