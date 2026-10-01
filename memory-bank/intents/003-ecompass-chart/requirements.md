---
intent: 003-ecompass-chart
phase: inception
status: complete
created: 2026-09-30T20:19:35.000Z
updated: 2026-09-30T20:21:20.000Z
---

# Requirements: 003-ecompass-chart

## Intent Overview
Integrate the live **eCompass MultiversX Token Chart** (`https://e-compass.io/tokens/ECAT-4ebd0f`) directly into the $ECAT landing page within the Price Tracker module. Provide an intuitive view toggle between the full live eCompass DEX candlestick chart and the lightweight SVG overview, paired with a direct deep link to the eCompass token portal.

## Business Goals
| Goal | Success Metric | Priority |
|------|----------------|----------|
| Professional DEX Charting | Token holders and traders can analyze live MultiversX candlestick data, volume bars, and order activity directly on-page | Must |
| MultiversX Ecosystem Integration | Deep link and iframe alignment with leading MultiversX analytics provider eCompass | Must |
| Seamless User Experience | Fast loading, responsive viewport scaling, and toggleable view modes | Should |

---

## Functional Requirements

### FR-1: eCompass Live Chart Embed
- **Description**: Embed the official eCompass chart for `$ECAT` (`ECAT-4ebd0f`) via an iframe pointing to `https://e-compass.io/tokens/ECAT-4ebd0f`.
- **Acceptance Criteria**:
  - Secure iframe sandbox attributes (`allow-scripts`, `allow-same-origin`, `allow-popups`).
  - Seamless dark theme styling with subtle glowing border matching the cosmic color scheme.
  - Loading skeleton with pulse indicator displayed while the iframe loads.
- **Priority**: Must

### FR-2: Dual Chart Mode Switcher
- **Description**: Provide a toggle control allowing visitors to switch between:
  1. **eCompass Live DEX Chart 📊** (Live candlesticks and liquidity pool depth from eCompass)
  2. **Simplified Overview 📈** (Lightweight responsive SVG trajectory chart)
- **Acceptance Criteria**:
  - Active toggle button styled with cosmic cyan pill highlight.
  - Smooth display toggle without DOM recreation or layout jumping.
- **Priority**: Must

### FR-3: External Action Controls
- **Description**: Add a prominent external link button: "Open in eCompass ↗" leading to `https://e-compass.io/tokens/ECAT-4ebd0f`.
- **Acceptance Criteria**:
  - Opens in a new tab with `rel="noopener noreferrer"`.
  - Positioned neatly alongside the chart header and timeframe controls.
- **Priority**: Must

### FR-4: Mobile & Responsive Scaling
- **Description**: Responsive container height scaling for optimal viewing on desktop and mobile screens.
- **Acceptance Criteria**:
  - Desktop height: `540px`.
  - Tablet/Mobile height: `420px`.
  - Iframe width: `100%` of container width with smooth borders and rounded corners.
- **Priority**: Must

---

## Non-Functional Requirements

### NFR-1: Performance & Resource Efficiency
- **Target**: Lazy iframe initialization to prevent unnecessary data usage on initial page load.
- **Execution**: Iframe loads on first view activation or scroll into viewport (`loading="lazy"`).

### NFR-2: Frame Security & Isolation
- **Target**: Strict isolation preventing iframe scripts from altering the host landing page.
- **Execution**: Standard `sandbox` flags and explicit HTTPS enforcement.

### NFR-3: Theme Harmonization
- **Target**: Container background blends smoothly with the landing page cosmic `#070B12` and `#0e1524` surfaces.
