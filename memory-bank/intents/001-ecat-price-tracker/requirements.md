---
intent: 001-ecat-price-tracker
phase: inception
status: complete
created: 2026-09-30T19:33:10.000Z
updated: 2026-09-30T19:36:10.000Z
---

# Requirements: 001-ecat-price-tracker

## Intent Overview
Add a live MultiversX token price tracking module to the existing $ECAT (`ECAT-4ebd0f`) landing page. The tracker monitors $ECAT paired with EGLD, displays real-time price in both USD and EGLD, calculates market cap, visualizes price trends via an interactive SVG chart, and auto-polls the network with graceful fallback states.

## Business Goals
| Goal | Success Metric | Priority |
|------|----------------|----------|
| Live Market Visibility | Real-time price and EGLD pair ratio available directly on landing page | Must |
| Accurate Token Metrics | Dynamic calculation of market cap and 24h price fluctuation | Must |
| High Community Trust | Transparent on-chain status, live polling feedback, and DEX swap access | Should |

---

## Functional Requirements

### FR-1: MultiversX Token & EGLD Pair Price Fetching
- **Description**: The system must query MultiversX API endpoints (`https://api.multiversx.com/tokens/ECAT-4ebd0f` and economics `/economics` or DEX pair endpoints) to obtain token metadata, current token price in USD, and current EGLD conversion rate.
- **Acceptance Criteria**:
  - Successfully parses token `price`, `supply`, `decimals`, `accounts`, and `transactions`.
  - Obtains live EGLD price in USD to calculate or display the ECAT/EGLD price ratio.
  - If token price is not yet indexed on public API, gracefully calculates from pair or displays "Pre-market / Launching" without UI errors.
- **Priority**: Must

### FR-2: Dual Currency & Market Cap Display
- **Description**: The UI must display the token price in both USD (`$X.XXXXXX`) and EGLD (`X.XXXXXXXX EGLD`), alongside calculated Market Capitalization based on supply.
- **Acceptance Criteria**:
  - Prices format with appropriate decimal precision (e.g. 6 to 8 decimals for micro-prices).
  - Market capitalization is dynamically calculated (`supply * price`) and formatted with commas.
  - Elements update seamlessly when new price data is received.
- **Priority**: Must

### FR-3: 24h Price Change & Trend Indicator
- **Description**: Display a visual badge showing 24h percentage change with color coding.
- **Acceptance Criteria**:
  - Positive gain displays in neon green (`#00E676`) with a `+` prefix.
  - Negative loss displays in coral red (`#FF5252`) with a `-` prefix.
  - Flat / pre-market state displays neutral indicator (`#9AB5C7`).
- **Priority**: Must

### FR-4: Interactive Price History & Timeframe Chart
- **Description**: Render an interactive SVG price chart with timeframe selector buttons (`24H`, `7D`, `30D`, `ALL`).
- **Acceptance Criteria**:
  - Selecting a timeframe recalculates the SVG bezier curve path and gradient fill smoothly.
  - Hovering/clicking points or timeframe updates the `#chartPriceTag` to reflect the respective point price.
  - Chart scales dynamically to container width with smooth SVG transitions.
- **Priority**: Must

### FR-5: Auto-Polling & Live Status Indicator
- **Description**: Periodically poll the MultiversX network for updated price data with a visual live heartbeat indicator.
- **Acceptance Criteria**:
  - Auto-polls every 30 seconds when tab is active without blocking the main browser thread.
  - Pauses or reduces polling rate when document is hidden (Page Visibility API) to conserve user bandwidth.
  - Includes a live pulse badge (`LIVE`) showing connection health and a manual refresh trigger.
  - Gracefully handles network timeouts and HTTP 429/500 errors with friendly retry state.
- **Priority**: Should

---

## Non-Functional Requirements

### Performance
| Requirement | Metric | Target |
|-------------|--------|--------|
| Initial Load Time | Network request completion | < 500ms |
| DOM Impact | Layout reflow / jank | 60 FPS transitions, zero cumulative layout shift (CLS) |
| Bundle Overhead | Additional script/CSS size | < 15KB uncompressed vanilla code |

### Reliability
| Requirement | Metric | Target |
|-------------|--------|--------|
| Error Resilience | Graceful degradation | 100% (Never breaks page if API is down) |
| Offline / Pre-market handling | Fallback UI display | Shows pre-market badge with explorer/swap link |

### Security & Privacy
| Requirement | Standard | Notes |
|-------------|----------|-------|
| API Communication | HTTPS Only | Public read-only MultiversX REST endpoints |
| Credentials | Zero secrets | No API keys or private keys required |

---

## Constraints

### Technical Constraints
- **Zero Build Step**: Must work directly within the existing `index.html` (or modular `style.css` / `app.js` if split) without requiring Node.js build processes.
- **Standards Conformance**: Must strictly honor `standards/tech-stack.md`, `standards/coding-standards.md`, and `standards/ux-guide.md` (dark palette `#05070F`, MultiversX cyan `#23F7DD`, glassmorphism, responsive grids).

---

## Assumptions
| Assumption | Risk if Invalid | Mitigation |
|------------|-----------------|------------|
| MultiversX public API CORS allows direct browser fetch | Browser blocks fetch requests | Use standard official CORS-enabled `https://api.multiversx.com` endpoints |
| Token is paired with EGLD on MultiversX DEX | Direct pair lookup might need fallback | Support both direct token price endpoint and calculated EGLD ratio fallback |
