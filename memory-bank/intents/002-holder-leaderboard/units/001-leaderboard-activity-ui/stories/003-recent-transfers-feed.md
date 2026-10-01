---
story: 003-recent-transfers-feed
unit: 001-leaderboard-activity-ui
intent: 002-holder-leaderboard
status: complete
created: 2026-09-30T20:00:00.000Z
implemented: true
---

# Story: Render Live Recent Transfers Feed

## User Story
As a website visitor,
I want to see the latest on-chain transfer transactions for $ECAT in real time,
So that I can observe genuine network activity and token velocity.

## Acceptance Criteria
- [ ] Queries `https://api.multiversx.com/tokens/ECAT-4ebd0f/transfers?size=10`.
- [ ] Formats transfer timestamp into relative human-readable format (e.g. "Just now", "5m ago", "2h ago").
- [ ] Displays Sender (`erd1...`) → Receiver (`erd1...`) with truncation and clipboard copy.
- [ ] Displays transferred ECAT token quantity formatted with commas.
- [ ] Provides direct explorer link for each transaction hash (`https://explorer.multiversx.com/transactions/{txHash}`).
- [ ] Graceful fallback state with informative empty/connecting notice.
