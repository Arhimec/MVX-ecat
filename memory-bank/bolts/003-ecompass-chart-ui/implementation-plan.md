---
stage: plan
bolt: 003-ecompass-chart-ui
created: 2026-09-30T20:23:15.000Z
---

# Implementation Plan: 003-ecompass-chart-ui

## Objective
Embed the **eCompass Live Token Chart** (`https://e-compass.io/tokens/ECAT-4ebd0f`) into the Price Tracker card in `index.html`, paired with a dual-mode switcher and external portal deep-links.

## Deliverables

### 1. HTML Markup (`index.html`)
- **Chart Card Header Enhancement**:
  - Add chart mode switcher toolbar (`.chart-mode-toolbar`):
    - `#btnModeEcompass`: "eCompass DEX Chart 📊" (Active by default)
    - `#btnModeOverview`: "Overview Curve 📈"
    - `#btnOpenEcompass`: "Open in eCompass ↗" (External link to `https://e-compass.io/tokens/ECAT-4ebd0f`)
- **Dual Container Layout**:
  - `#ecompassChartContainer`: Secure iframe container with loading skeleton (`#ecompassSkeleton`) and embedded iframe (`#ecompassIframe`).
  - `#overviewChartContainer`: Existing SVG price trajectory, hover crosshair, and timeframe controls (`24H`, `7D`, `30D`, `ALL`).

### 2. Styling (CSS)
- Glassmorphic frame for `#ecompassChartContainer` with cosmic dark background (`#070B12`) and neon cyan accent glow.
- Responsive height: `540px` on desktop, `420px` on tablet and mobile.
- Clean toolbar styling for mode buttons with active pill states and hover transitions.
- Loading skeleton with subtle pulse glow while iframe initializes.

### 3. JavaScript Logic
- Mode switching handler:
  - Toggles `.active` classes on buttons and switches visibility between `#ecompassChartContainer` and `#overviewChartContainer`.
  - Lazy iframe initialization to minimize initial bandwidth usage.
  - Iframe `onload` event listener to fade out `#ecompassSkeleton`.

## Dependencies
- eCompass MultiversX Token Portal: `https://e-compass.io/tokens/ECAT-4ebd0f`
- Existing `#token-properties` chart card in `index.html`

## Acceptance Criteria
- [ ] eCompass iframe embedded with valid sandbox flags and responsive dimensions.
- [ ] Mode switcher seamlessly toggles between eCompass DEX Chart and Overview curve.
- [ ] Loading skeleton displays during iframe load and hides cleanly when ready.
- [ ] External launch button opens `https://e-compass.io/tokens/ECAT-4ebd0f` in a new tab with `rel="noopener noreferrer"`.
- [ ] Mobile responsive layout tested and verified without horizontal scroll.
