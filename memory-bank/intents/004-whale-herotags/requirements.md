---
intent: 004-whale-herotags
phase: inception
status: complete
created: 2026-10-01T08:20:00.000Z
updated: 2026-10-01T08:22:00.000Z
---

# Requirements: 004-whale-herotags

## Intent Overview
Enhance the $ECAT **Whale Leaderboard** (`#holders-activity`) by displaying MultiversX **herotags** (`@username`) instead of raw wallet addresses for top holders. When an account has a registered MultiversX herotag, display it in clean community social format (`@username`) with a distinctive herotag badge. When an account belongs to a known smart contract or liquidity pool, display its protocol asset name. For accounts without a registered herotag, gracefully fallback to the truncated address (`erd1...xxxx`).

## Business Goals
| Goal | Success Metric | Priority |
|------|----------------|----------|
| Identity & Social Recognition | High-visibility recognition for community whales via registered on-chain herotags | Must |
| Clarity & Legibility | Clean `@username` format replaces long cryptographic hash strings on the leaderboard | Must |
| Protocol Transparency | Smart contract / DEX liquidity pools identified by name (e.g. `xExchange: ECAT/WEGLD LP`) | Should |
| Trust & Usability | Copy button copies full `erd1...` wallet address with explorer link intact | Must |

---

## Functional Requirements

### FR-1: On-Chain Herotag & Asset Name Resolution
- **Description**: For each address returned in the Top 10 accounts feed (`/tokens/ECAT-4ebd0f/accounts`), resolve identity metadata:
  - If `assets.name` is present, capture the protocol/pool label.
  - Otherwise, query `https://api.multiversx.com/accounts/{address}` to fetch the `username` field.
  - Strip the trailing `.elrond` suffix and format as `@username` (e.g. `poshanarchist.elrond` → `@poshanarchist`, `adriancodarcea.elrond` → `@adriancodarcea`).
  - Cache resolved herotags in memory (`Map<string, string>`) to eliminate redundant HTTP requests across the 30-second polling intervals.
- **Priority**: Must

### FR-2: Leaderboard UI Presentation & Badges
- **Description**: Update the Holder row template in `#holdersTableBody`:
  - If herotag is present: Display `@username` in bold with a cyan `@` badge and hover tooltip showing full address.
  - If protocol name is present: Display protocol name with an `LP` / `Contract` indicator.
  - If neither is present: Display the formatted truncated address (`erd1...xxxx`).
  - The 1-click clipboard copy button continues to copy the full underlying `erd1...` address to the clipboard with toast feedback.
  - The link continues to open `https://explorer.multiversx.com/accounts/{address}` in a new tab.
- **Priority**: Must

### FR-3: Polling & Cache Synchronization
- **Description**: Integrate herotag lookup into the existing 30-second background polling cycle and manual refresh button without delaying the initial table render.
- **Priority**: Should

---

## Non-Functional Requirements

### NFR-1: Non-Blocking Concurrent Fetching
- **Target**: Query all top holder accounts in parallel with `Promise.all` and timeout boundaries (< 800ms).
- **Execution**: If a herotag lookup times out or fails, fallback instantly to truncated address without breaking the row render.

### NFR-2: Zero Dependencies
- **Target**: Pure Vanilla JS ES2022 and native browser `fetch`.

### NFR-3: Mobile Responsiveness
- **Target**: Herotags with long names truncate with ellipsis (`text-overflow: ellipsis`) on screens `< 640px` to prevent table horizontal blowout.
