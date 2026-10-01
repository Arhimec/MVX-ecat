# Units: 004-whale-herotags

## Overview
This intent consists of a single cohesive delivery unit:

```text
Intent: 004-whale-herotags
└── Unit: 001-herotags-resolution
```

---

## Unit Breakdown

### `001-herotags-resolution`
- **Name**: Whale Leaderboard Herotags Resolution & UI Presentation
- **Type**: Frontend Web UI & Client Data Integration
- **Description**: Extends `fetchHoldersAndActivity` in `index.html` to resolve on-chain MultiversX herotags (`@username`) via parallel account queries, maintains an in-memory identity cache, and renders formatted herotag badges or protocol asset names on the Top 10 Whale Leaderboard with fallback to truncated addresses.
- **Stories**:
  - `012`: Resolve and cache MultiversX herotags and asset names in parallel.
  - `013`: Render formatted herotag badges, protocol labels, clipboard copy, and responsive styles in `#holdersTableBody`.
- **Status**: Planned
