---
id: 003-ecompass-chart-ui
unit: 001-ecompass-chart-ui
intent: 003-ecompass-chart
type: simple-construction-bolt
status: complete
stories:
  - 001-embed-ecompass-frame
  - 002-dual-chart-mode-toggle
  - 003-ecompass-action-links
created: 2026-09-30T20:21:05.000Z
started: 2026-09-30T20:23:10.000Z
completed: '2026-09-30T21:43:29Z'
current_stage: null
stages_completed:
  - name: plan
    completed: 2026-09-30T22:56:55.000Z
    artifact: implementation-plan.md
  - name: implement
    completed: 2026-09-30T23:18:40.000Z
    artifact: implementation-walkthrough.md
requires_bolts:
  - 001-price-tracker-ui
enables_bolts: []
requires_units: []
blocks: false
complexity:
  avg_complexity: 1
  avg_uncertainty: 1
  max_dependencies: 1
  testing_scope: 2
---

# Bolt: 003-ecompass-chart-ui

## Overview
Implementation bolt for integrating the eCompass live token charting terminal (`https://e-compass.io/tokens/ECAT-4ebd0f`) into the Price Tracker chart card in `index.html`.

## Objective
Enhance the chart card in `#token-properties` with:
1. Dual-mode switcher buttons: **eCompass DEX Chart 📊** and **Overview 📈**.
2. Seamlessly embedded eCompass iframe with dark-theme container, responsive height, and loading placeholder.
3. "Open in eCompass ↗" launch button for opening the full analytics portal.

## Stories Included
- **001**: Embed eCompass Live Token Chart Frame (Must)
- **002**: Dual Chart Mode Switcher (Must)
- **003**: External Action Controls to eCompass (Should)

## Bolt Type
**Type**: Simple Construction Bolt
**Definition**: `.specsmd/aidlc/templates/construction/bolt-types/simple-construction-bolt.md`

## Stages
- [ ] **1. Plan**: Pending → `implementation-plan.md`
- [ ] **2. Implement**: Pending → `implementation-walkthrough.md`
- [ ] **3. Test**: Pending → `test-walkthrough.md`

## Dependencies
### Requires
- `001-price-tracker-ui` (Base Price Tracker and Chart Card)
