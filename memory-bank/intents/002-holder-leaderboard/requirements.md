---
intent: 002-holder-leaderboard
phase: inception
status: complete
created: 2026-09-30T19:59:00.000Z
updated: 2026-09-30T20:00:55.000Z
---

# Requirements: 002-holder-leaderboard

## Intent Overview
Add an on-chain **Holder Leaderboard & Real-Time Activity Feed** to the $ECAT landing page. Directly querying the MultiversX public API, the module presents the Top 10 token holders (whale distribution, balance, share of circulating supply) and the latest token transfers with 1-click address copy, explorer links, and tabbed view switching.

## Business Goals
| Goal | Success Metric | Priority |
|------|----------------|----------|
| Token Distribution Transparency | Clear visibility of circulating supply distribution among top holders | Must |
| On-Chain Activity Proof | Real-time stream of genuine MultiversX transfer transactions | Must |
| Community Trust & Engagement | Whale tier badges, 1-click address copy, and direct explorer verification | Should |

---

## Functional Requirements

### FR-1: Top Token Accounts Fetching & Supply Normalization
- **Description**: Query `https://api.multiversx.com/tokens/ECAT-4ebd0f/accounts?size=10` and calculate normalized ECAT token quantities and supply percentage.
- **Acceptance Criteria**:
  - Handles 18 decimal places accurately without precision loss.
  - Computes each holder's exact percentage share against total circulating supply (1,000,000,000 ECAT).
  - Gracefully handles API latency or errors with fallback data.
- **Priority**: Must

### FR-2: Whale Leaderboard UI & Tier Badges
- **Description**: Render a responsive leaderboard table displaying Rank, Address, Balance, Supply Share, and Tier Badge.
- **Acceptance Criteria**:
  - Ranks 1 to 10 with tier classifications:
    - Ranks 1–3: **Alpha Whale 🐋** (Cyan badge)
    - Ranks 4–7: **Tiger Shark 🦈** (Indigo badge)
    - Ranks 8–10: **Diamond Paws 🐾** (Purple badge)
  - Visual supply share bar reflecting proportional token holdings.
  - Truncated address formatting (`erd1...xxxx`) with 1-click clipboard copy button and tooltip feedback ("Copied!").
  - Direct link to `https://explorer.multiversx.com/accounts/{address}`.
- **Priority**: Must

### FR-3: Recent On-Chain Activity Feed
- **Description**: Query `https://api.multiversx.com/tokens/ECAT-4ebd0f/transfers?size=10` to display recent token transfers.
- **Acceptance Criteria**:
  - Displays transaction timestamp formatted as human-readable relative time (e.g. "Just now", "4m ago").
  - Shows sender and receiver addresses with truncation and explorer links.
  - Formats transferred ECAT value with commas.
  - Links transaction hash directly to `https://explorer.multiversx.com/transactions/{txHash}`.
- **Priority**: Must

### FR-4: Tabbed Navigation & Real-Time Sync
- **Description**: Provide clean tab toggles between "Top Holders" and "Live Activity" within the `#holders-activity` section.
- **Acceptance Criteria**:
  - Tab state switches instantly with active underline / glow animation.
  - Synchronized with the existing 30s background polling lifecycle and `#manualRefreshBtn`.
  - Seamlessly integrates into existing dark cosmic `#070B12` theme and glassmorphic card patterns.
- **Priority**: Must

---

## Non-Functional Requirements

### NFR-1: Performance & Zero Overhead
- **Target**: Zero npm build dependencies; pure Vanilla JS and CSS.
- **Execution**: Initial render and tab switching execute in `< 16ms` (60fps).

### NFR-2: Mobile Responsiveness
- **Target**: Complete readability on screens from 320px to 4K.
- **Execution**: Table collapses into compact mobile card rows on screens `< 640px`.

### NFR-3: Network Resilience
- **Target**: Zero uncaught exceptions when MultiversX gateway throttles or drops connection.
- **Execution**: Graceful fallback to cached state with non-intrusive status pill update.
