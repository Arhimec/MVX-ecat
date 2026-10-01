---
story: 002-whale-leaderboard-card-ui
unit: 001-leaderboard-activity-ui
intent: 002-holder-leaderboard
status: complete
created: 2026-09-30T19:59:55.000Z
implemented: true
---

# Story: Render Whale Leaderboard & Tier Badges

## User Story
As a website visitor,
I want to view a formatted leaderboard showing ranks 1 to 10 with tier badges, visual supply bars, and 1-click address copy,
So that I can easily recognize major community stakeholders and verify their holdings on MultiversX Explorer.

## Acceptance Criteria
- [ ] Renders ranks 1 to 10 with tier badges:
  - Ranks 1–3: **Alpha Whale 🐋** (Cyan highlight)
  - Ranks 4–7: **Tiger Shark 🦈** (Indigo highlight)
  - Ranks 8–10: **Diamond Paws 🐾** (Purple highlight)
- [ ] Displays proportional fill bar indicating each holder's share of circulating supply.
- [ ] Formats address truncated (`erd1dj7q...wyx4p`) with a 1-click copy-to-clipboard button and toast feedback.
- [ ] Clicking the address or explorer icon opens `https://explorer.multiversx.com/accounts/{address}` in a new tab.
- [ ] Full responsive card collapse on mobile screens (< 640px).
