---
id: 4
title: Implement Polling & Live Status Indicator
unit: 001-price-tracker-ui
intent: 001-ecat-price-tracker
priority: Should
status: complete
created: 2026-09-30T19:35:10.000Z
implemented: true
---

# Story 004: Implement Polling & Live Status Indicator

## User Story
**As a** page visitor keeping the landing page open
**I want** prices to auto-refresh in the background with a visual live pulse indicator and manual refresh option
**So that** I stay informed of real-time market changes without having to manually reload the entire browser page.

## Acceptance Criteria
- [ ] Auto-polls MultiversX endpoints every 30 seconds when the browser tab is visible.
- [ ] Uses Page Visibility API to pause polling when the tab is hidden and resume immediately upon tab focus.
- [ ] Provides a subtle glowing `LIVE` pulse indicator in the header/price card.
- [ ] Adds a manual refresh button with spinning state on click.
- [ ] Shows clear offline/error feedback if connection fails, auto-retrying on the next cycle.
