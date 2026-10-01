---
stage: plan
bolt: 002-leaderboard-activity-ui
created: 2026-09-30T20:01:50.000Z
---

# Implementation Plan: 002-leaderboard-activity-ui

## Objective
Implement an on-chain **Holder Leaderboard & Real-Time Activity Feed** on the $ECAT landing page (`index.html`) using live MultiversX public REST APIs.

## Deliverables

### 1. HTML Markup (`index.html`)
- Dedicated section `#holders-activity` positioned directly beneath `#token-properties`.
- Section header with category tag `ON-CHAIN TRANSPARENCY`, title `Holder Leaderboard & Activity`, and live sync indicator.
- Cosmic view switcher tabs:
  - `#tabHoldersBtn`: "Top Holders (10)" with whale icon 🐋
  - `#tabActivityBtn`: "Live Activity" with pulse stream icon ⚡
- **Holders View Container (`#holdersView`)**:
  - Leaderboard table / card list with columns: Rank, Holder Address, Tier Badge, Balance (ECAT), and % of Supply (visual bar).
- **Activity Feed Container (`#activityView`)**:
  - Live transaction stream with relative timestamps, direction badge, sender & receiver, transferred quantity, and transaction hash link.
- Global copy toast notification element (`#copyToast`).

### 2. Styling (CSS)
- Glassmorphic card design matching cosmic dark theme (`#070B12`, cyan `#23F7DD`, indigo `#6366F1`, purple `#A855F7`).
- Tier badge color schemes:
  - Rank 1–3: `Alpha Whale` (Neon cyan badge with subtle glow)
  - Rank 4–7: `Tiger Shark` (Electric indigo badge)
  - Rank 8–10: `Diamond Paws` (Royal violet badge)
- Supply percentage progress bar with neon gradient fill.
- 1-click clipboard copy button with hover state and micro-interactions.
- Responsive mobile card collapse for screens `< 640px`.

### 3. JavaScript Logic
- `fetchTopHolders()`: Query `https://api.multiversx.com/tokens/ECAT-4ebd0f/accounts?size=10`.
  - Atomic unit balance parsing (18 decimal places) using BigInt division and standard localization.
  - Calculate percentage share against 1,000,000,000 ECAT total supply.
- `fetchRecentTransfers()`: Query `https://api.multiversx.com/tokens/ECAT-4ebd0f/transfers?size=10`.
  - Humanized relative time calculation ("Just now", "2m ago", "1h ago").
  - Address truncation utility (`erd1...xxxx`).
- `copyAddressToClipboard(address, btnEl)`: Native `navigator.clipboard.writeText` with visual tooltip/toast feedback.
- Tab toggle handler (`switchActivityTab(tabName)`).
- Synchronization with existing 30s background polling loop and `#manualRefreshBtn`.

## Dependencies
- MultiversX Accounts API: `https://api.multiversx.com/tokens/ECAT-4ebd0f/accounts?size=10`
- MultiversX Transfers API: `https://api.multiversx.com/tokens/ECAT-4ebd0f/transfers?size=10`
- MultiversX Explorer: `https://explorer.multiversx.com/`

## Acceptance Criteria
- [ ] Top 10 holders displayed with correct rank, tier, formatted ECAT balance, and supply bar.
- [ ] Addresses displayed truncated with working 1-click copy-to-clipboard functionality and explorer links.
- [ ] Recent transactions feed renders timestamp, addresses, transfer amount, and tx hash links.
- [ ] Tab switching toggles views seamlessly without page reload or visual jarring.
- [ ] Polling and refresh handlers update leaderboard and activity feed alongside the price tracker.
- [ ] Mobile responsive layout tested and verified.
