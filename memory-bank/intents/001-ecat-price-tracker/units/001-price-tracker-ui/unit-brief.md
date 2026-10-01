---
unit: 001-price-tracker-ui
intent: 001-ecat-price-tracker
phase: operational
status: complete
created: 2026-09-30T19:34:40.000Z
updated: 2026-09-30T19:53:00.000Z
---

# Unit Brief: 001-price-tracker-ui

## Purpose
Deliver real-time market transparency on the $ECAT landing page by fetching, computing, and visually presenting ECAT token metrics, USD/EGLD conversions, and interactive price trajectories.

## Scope

### In Scope
- Fetching live ECAT token details (`ECAT-4ebd0f`) and EGLD economics from MultiversX REST endpoints.
- Computing ECAT/EGLD pair ratio and calculating circulating market cap.
- Displaying real-time USD price, EGLD price, and 24h percentage change indicator.
- Interactive SVG price chart with timeframe switching (24H, 7D, 30D, ALL) and dynamic price tag updates.
- 30-second visibility-aware auto-polling with pulse indicator and manual refresh button.
- Comprehensive error and pre-market fallback handling.

### Out of Scope
- Direct on-chain wallet signing or in-page transaction broadcasting (links to Explorer/DEX instead).
- Server-side caching proxy (pure client-side execution).

---

## Assigned Requirements

| FR | Requirement | Priority |
|----|-------------|----------|
| FR-1 | MultiversX Token & EGLD Pair Price Fetching | Must |
| FR-2 | Dual Currency & Market Cap Display | Must |
| FR-3 | 24h Price Change & Trend Indicator | Must |
| FR-4 | Interactive Price History & Timeframe Chart | Must |
| FR-5 | Auto-Polling & Live Status Indicator | Should |

---

## Domain Concepts

### Key Entities
| Entity | Description | Attributes |
|--------|-------------|------------|
| TokenMetrics | Core token statistics from MultiversX | identifier, name, supply, decimals, price, transactions, accounts |
| Economics | Network-level economic data | egldPrice, marketCap |
| ChartPoint | Data point for SVG trajectory | timestamp, price, formattedDate |

### Key Operations
| Operation | Description | Inputs | Outputs |
|-----------|-------------|--------|---------|
| `fetchTokenMetrics()` | Queries token and economics APIs | identifier | Token & EGLD data object |
| `calculateMetrics()` | Computes EGLD ratio, market cap, % change | price, egldPrice, supply | Computed metrics |
| `renderPriceChart()` | Draws SVG bezier path and gradient area | pricePoints array | SVG paths & label updates |
| `startPolling()` | Sets up visibility-aware interval | intervalMs (30000) | Timer handle |

---

## Story Summary

| Metric | Count |
|--------|-------|
| Total Stories | 4 |
| Must Have | 3 |
| Should Have | 1 |
| Could Have | 0 |

### Stories

| Story ID | Title | Priority | Status |
|----------|-------|----------|--------|
| 001 | Fetch Token & EGLD Price Data | Must | Planned |
| 002 | Display Dual Currency Price & Market Cap | Must | Planned |
| 003 | Render Interactive Price History Chart | Must | Planned |
| 004 | Implement Polling & Live Status Indicator | Should | Planned |

---

## Technical Context
- **Stack**: Vanilla HTML5, CSS3, ES6+ JavaScript.
- **Endpoints**:
  - `https://api.multiversx.com/tokens/ECAT-4ebd0f`
  - `https://api.multiversx.com/economics`
- **Design Tokens**: Defined in `ux-guide.md` (Dark palette `#05070F`, Cyan `#23F7DD`, neon accents).

---

## Success Criteria
- [ ] Live price in USD and EGLD renders accurately.
- [ ] Market cap computes correctly from supply and price.
- [ ] Interactive chart toggles smoothly across all timeframes.
- [ ] Polling runs unobtrusively in background when tab is active.
- [ ] Landing page gracefully displays pre-market / offline state if API is unreachable.

---

## Bolt Suggestions

| Bolt | Type | Stories | Objective |
|------|------|---------|-----------|
| 001-price-tracker-ui | simple-construction-bolt | 001, 002, 003, 004 | Complete Price Tracker & Chart implementation |
