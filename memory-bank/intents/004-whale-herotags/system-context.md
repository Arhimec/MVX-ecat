# System Context: 004-whale-herotags

## Overview
This feature extends the client-side data layer of the $ECAT landing page (`index.html`) to resolve and display on-chain MultiversX Herotags (`@username`) and verified protocol asset names for top token holders.

```text
                               ┌────────────────────────────────────────────────────────┐
                               │                 MultiversX Public API                  │
                               └──────────┬─────────────────────────────────┬───────────┘
                                          │                                 │
     1. Fetch Top 10 Accounts             │                                 │ 2. Fetch Account Details
     GET /tokens/ECAT-4ebd0f/accounts     │                                 │ GET /accounts/{address}
                                          ▼                                 ▼
                         ┌───────────────────────────────────┐     ┌──────────────────┐
                         │      Client Holder Processor      │◄────┤ Herotag Memory   │
                         │      (fetchHoldersAndActivity)    │     │ Cache (Map)      │
                         └─────────────────┬─────────────────┘     └──────────────────┘
                                           │
                                           │ Normalizes Identity:
                                           │ - Herotag: "@poshanarchist"
                                           │ - Protocol: "xExchange: ECAT/WEGLD LP"
                                           │ - Fallback: "erd10wfe...yjwx"
                                           ▼
                         ┌────────────────────────────────────────────────────────┐
                         │               Whale Leaderboard Table UI               │
                         │              (#holdersTableBody in DOM)                │
                         │                                                        │
                         │  [#1 🐋] @poshanarchist   716,395,925 ECAT (71.6%)     │
                         │  [#2 🐋] xExchange LP      78,138,083 ECAT (7.8%)      │
                         │  [#3 🐋] erd10wfe...yjwx   31,492,335 ECAT (3.1%)      │
                         │  ...                                                   │
                         │  [#10🐾] @adriancodarcea   10,914,337 ECAT (1.1%)      │
                         └────────────────────────────────────────────────────────┘
```

---

## External Integrations

| Service / Endpoint | Method | Purpose | Response Fields |
|---|---|---|---|
| `https://api.multiversx.com/tokens/ECAT-4ebd0f/accounts?size=10` | GET | Top holder accounts and balances | `address`, `balance`, `assets.name` |
| `https://api.multiversx.com/accounts/{address}` | GET | On-chain account profile & herotag | `username` (e.g. `poshanarchist.elrond`) |
| `https://explorer.multiversx.com/accounts/{address}` | Link | Direct blockchain explorer account view | N/A (External Portal) |

---

## Identity Resolution Rules

1. **Known Asset / Liquidity Pool**:
   - Condition: `account.assets && account.assets.name`
   - Rendering: Display asset name with protocol badge (e.g. `xExchange: ECAT/WEGLD Liquidity Pool`).
2. **Registered Herotag**:
   - Condition: `accountData.username` exists and is non-empty.
   - Processing: Strip `.elrond` suffix, prepend `@` (e.g. `poshanarchist.elrond` → `@poshanarchist`).
   - Rendering: Display `@username` in bold cyan with herotag pill.
3. **Unregistered Account Fallback**:
   - Condition: No `assets.name` and no `username`.
   - Rendering: Display truncated wallet address (`erd10wfe...yjwx`).
