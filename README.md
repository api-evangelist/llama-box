# Chado Studio

<!-- API-EVANGELIST-PROVENANCE:BEGIN -->
> ### About this repository
>
> **This is not our API.** This repository is an independent, third-party profile of a company's
> **publicly available** API surface, maintained by [API Evangelist](https://apievangelist.com).
> API Evangelist does not operate, host, resell, or support this company's APIs, and is not
> affiliated with or endorsed by the company unless stated on the profile.
>
> **Where the information came from.** Everything here is assembled from material a member of the
> public can reach with a browser and no credentials — the company's own website, developer portal
> and documentation, the specifications it publishes for public use (OpenAPI, AsyncAPI, JSON Schema,
> `apis.json`, `llms.txt` and similar), its public repositories, and its public status, pricing and
> changelog pages. **Nothing here is obtained by breaching a system, defeating an access control, or
> using credentials of any kind.**
>
> **The rating is an independent assessment.** The Kin Score and Agent Readiness rating are
> independently calculated scores of a company's *public* API artifacts, produced by API Evangelist
> against a published rubric. They are not certifications, endorsements, security assessments, or
> audits, and they score published artifacts — not the quality, safety, or security of the software.
>
> **Corrections, re-scores, and removal are free.** No partnership, contract, or purchase is
> required, and you do not need to justify the request.
>
> - **Something wrong?** Open an issue on this repository, or email
>   [info@apievangelist.com](mailto:info@apievangelist.com).
> - **Published something new?** Ask for a re-score and we will re-run the rating.
> - **Want the listing taken down?** Say so and we will honor it. The profile is reduced to your
>   company name, a factual description, and a link to your own site, and the company is recorded as
>   **unrated** — never scored zero for having asked.
>
> **Response times.** Acknowledgement within **one business day**; removal or restriction within
> **two business days**; corrections and re-scores within **five business days**.
>
> **Not from the company, and here with a question?** You are welcome here — we would rather be the
> front line and point you the right way than have a good report go nowhere. What this repository
> can answer is narrow, though, so it is worth knowing who you are actually looking for:
>
> - **A question about how the API works, an account, billing, or a bug in the service** — that is
>   the company's own support, not us. We profile this API; we do not operate it and cannot see
>   your account.
> - **A bug in an open-source project we only catalog** — file it on that project's own repository.
>   This has happened with a real and correct bug report that reached us instead of the people who
>   could fix it, which helped nobody.
> - **Anything about this listing itself** — the description, the tags, the rating, a missing or
>   wrong artifact — is ours. Open an issue here.
> - **Not sure, or something general about API Evangelist or APIs.io** — open an issue on the
>   [APIs.io Inbox](https://github.com/api-search/inbox) and we will route it.
>
> **This repository contains no software, and we will never ask you to download anything.** There is
> no build, release, installer, or binary here — only text and machine-readable API descriptions, so
> there is nothing here that can be "corrupt" or need "repairing". Any issue, comment, or email
> claiming otherwise and offering a download link is not from us and is hostile. Do not follow the
> link; it is a lure. Report it to GitHub and, if you like, tell us at
> [info@apievangelist.com](mailto:info@apievangelist.com) so we can take it down.
>
> **On a security or compliance team?** Email
> [info@apievangelist.com](mailto:info@apievangelist.com) with *security* in the subject line and
> you will get a person, not a form. We will tell you exactly which public URLs this profile was
> built from so your team can see the same surface we did, and we will take the listing down on
> request while you work through it.
>
> Full detail: **[Where this data comes from](https://apievangelist.com/about/where-our-data-comes-from)**
<!-- API-EVANGELIST-PROVENANCE:END -->

Chado Studio (contact api@chado.studio) operates llama.box, a desktop-style hub for the Curve Finance ecosystem — dashboards, analytics and curated links for Curve, crvUSD, LlamaLend, YieldBasis, Convex, Stake DAO, Yearn and Resupply. Its one machine-readable surface is the crvUSD Yield Optimizer, a FastAPI service mounted at https://llama.box/yo that discovers crvUSD yield across scrvUSD, LlamaLend, Convex and StakeDAO on Ethereum, Arbitrum, Base, Optimism and Fraxtal, scores pool risk 0-100 and simulates rebalances. It publishes an OpenAPI 3.1.0 contract (10 operations) at /yo/openapi.json with Swagger UI and ReDoc, an A2A 0.2.5 agent card at /yo/.well-known/agent.json declaring four skills, and charges for the risk, rebalance and A2A calls per request through the x402 protocol in USDC on the Base Sepolia testnet. The hub itself serves an llms.txt and a robots.txt that allows every major AI crawler.

**Areas:** Agents · A2A · x402 · DeFi · Yield · Curve Finance · crvUSD · Stablecoins · Risk Scoring · Analytics · Agent-Native

## Chado Studio on APIs.io

Everything profiled for Chado Studio is published on APIs.io rather than in this repository. Start at the provider page — **[apis.io/providers/llama-box/](https://apis.io/providers/llama-box/)** — or go straight to one of the APIs or properties below.

### APIs (10)

- [crvUSD Yield Optimizer A2A Agent](https://apis.io/apis/llama-box/crvusd-yield-optimizer-a2a-agent/) — Agent2Agent surface of the same service: an agent card at https://llama.box/yo/.well-known/agent.json (protocolVersion 0.2.5, version 1.1.0, provider "Chado…
- [Chado Studio A2a API](https://apis.io/apis/llama-box/llama-box-a2a-api/) — The A2a API from Chado Studio — 2 operation(s) for a2a.
- [Chado Studio Access Log API](https://apis.io/apis/llama-box/llama-box-access-log-api/) — The Access Log API from Chado Studio — 1 operation(s) for access log.
- [Chado Studio Best Yield API](https://apis.io/apis/llama-box/llama-box-best-yield-api/) — The Best Yield API from Chado Studio — 1 operation(s) for best yield.
- [Chado Studio Health API](https://apis.io/apis/llama-box/llama-box-health-api/) — The Health API from Chado Studio — 1 operation(s) for health.
- [Chado Studio Pools API](https://apis.io/apis/llama-box/llama-box-pools-api/) — The Pools API from Chado Studio — 1 operation(s) for pools.
- [Chado Studio Pricing API](https://apis.io/apis/llama-box/llama-box-pricing-api/) — The Pricing API from Chado Studio — 1 operation(s) for pricing.
- [Chado Studio Rebalance API](https://apis.io/apis/llama-box/llama-box-rebalance-api/) — The Rebalance API from Chado Studio — 1 operation(s) for rebalance.
- [Chado Studio Risk Score API](https://apis.io/apis/llama-box/llama-box-risk-score-api/) — The Risk Score API from Chado Studio — 1 operation(s) for risk score.
- [Chado Studio .well Known API](https://apis.io/apis/llama-box/llama-box-well-known-api/) — The .well Known API from Chado Studio — 1 operation(s) for .well known.

### Published properties

Each property below is a page on APIs.io carrying the machine-readable artifact and what it says.

#### MCP servers (1)

Model Context Protocol servers that expose the API to agents.

- [llama-box-crvusd-yield-optimizer](https://apis.io/servers/llama-box/llama-box-crvusd-yield-optimizer/)

#### Agentic access (1)

Which operations an agent can call, which act, and which need a human in the loop.

- [Llama Box Agentic Access](https://apis.io/agentic-access/llama-box/llama-box-agentic-access/)

#### Overlays (1)

OpenAPI overlays, including conversational phrasing for each operation.

- [Llama Box Crvusd Yield Optimizer Overlay](https://apis.io/overlays/llama-box/llama-box-crvusd-yield-optimizer-overlay/)

#### Security (2)

Authentication, trust centre, and vulnerability disclosure.

- [Llama Box Authentication](https://apis.io/security/llama-box/llama-box-authentication/)
- [Llama Box Domain Security](https://apis.io/security/llama-box/llama-box-domain-security/)

#### Plans and pricing (1)

Published plans, tiers and prices.

- [Llama Box Plans Pricing](https://apis.io/plans/llama-box/llama-box-plans-pricing/)

#### Rate limits (1)

Published request limits.

- [Llama Box Rate Limits](https://apis.io/rate-limits/llama-box/llama-box-rate-limits/)

## Where to find this API

Links to the company's own pages. This repository publishes no copy of their specifications — the canonical document is theirs and lives at the URLs below.

- [Website](https://llama.box/)
- [Documentation](https://llama.box/yo/redoc)
- [API reference](https://llama.box/yo/docs)
- [Pricing](https://llama.box/yo/api/pricing)

## API Evangelist rating

**Kin Score 33.5** — thin · rubric 0.24.0 · scored 2026-10-17

| Facet | Score |
|---|---|
| Discoverability | 78.6 |
| Contract quality | 40.6 |
| Contract governance | 18.2 |
| Operational transparency | 0.0 |
| Developer ergonomics | 37.5 |
| Access clarity | 31.6 |

**Agent readiness 29.9** — agent-ready

| Agent-readiness dimension | Result |
|---|---|
| Spec Presence | yes |
| Agentic Access | derived (partial credit) |
| Reversibility Documented | — |
| MCP Server | — |
| Auth Clarity | bearer (partial credit) |
| Idempotency | — |
| Error Semantics | verified |
| OpenAPI Examples | — |
| Rate Limit Signal | documented (partial credit) |
| Event Surface Described | — |
| Agent Skills | derived (partial credit) |
| Well Known Catalog | — |
| Consent Identity | — |
| Agent Card | near-conformant (partial credit) |
| Dry Run Mode | — |
| Delegated Identity | — |
| Protected Resource Metadata | — |
| Dynamic Client Registration | — |
| Agentic Commerce | — |

**Regulatory alignment 16.7** — Horizontal (data, software, accessibility, platform)

The rubric is published at [github.com/api-evangelist/kin-score](https://github.com/api-evangelist/kin-score). The per-check breakdown behind these numbers — which checks were earned, partial or missed — along with score history and how this provider compares to its peers, is available at [apis.io/providers/llama-box/](https://apis.io/providers/llama-box/).

## How this profile is made

API Evangelist profiles a company's public API surface the way a developer would find it: the website, developer portal and documentation, the specifications it publishes, its public repositories, and its pricing, status and changelog pages. From that it derives the properties above — contracts split per API, workflows, schemas, collections, governance rules, plans and rate limits — and scores them against the published [Kin Score rubric](https://github.com/api-evangelist/kin-score).

The artifacts are published on [APIs.io](https://apis.io), not in this repository. This repository is the public record for Chado Studio: the place to say something is wrong, missing or out of date, and to ask for a re-score or a removal.

## Open an issue

- **Something about this listing** — a wrong description, a missing API, a stale artifact or a question about the rating: [open an issue on this repository](https://github.com/api-evangelist/llama-box/issues/new).
- **A new API, or one that is not in the catalog yet** — [submit it on APIs.io](https://apis.io/add/).
- **Anything else** — [the APIs.io inbox](https://github.com/api-search/inbox/issues/new) or [info@apievangelist.com](mailto:info@apievangelist.com).
