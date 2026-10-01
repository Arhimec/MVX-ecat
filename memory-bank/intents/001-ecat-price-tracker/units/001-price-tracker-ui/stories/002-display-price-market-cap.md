---
id: 2
title: Display Dual Currency Price & Market Cap
unit: 001-price-tracker-ui
intent: 001-ecat-price-tracker
priority: Must
status: complete
created: 2026-09-30T19:34:50.000Z
implemented: true
---

# Story 002: Display Dual Currency Price & Market Cap

## User Story
**As a** crypto investor or ECAT holder
**I want** to see the ECAT price displayed in both USD and EGLD alongside the calculated market cap and 24h trend
**So that** I can gauge value in both fiat terms and native blockchain currency.

## Acceptance Criteria
- [ ] Renders formatted USD price (`$0.000123` or clean fallback `Pre-market`).
- [ ] Renders formatted EGLD price (`0.0000045 EGLD`).
- [ ] Dynamically calculates and formats circulating Market Cap (`supply * price`).
- [ ] Displays a 24h price trend badge with green/red styling (`+5.4%` / `-2.1%` / `0.0%`).
- [ ] Formats all numbers with tabular figures for visual stability during updates.
