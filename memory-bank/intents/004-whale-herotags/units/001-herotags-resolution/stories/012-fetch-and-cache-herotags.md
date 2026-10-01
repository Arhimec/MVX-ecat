---
story: 012-fetch-and-cache-herotags
unit: 001-herotags-resolution
intent: 004-whale-herotags
status: complete
created: 2026-10-01T08:21:00.000Z
implemented: true
---

# Story: Fetch & Cache Top Holder Herotags

## User Story
As a community member,
I want the application to resolve on-chain MultiversX herotags and verified protocol asset names for the top 10 holders in parallel and cache them,
So that whale identities are instantly recognized without causing redundant network requests during polling.

## Acceptance Criteria
- [ ] Concurrently queries `https://api.multiversx.com/accounts/{address}` for all top accounts in the leaderboard feed.
- [ ] Strips `.elrond` suffix and formats valid usernames as `@username` (e.g., `poshanarchist.elrond` → `@poshanarchist`, `adriancodarcea.elrond` → `@adriancodarcea`).
- [ ] Extracts protocol labels for known liquidity pools and smart contracts from `account.assets.name`.
- [ ] Caches resolved identities in an in-memory `Map` across 30-second polling cycles.
- [ ] Employs safety timeouts and non-blocking fallbacks so that missing herotags or network timeouts never block the leaderboard render.
