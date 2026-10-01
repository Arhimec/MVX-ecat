---
id: 004-herotags-resolution
unit: 001-herotags-resolution
intent: 004-whale-herotags
type: simple-construction-bolt
status: complete
stories:
  - 012-fetch-and-cache-herotags
  - 013-render-herotags-in-leaderboard
created: 2026-10-01T08:21:45.000Z
started: 2026-10-01T08:24:30.000Z
current_stage: null
stages_completed:
  - name: plan
    completed: 2026-10-01T08:24:45.000Z
    artifact: implementation-plan.md
  - name: implement
    completed: 2026-10-01T08:28:30.000Z
    artifact: implementation-walkthrough.md
requires_bolts:
  - 002-leaderboard-activity-ui
enables_bolts: []
requires_units:
  - 001-leaderboard-activity-ui
blocks: false
complexity:
  avg_complexity: 1
  avg_uncertainty: 1
  max_dependencies: 1
  testing_scope: 2
completed: '2026-10-01T20:49:20Z'
---

# Bolt: 004-herotags-resolution

## Overview
Implementation bolt for resolving on-chain MultiversX herotags (`@username`) and verified protocol asset names for top token holders and rendering them with badges, clipboard copy, and responsive fallbacks in the Whale Leaderboard (`#holders-activity`).

## Objective
1. Concurrently resolve `username` from `https://api.multiversx.com/accounts/{address}` for each top holder and cache in memory.
2. Format herotags as `@username` (stripping `.elrond`).
3. Display protocol names for known liquidity pools and contracts.
4. Render herotags with distinct styling and badges while falling back to truncated addresses for un-tagged accounts.
5. Preserve 1-click clipboard copy (copying full `erd1...` address) and explorer links.

## Stories Included
- **012**: Fetch & Cache Top Holder Herotags (Must)
- **013**: Render Herotags in Whale Leaderboard Table (Must)

## Bolt Type
**Type**: Simple Construction Bolt
**Definition**: `.specsmd/aidlc/templates/construction/bolt-types/simple-construction-bolt.md`

## Stages
- [ ] **1. Plan**: Pending → `implementation-plan.md`
- [ ] **2. Implement**: Pending → `implementation-walkthrough.md`
- [ ] **3. Test**: Pending → `test-walkthrough.md`

## Dependencies
### Requires
- `002-leaderboard-activity-ui` (Base Leaderboard & Activity UI)
