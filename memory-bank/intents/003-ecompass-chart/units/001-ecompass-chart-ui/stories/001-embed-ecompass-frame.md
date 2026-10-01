---
story: 001-embed-ecompass-frame
unit: 001-ecompass-chart-ui
intent: 003-ecompass-chart
status: complete
created: 2026-09-30T20:20:35.000Z
implemented: true
---

# Story: Embed eCompass Live Token Chart Frame

## User Story
As a token trader,
I want to see the live eCompass DEX candlestick chart for $ECAT directly on the page,
So that I can analyze price candles, market volume, and trading trends without leaving the site.

## Acceptance Criteria
- [ ] Embeds iframe pointing to `https://e-compass.io/tokens/ECAT-4ebd0f`.
- [ ] Implements secure iframe sandbox attributes (`allow-scripts allow-same-origin allow-popups allow-forms`).
- [ ] Styles container with rounded corners, dark cosmic border, and responsive height (540px desktop / 420px mobile).
- [ ] Shows a loading placeholder skeleton while the iframe establishes connection.
