# Deployment History: 001-herotags-resolution

## Overview
- **Unit**: `001-herotags-resolution`
- **Intent**: `004-whale-herotags`
- **Current Version**: `v1.3.0`

---

## Log

### v1.3.0 (2026-10-01)
- **Target Environments**: Development, Staging, Production
- **Status**: ✅ Production Deployed & Verified
- **Key Changes**:
  - Implemented on-chain herotag (`@username`) resolution for the Whale Leaderboard table.
  - Implemented protocol asset label detection for known liquidity pools and smart contracts.
  - Added `cachedHerotags` `Map` to prevent redundant network queries during 30s background polling.
  - Maintained 1-click clipboard copy of underlying wallet address and explorer links.
- **Automated Validation**: 13/13 tests passed.
- **Verification Reports**:
  - Dev: [`verification-v1.3.0-dev.md`](file:///Users/vladimirvechiu/Antigravity/MVX-ecat/memory-bank/intents/004-whale-herotags/units/001-herotags-resolution/deployment/verification-v1.3.0-dev.md)
  - Staging: [`verification-v1.3.0-staging.md`](file:///Users/vladimirvechiu/Antigravity/MVX-ecat/memory-bank/intents/004-whale-herotags/units/001-herotags-resolution/deployment/verification-v1.3.0-staging.md)
  - Production: [`verification-v1.3.0-prod.md`](file:///Users/vladimirvechiu/Antigravity/MVX-ecat/memory-bank/intents/004-whale-herotags/units/001-herotags-resolution/deployment/verification-v1.3.0-prod.md)
- **Monitoring & Runbooks**: [`monitoring.md`](file:///Users/vladimirvechiu/Antigravity/MVX-ecat/memory-bank/intents/004-whale-herotags/units/001-herotags-resolution/deployment/monitoring.md)
