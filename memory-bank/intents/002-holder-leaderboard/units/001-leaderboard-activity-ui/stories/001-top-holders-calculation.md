---
story: 001-top-holders-calculation
unit: 001-leaderboard-activity-ui
intent: 002-holder-leaderboard
status: complete
created: 2026-09-30T19:59:50.000Z
implemented: true
---

# Story: Fetch & Calculate Top Token Holders

## User Story
As a website visitor,
I want the page to fetch the top 10 accounts holding $ECAT from the MultiversX public API,
So that I can see the real balance and percentage share of circulating supply for each top holder.

## Acceptance Criteria
- [ ] Queries `https://api.multiversx.com/tokens/ECAT-4ebd0f/accounts?size=10`.
- [ ] Correctly converts atomic 18-decimal balances using `BigInt` division or exact math to avoid truncation errors.
- [ ] Computes exact percentage share of circulating supply (`balance / 1,000,000,000 * 100`).
- [ ] Provides fallback simulated holders if network request encounters rate limits or offline state.
