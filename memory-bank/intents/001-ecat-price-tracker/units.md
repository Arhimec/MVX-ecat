---
intent: 001-ecat-price-tracker
phase: inception
status: units-decomposed
updated: 2026-09-30T19:34:40Z
---

# 001-ecat-price-tracker - Unit Decomposition

## Units Overview

This intent decomposes into 1 cohesive frontend unit:

### Unit 1: 001-price-tracker-ui

**Description**: The client-side price tracking and chart module integrated into the existing `index.html` landing page, providing live MultiversX API data fetching, dual currency conversion (USD/EGLD), market cap, interactive SVG chart visualization, and resilient background polling.

**Stories**:
- `001-fetch-token-egld-price`: As a user, I want the page to fetch current ECAT token and EGLD prices from MultiversX APIs.
- `002-display-price-market-cap`: As a user, I want to see ECAT price in both USD and EGLD along with market cap and 24h trend.
- `003-render-price-history-chart`: As a user, I want to explore interactive price charts across multiple timeframes (24H, 7D, 30D, ALL).
- `004-polling-and-status-indicator`: As a user, I want the prices to auto-update smoothly with a live status indicator and manual refresh.

**Deliverables**:
- Enhanced `index.html` markup, styling, and JavaScript logic with complete MultiversX API integration.

**Dependencies**:
- Depends on: None (Self-contained frontend component)
- Depended by: None

**Estimated Complexity**: Medium (M)
**Default Bolt Type**: `simple-construction-bolt`

## Unit Dependency Graph

```text
[001-price-tracker-ui] (Complete Tracker & Chart Integration)
```

## Execution Order
1. Bolt `001-price-tracker-ui`: Implement data layer, UI metric displays, interactive chart, and polling engine.
