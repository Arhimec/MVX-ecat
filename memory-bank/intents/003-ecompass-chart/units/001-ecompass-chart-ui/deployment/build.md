---
version: "v1.2.0"
commit: "working-tree"
built: "2026-09-30T23:44:30Z"
status: "success"
unit: "001-ecompass-chart-ui"
intent: "003-ecompass-chart"
---

# Build: v1.2.0

## Artifact Details
- **Unit**: `001-ecompass-chart-ui`
- **Release Type**: Minor Feature Release (`v1.2.0`)
- **Primary File**: `index.html`
- **Size**: 95,260 bytes (93 KB)
- **SHA-256**: `825fa818edb920ce74b654429d8492ca39db07bcd8bfb0f1ccdda8bda5ef5ef0`
- **Runtime Dependencies**: 0 npm packages (Pure client-side HTML5/CSS3/ES2022)

## Build Environment
- **OS**: macOS (Darwin 24.3.0)
- **Runtime**: Web Modern Standards (CSS Grid/Flexbox, ES6+ Modules, SVG, iFrame Sandboxing)
- **Target Platform**: MultiversX Mainnet Community Web Portal

## Bundled Features & Capabilities
1. **Interactive eCompass DEX Chart Embed**:
   - Live URL: `https://e-compass.io/token/ECAT-4ebd0f`.
   - Native eCompass candlestick/depth charts with real-time MultiversX DEX pairs, order books, and indicators.
   - Sandboxed iframe with security attributes (`sandbox="allow-scripts allow-same-origin allow-popups allow-forms allow-presentation"`).
2. **Dual-Mode Chart Switcher**:
   - Accessible ARIA toggle buttons with instant mode switching:
     - `eCompass DEX Chart 📊` (Default active view)
     - `Overview Curve 📈` (Cosmic SVG curve with timeframe selector)
3. **Skeleton Loading Screen & Direct Action Controls**:
   - Cosmic skeleton loader with spinning indicator and CSS shimmer gradient, smoothly fading out once the iframe completes loading.
   - Quick launch external action button (`Open in eCompass ↗`) with secure `target="_blank"` and `rel="noopener noreferrer"`.
4. **Responsive Layout**:
   - 540px view height on desktop, automatically adjusting to 420px on mobile screens (< 768px).

## Verification & Test Status
- Automated Test Suite: 21/21 tests passed ([`test-walkthrough.md`](file:///Users/vladimirvechiu/Antigravity/MVX-ecat/memory-bank/bolts/003-ecompass-chart-ui/test-walkthrough.md)).
