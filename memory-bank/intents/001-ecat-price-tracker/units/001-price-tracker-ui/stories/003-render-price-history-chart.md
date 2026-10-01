---
id: 3
title: Render Interactive Price History Chart
unit: 001-price-tracker-ui
intent: 001-ecat-price-tracker
priority: Must
status: complete
created: 2026-09-30T19:35:00.000Z
implemented: true
---

# Story 003: Render Interactive Price History Chart

## User Story
**As a** token observer
**I want** to switch across different timeframes (`24H`, `7D`, `30D`, `ALL`) on an SVG price trajectory chart
**So that** I can visualize the historical momentum and performance over time.

## Acceptance Criteria
- [ ] Timeframe buttons (`24H`, `7D`, `30D`, `ALL`) highlight actively upon selection.
- [ ] Smoothly updates the SVG line path (`#chartLinePath`) and area gradient fill (`#chartAreaPath`).
- [ ] Displays appropriate min/max scales and updates `#chartPriceTag` dynamically with current/selected price.
- [ ] Supports touch and mouse hover states without visual clipping on mobile screens.
