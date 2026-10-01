---
intent: 002-holder-leaderboard
phase: inception
status: units-decomposed
updated: 2026-09-30T19:59:40Z
---

# 002-holder-leaderboard - Unit Decomposition

## Units Overview

This intent decomposes into 1 frontend unit:

### Unit 1: 001-leaderboard-activity-ui

**Description**: The client-side holder leaderboard and real-time activity module integrated into `index.html`, providing MultiversX top account balance calculations, whale tier badges, interactive supply share bars, 1-click address copy, real-time token transfer stream, and synchronized tab toggling.

**Stories**:
- `001-top-holders-calculation`: As a visitor, I want to view the top 10 ECAT holders, their token balance, and percentage of circulating supply.
- `002-whale-leaderboard-card-ui`: As a visitor, I want to see tier badges, supply distribution bars, and 1-click address copy on the leaderboard.
- `003-recent-transfers-feed`: As a visitor, I want to see a live stream of recent token transfers with relative timestamps and explorer links.
- `004-tab-toggle-polling-sync`: As a visitor, I want to seamlessly switch between Top Holders and Activity tabs with auto-polling sync.

**Deliverables**:
- Augmented `index.html` with `#holders-activity` section, styles, and data controllers.

**Dependencies**:
- Depends on: None (connects with existing MultiversX API fetcher and polling loop)
- Depended by: None

**Estimated Complexity**: Medium (M)
**Default Bolt Type**: `simple-construction-bolt`

## Unit Dependency Graph
```text
[001-leaderboard-activity-ui] (Leaderboard & Activity Feed Integration)
```

## Execution Order
1. `001-leaderboard-activity-ui`
