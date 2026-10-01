---
stage: plan
bolt: 001-price-tracker-ui
created: 2026-09-30T19:37:45Z
---

## Implementation Plan: 001-price-tracker-ui

### Objective
Integrate real-time MultiversX token tracking, EGLD pair valuation, dynamic market cap calculation, interactive SVG price chart updates, and background auto-polling into `index.html`.

### Deliverables
- **API Client Engine (`fetchLiveECATProperties`)**:
  - Concurrently queries `https://api.multiversx.com/tokens/ECAT-4ebd0f` and `https://api.multiversx.com/economics`.
  - Calculates EGLD price ratio and circulating market cap.
  - Formats numbers cleanly with micro-precision.
- **Enhanced Token Metrics Grid (`#liveTokenGrid`)**:
  - Displays USD Price (`$0.000...`), EGLD Price (`0.000... EGLD`), Market Cap, 24h Price Change badge, Supply, Transfers, and Holders.
  - Interactive live connection indicator (`● LIVE`) with manual refresh action.
- **Dynamic Price Chart (`renderPriceChart`)**:
  - Timeframe switcher (`24H`, `7D`, `30D`, `ALL`) updating SVG bezier curve and gradient area.
  - Updates `#chartPriceTag` with formatted USD and EGLD values.
- **Visibility-Aware Polling**:
  - 30-second interval with automatic pause/resume on browser tab visibility changes.

### Dependencies
- **MultiversX REST APIs**:
  - `https://api.multiversx.com/tokens/ECAT-4ebd0f` (Token details)
  - `https://api.multiversx.com/economics` (EGLD network economics)

### Technical Approach
- Vanilla JavaScript (ES6+ async/await, modern DOM APIs).
- Maintain CSS custom properties and dark cosmic theme defined in `standards/ux-guide.md`.
- Fallback gracefully to "Pre-market / Launching" if token has zero trades or API is unreachable, avoiding broken states.

### Acceptance Criteria
- [ ] Stories 001, 002, 003, and 004 requirements met.
- [ ] MultiversX API and Economics endpoints queried concurrently.
- [ ] Price displayed in both USD and EGLD.
- [ ] Market Cap calculated dynamically (`supply * price`).
- [ ] 24h Change badge reflects market trend with appropriate colors.
- [ ] Timeframe switching updates chart curve and price label.
- [ ] Background polling auto-refreshes every 30s and pauses when hidden.
