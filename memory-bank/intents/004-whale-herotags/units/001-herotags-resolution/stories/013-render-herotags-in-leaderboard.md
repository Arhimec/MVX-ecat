---
story: 013-render-herotags-in-leaderboard
unit: 001-herotags-resolution
intent: 004-whale-herotags
status: complete
created: 2026-10-01T08:21:30.000Z
implemented: true
---

# Story: Render Herotags in Whale Leaderboard Table

## User Story
As a visitor viewing the Whale Leaderboard,
I want to see `@username` badges and protocol names displayed in place of raw wallet addresses,
So that the whale community distribution is visually engaging, immediately recognizable, and easy to read.

## Acceptance Criteria
- [ ] Displays `@username` with distinctive cyan herotag styling and an `@` icon/badge for accounts with resolved herotags.
- [ ] Displays verified protocol labels (e.g. `xExchange: ECAT/WEGLD LP`) with an `LP` badge for known liquidity pools.
- [ ] Gracefully falls back to the truncated wallet address (`erd1...xxxx`) for accounts without registered herotags.
- [ ] Maintains the 1-click clipboard copy button to copy the underlying full `erd1...` wallet address with toast feedback.
- [ ] Maintains clickable link to `https://explorer.multiversx.com/accounts/{address}` opening in a new tab.
- [ ] Includes CSS rules with ellipsis truncation on mobile viewports (`< 640px`) to prevent table layout distortion.
