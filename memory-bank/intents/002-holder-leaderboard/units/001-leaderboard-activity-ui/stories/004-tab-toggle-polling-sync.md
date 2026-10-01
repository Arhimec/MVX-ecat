---
story: 004-tab-toggle-polling-sync
unit: 001-leaderboard-activity-ui
intent: 002-holder-leaderboard
status: complete
created: 2026-09-30T20:00:05.000Z
implemented: true
---

# Story: Tab Switching & Background Polling Sync

## User Story
As a website visitor,
I want to toggle between "Top Holders (10)" and "Live Activity" tabs seamlessly and have data auto-refresh with the network,
So that I can switch perspectives without page reloads and stay up-to-date with on-chain events.

## Acceptance Criteria
- [ ] Toggle buttons with active neon highlight for "Top Holders (10)" and "Live Activity".
- [ ] Switching tabs toggles view visibility without layout shift.
- [ ] Integrated into the 30-second visibility-aware polling loop.
- [ ] Clicking the `#manualRefreshBtn` refreshes price, top holders, and transfers simultaneously.
- [ ] Adheres strictly to the dark cosmic aesthetic defined in `memory-bank/standards/ux-guide.md`.
