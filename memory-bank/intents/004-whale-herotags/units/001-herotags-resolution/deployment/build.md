---
version: "v1.3.0"
commit: "working-tree"
built: "2026-10-01T22:52:00Z"
status: "success"
unit: "001-herotags-resolution"
intent: "004-whale-herotags"
---

# Build: v1.3.0

## Artifact Details
- **Unit**: `001-herotags-resolution`
- **Release Type**: Minor Feature Release (`v1.3.0`)
- **Primary File**: `index.html`
- **Size**: 101,545 bytes (99 KB)
- **SHA-256**: `f1a9df6331d62fc3eda4990662ff9a040b88825d31df8e79ac6a772a71579aad`
- **Runtime Dependencies**: 0 npm packages (Pure client-side HTML5/CSS3/ES2022)

## Build Environment
- **OS**: macOS (Darwin 24.3.0)
- **Runtime**: Web Modern Standards (CSS Grid/Flexbox, ES6+ Modules, Async Fetch, Promise.allSettled)
- **Target Platform**: MultiversX Mainnet Community Web Portal

## Bundled Features & Capabilities
1. **On-Chain Herotags Resolution**:
   - Concurrently queries `https://api.multiversx.com/accounts/{address}` for top token holders.
   - Formats usernames as community `@username` (e.g. `@poshanarchist`, `@adriancodarcea`).
   - Identifies smart contracts and liquidity pools via `assets.name` (e.g. `xExchange: ECAT/WEGLD Liquidity Pool`).
   - Graceful fallback to truncated wallet address (`erd10wfe...yjwx`) when no herotag is registered.
2. **In-Memory Identity Cache**:
   - `cachedHerotags` `Map` preserves resolved account metadata across 30-second background polling cycles to avoid redundant network requests.
3. **Leaderboard UX & Interactivity**:
   - Renders `.herotag-link` and `.protocol-link` with distinctive neon styling, pill accents, and hover glow effects.
   - Preserves 1-click clipboard copy of underlying full `erd1...` wallet address with toast confirmation.
   - Retains direct external links to MultiversX Explorer accounts.

## Verification & Test Status
- Automated Test Suite: 13/13 checks passed ([`test-walkthrough.md`](file:///Users/vladimirvechiu/Antigravity/MVX-ecat/memory-bank/bolts/004-herotags-resolution/test-walkthrough.md)).
