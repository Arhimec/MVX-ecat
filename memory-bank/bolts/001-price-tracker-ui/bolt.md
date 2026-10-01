---
id: 001-price-tracker-ui
unit: 001-price-tracker-ui
intent: 001-ecat-price-tracker
type: simple-construction-bolt
status: complete
stories:
  - '001'
  - '002'
  - '003'
  - '004'
created: 2026-09-30T19:35:20.000Z
started: 2026-09-30T19:37:30.000Z
completed: '2026-09-30T17:46:28Z'
current_stage: null
stages_completed:
  - name: plan
    completed: 2026-09-30T19:38:20.000Z
    artifact: implementation-plan.md
  - name: implement
    completed: 2026-09-30T19:44:20.000Z
    artifact: implementation-walkthrough.md
requires_bolts: []
enables_bolts: []
requires_units: []
blocks: false
complexity:
  avg_complexity: 1
  avg_uncertainty: 1
  max_dependencies: 1
  testing_scope: 2
---

# Bolt: 001-price-tracker-ui

## Overview
Implementation bolt for adding the real-time MultiversX token price tracker and interactive chart to the $ECAT landing page.

## Objective
Enhance the existing `index.html` with live MultiversX API integration (ECAT token data and EGLD economics), USD & EGLD price display, market cap calculations, interactive SVG historical chart, and visibility-aware background polling.

## Stories Included
- **001**: Fetch Token & EGLD Price Data (Must)
- **002**: Display Dual Currency Price & Market Cap (Must)
- **003**: Render Interactive Price History Chart (Must)
- **004**: Implement Polling & Live Status Indicator (Should)

## Bolt Type
**Type**: Simple Construction Bolt
**Definition**: `.specsmd/aidlc/templates/construction/bolt-types/simple-construction-bolt.md`

## Stages
- [ ] **1. Plan**: Pending → `implementation-plan.md`
- [ ] **2. Implement**: Pending → `implementation-walkthrough.md`
- [ ] **3. Test**: Pending → `test-walkthrough.md`

## Dependencies
### Requires
- None (First bolt)

### Enables
- Operations deployment

## Success Criteria
- [ ] MultiversX token API and EGLD economics queried concurrently.
- [ ] Live USD price, EGLD price, and circulating market cap displayed clearly.
- [ ] 24h gain/loss indicator reflects market movement with color coding.
- [ ] SVG price chart dynamically renders trajectories across all timeframes.
- [ ] 30s auto-polling with live indicator and fallback for offline/pre-market.
