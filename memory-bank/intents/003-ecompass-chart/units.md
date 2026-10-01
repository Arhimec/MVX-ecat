---
intent: 003-ecompass-chart
phase: inception
status: units-decomposed
updated: 2026-09-30T20:20:15Z
---

# 003-ecompass-chart - Unit Decomposition

## Units Overview

This intent decomposes into 1 frontend unit:

### Unit 1: 001-ecompass-chart-ui

**Description**: The client-side eCompass chart embedding and mode switching interface integrated into `index.html`. It provides a seamless toggle between the live eCompass DEX trading chart (`https://e-compass.io/tokens/ECAT-4ebd0f`) and the simplified SVG price curve, accompanied by a direct "Open in eCompass ↗" launch button and responsive dark container styling.

**Stories**:
- `001-embed-ecompass-frame`: As a trader, I want to view the live eCompass DEX candlestick chart embedded within the price tracker card.
- `002-dual-chart-mode-toggle`: As a visitor, I want to easily toggle between the eCompass live chart and the simplified overview curve.
- `003-ecompass-action-links`: As a visitor, I want a direct action button to open the full eCompass token portal in a new tab.

**Deliverables**:
- Augmented `index.html` markup, CSS styling, and controller script in the price chart studio card.

**Dependencies**:
- Depends on: `001-price-tracker-ui` (enhances existing price chart card in `#token-properties`)
- Depended by: None

**Estimated Complexity**: Low to Medium (S/M)
**Default Bolt Type**: `simple-construction-bolt`

## Unit Dependency Graph
```text
[001-ecompass-chart-ui] (eCompass Chart Studio & Mode Switcher)
```

## Execution Order
1. `001-ecompass-chart-ui`
