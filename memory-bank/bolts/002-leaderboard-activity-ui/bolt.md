---
id: 002-leaderboard-activity-ui
unit: 001-leaderboard-activity-ui
intent: 002-holder-leaderboard
type: simple-construction-bolt
status: complete
stories:
  - 001-top-holders-calculation
  - 002-whale-leaderboard-card-ui
  - 003-recent-transfers-feed
  - 004-tab-toggle-polling-sync
created: 2026-09-30T20:00:30.000Z
started: 2026-09-30T20:01:40.000Z
completed: '2026-09-30T18:06:34Z'
current_stage: null
stages_completed:
  - name: plan
    completed: 2026-09-30T20:02:15.000Z
    artifact: implementation-plan.md
  - name: implement
    completed: 2026-09-30T20:05:45.000Z
    artifact: implementation-walkthrough.md
requires_bolts:
  - 001-price-tracker-ui
enables_bolts: []
requires_units: []
blocks: false
complexity:
  avg_complexity: 2
  avg_uncertainty: 1
  max_dependencies: 1
  testing_scope: 2
---

# Bolt: 002-leaderboard-activity-ui

## Overview
Implementation bolt for integrating the on-chain Holder Leaderboard and Real-Time Activity Feed into the $ECAT landing page.

## Objective
Add a dedicated `#holders-activity` section directly beneath the Price Tracker in `index.html` featuring:
1. Top 10 Token Holders with 18-decimal normalized balances, tier badges (Whale, Shark, Diamond Paws), and supply distribution bars.
2. 1-click address copy button with tooltip feedback and MultiversX Explorer links.
3. Live stream of recent token transfer transactions with relative timestamps and transaction hash explorer links.
4. Cosmic neon tab switcher and integration with the 30-second background polling cycle.

## Stories Included
- **001**: Fetch & Calculate Top Token Holders (Must)
- **002**: Render Whale Leaderboard & Tier Badges (Must)
- **003**: Render Live Recent Transfers Feed (Must)
- **004**: Tab Switching & Background Polling Sync (Should)

## Bolt Type
**Type**: Simple Construction Bolt
**Definition**: `.specsmd/aidlc/templates/construction/bolt-types/simple-construction-bolt.md`

## Stages
- [ ] **1. Plan**: Pending → `implementation-plan.md`
- [ ] **2. Implement**: Pending → `implementation-walkthrough.md`
- [ ] **3. Test**: Pending → `test-walkthrough.md`

## Dependencies
### Requires
- `001-price-tracker-ui` (Base price tracker and polling infrastructure)
