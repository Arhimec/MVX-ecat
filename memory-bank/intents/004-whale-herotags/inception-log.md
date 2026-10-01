---
intent: 004-whale-herotags
status: inception-complete
created: 2026-10-01T08:20:00.000Z
completed: 2026-10-01T08:22:15.000Z
---

# Inception Log: 004-whale-herotags

## Summary
- **Intent**: `004-whale-herotags`
- **Units Planned**: 1 (`001-herotags-resolution`)
- **Stories Created**: 2 (`012`, `013`)
- **Bolts Planned**: 1 (`004-herotags-resolution`)
- **Status**: Inception Complete

## Decisions Made
1. **Herotag Format**: Formatted as `@username` (stripping `.elrond` suffix) for clean social visibility (e.g. `@poshanarchist`, `@adriancodarcea`).
2. **Protocol Contracts**: Use `assets.name` to identify and display known protocols/liquidity pools (e.g. `xExchange: ECAT/WEGLD LP`).
3. **Graceful Fallback**: Accounts without registered herotags fallback to truncated addresses (`erd10wfe...yjwx`).
4. **Clipboard Copy**: Copy button continues to copy the full underlying `erd1...` wallet address with animated toast feedback.
5. **Caching**: In-memory `Map` caches resolved identities to prevent redundant network calls during the 30-second background polling cycle.

## Next Phase
Transition to Construction Phase (`/specsmd-construction-agent --bolt="004-herotags-resolution"`).
