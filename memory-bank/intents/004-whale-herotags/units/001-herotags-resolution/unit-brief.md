---
unit: 001-herotags-resolution
intent: 004-whale-herotags
status: complete
created: 2026-10-01T08:20:30.000Z
---

# Unit Brief: 001-herotags-resolution

## Goal
Implement client-side on-chain herotag discovery and display for top token holders on the Whale Leaderboard table, showing `@username` badges or protocol asset names with graceful fallback to truncated addresses.

## Scope
- Parallel async resolution of `username` via `https://api.multiversx.com/accounts/{address}` for the top 10 accounts.
- Fast in-memory cache to prevent redundant API queries during 30s background polling.
- Clean community formatting (`@username` without `.elrond` suffix).
- Special handling for known liquidity pools and protocol contracts via `assets.name`.
- Fallback to formatted wallet address (`erd1...xxxx`) when no herotag exists.
- Preservation of 1-click clipboard copy (copies underlying `erd1...` address) and direct MultiversX Explorer account link.

## Target Deliverables
- `index.html`:
  - `cachedHerotags` cache map.
  - Enhanced account processing logic in `fetchHoldersAndActivity()`.
  - Updated HTML table row rendering template in `#holdersTableBody`.
  - CSS rules for `.herotag-badge`, `.protocol-badge`, and responsive truncation.
