---
unit: 001-ecompass-chart-ui
intent: 003-ecompass-chart
phase: inception
status: complete
created: 2026-09-30T20:20:25.000Z
updated: 2026-09-30T20:20:25.000Z
---

# Unit Brief: 001-ecompass-chart-ui

## Purpose
Incorporate real-time MultiversX DEX candlestick and trading depth charts from eCompass (`e-compass.io`) into the $ECAT landing page, giving token holders and decentralized traders a comprehensive trading terminal view alongside the simplified trajectory overview.

## Scope

### In Scope
- Embedding `https://e-compass.io/tokens/ECAT-4ebd0f` within a secure, responsive iframe container.
- Implementing a dual-mode chart controller: **eCompass DEX Chart 📊** vs **Simplified Overview 📈**.
- Adding a high-visibility external button: "Open in eCompass ↗" leading to the live token portal.
- Styling the chart studio with cosmic glassmorphism, responsive height (540px desktop / 420px mobile), and a loading skeleton with pulse effect.

### Out of Scope
- Reverse engineering or hosting a custom WebSocket candlestick back-end (relies on eCompass's established charting platform).

## Technical Approach
- Vanilla HTML5/CSS3/ES2022 within `index.html`.
- Standard iframe sandbox flags (`allow-scripts allow-same-origin allow-popups`).
- Seamless coexistence with the existing SVG chart and timeframes.
