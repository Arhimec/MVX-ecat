---
stage: plan
bolt: 004-herotags-resolution
unit: 001-herotags-resolution
intent: 004-whale-herotags
created: 2026-10-01T08:24:45.000Z
---

# Implementation Plan: 004-herotags-resolution

## Objective
Enhance the Whale Leaderboard table (`#holdersTableBody` in `index.html`) to resolve and display MultiversX on-chain herotags (`@username`) and verified protocol asset names for top holders with graceful fallback to truncated addresses.

---

## Deliverables

### 1. Data Layer & Resolution (`index.html`)
- **Herotag Cache (`cachedHerotags`)**:
  - Implement an in-memory `Map` keyed by wallet address to cache resolved usernames/labels across polling intervals.
- **Concurrent Identity Fetching**:
  - In `fetchHoldersAndActivity()`, after fetching the top 10 accounts from `/tokens/ECAT-4ebd0f/accounts`:
    - For each account without cached metadata:
      - If `account.assets && account.assets.name`, cache as protocol label (e.g. `xExchange: ECAT/WEGLD LP`).
      - Otherwise, query `https://api.multiversx.com/accounts/{address}` concurrently using `Promise.all` with a 1.2s timeout fallback.
      - If `username` is present, format as `@username` (stripping `.elrond`), e.g. `poshanarchist.elrond` → `@poshanarchist`.
      - Store in `cachedHerotags`.

### 2. UI Markup & Row Templating (`#holdersTableBody`)
- **Holder Identity Presentation**:
  - Render an identity block containing:
    - **For Herotagged Accounts**:
      - A stylish `@username` badge (`.holder-herotag`) in bold cyan with a subtle `@` icon.
      - Hover tooltip displaying full `erd1...` address.
    - **For Protocol / Liquidity Pools**:
      - Protocol label with a subtle `.holder-protocol` badge (`xExchange LP`).
    - **For Standard Accounts**:
      - Clean truncated address (`erd1...xxxx`) in monospace.
  - **Copy Button**:
    - Keeps the 1-click clipboard copy button that copies the underlying full `erd1...` wallet address with `#copyToast` confirmation.
  - **Explorer Link**:
    - Keeps the external link opening `https://explorer.multiversx.com/accounts/{address}` in a new tab.

### 3. Styling & Micro-interactions (CSS)
- `.holder-herotag`: Cyan gradient text (`var(--color-primary)`), font-weight 700, with a mini `@` pill indicator.
- `.holder-protocol`: Purple/indigo accent (`var(--color-primary-2)`) with a compact protocol chip.
- Responsive layout: Monospace fallback and herotag containers enforce `max-width: 180px` on mobile (< 640px) with `text-overflow: ellipsis` to guarantee zero table overflow.

---

## Dependencies & API Endpoints
- Top accounts endpoint: `https://api.multiversx.com/tokens/ECAT-4ebd0f/accounts?size=10`
- Account details endpoint: `https://api.multiversx.com/accounts/{address}`
- Explorer account URL: `https://explorer.multiversx.com/accounts/{address}`

---

## Acceptance Criteria
- [ ] Top 10 holder rows resolve on-chain herotags in parallel and format them as `@username` (e.g. `@poshanarchist`, `@adriancodarcea`).
- [ ] Known protocol liquidity pools display clean asset labels (e.g. `xExchange: ECAT/WEGLD LP`).
- [ ] Accounts without herotags display standard truncated addresses (`erd10wfe...yjwx`).
- [ ] Copy button copies the full underlying `erd1...` wallet address with toast notification.
- [ ] Explorer link opens account details on `explorer.multiversx.com`.
- [ ] Resolved identities are cached in memory to prevent repeat network calls during 30s polling.
- [ ] Mobile viewports (< 640px) render legibly without table blowout.
