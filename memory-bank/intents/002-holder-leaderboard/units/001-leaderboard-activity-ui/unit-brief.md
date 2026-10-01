---
unit: 001-leaderboard-activity-ui
intent: 002-holder-leaderboard
phase: operational
status: complete
created: 2026-09-30T19:59:45.000Z
updated: 2026-09-30T20:13:00.000Z
---

# Unit Brief: 001-leaderboard-activity-ui

## Purpose
Empower the $ECAT landing page with verified on-chain transparency by surfacing the top 10 token holders, their share of total supply, tier classification, and real-time token transaction stream from the MultiversX network.

## Scope

### In Scope
- Querying MultiversX `/tokens/ECAT-4ebd0f/accounts?size=10` and computing 18-decimal balances and supply percentages.
- Displaying leaderboard ranks 1–10 with tier badges (Alpha Whale, Tiger Shark, Diamond Paws) and visual share progress bars.
- 1-click address copy with animated visual tooltip feedback ("Copied!") and external explorer links.
- Querying MultiversX `/tokens/ECAT-4ebd0f/transfers?size=10` and rendering a live stream of recent transactions.
- Cosmic glassmorphic tab switcher (Top Holders vs Live Activity) with responsive layout.
- Synchronization with the existing 30s background polling engine and manual refresh button.

### Out of Scope
- Internal wallet connection or signing of transactions (delegated to future wallet connect intent).
- Complex server-side database indexing (client queries public MultiversX REST API directly).

## Technical Approach
- Single-file zero-dependency design in `index.html`.
- Clean modular JS functions integrated into existing `ECATTracker` controller namespace.
- High-contrast accessible styling adhering to `memory-bank/standards/ux-guide.md`.
