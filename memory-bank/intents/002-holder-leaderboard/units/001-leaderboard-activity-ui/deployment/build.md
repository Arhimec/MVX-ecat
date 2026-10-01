---
version: "v1.1.0"
commit: "working-tree"
built: "2026-09-30T20:07:35Z"
status: "success"
unit: "001-leaderboard-activity-ui"
intent: "002-holder-leaderboard"
---

# Build: v1.1.0

## Artifact Details
- **Unit**: `001-leaderboard-activity-ui`
- **Release Type**: Minor Feature Release (`v1.1.0`)
- **Primary File**: `index.html`
- **Size**: 87,092 bytes (85 KB)
- **SHA-256**: `33c83f19e4c30788cb854428a6d20ad58aca22f8409e408e3c830031a3fc09c7`
- **Runtime Dependencies**: 0 npm packages (Pure client-side HTML5/CSS3/ES2022)

## Build Environment
- **OS**: macOS (Darwin 24.3.0)
- **Runtime**: Web Modern Standards (CSS Grid/Flexbox, ES6+ Modules, SVG)
- **Target Platform**: MultiversX Mainnet Community Web Portal

## Bundled Features & Capabilities
1. **On-Chain Whale Leaderboard**:
   - Live query: `https://api.multiversx.com/tokens/ECAT-4ebd0f/accounts?size=10`.
   - Exact 18-decimal token balance parsing and dynamic supply percentage calculations against 1,000,000,000 circulating supply.
   - Community tier classification: **Alpha Whale 🐋**, **Tiger Shark 🦈**, **Diamond Paws 🐾**.
   - Truncated wallet addresses with 1-click clipboard copy, animated toast feedback, and MultiversX Explorer account links.
2. **Real-Time On-Chain Activity Stream**:
   - Live query: `https://api.multiversx.com/tokens/ECAT-4ebd0f/transfers?size=10`.
   - Relative timestamps, sender & receiver wallets, transferred ECAT volume, and transaction hash links.
3. **Cosmic Tab Switching**:
   - Zero-layout-jump switching between "Top Holders (10)" and "Live Activity".
4. **Resilient Auto-Polling**:
   - Synchronized with the 30-second Page Visibility polling lifecycle and manual refresh button.

## Verification & Test Status
- Automated Test Suite: 25/25 tests passed ([`test-walkthrough.md`](file:///Users/vladimirvechiu/Antigravity/MVX-ecat/memory-bank/bolts/002-leaderboard-activity-ui/test-walkthrough.md)).
