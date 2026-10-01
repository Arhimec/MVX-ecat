---
version: "v1.3.0"
unit: "001-herotags-resolution"
intent: "004-whale-herotags"
configured: "2026-10-01T22:53:35Z"
status: "active"
---

# Observability & Monitoring: 001-herotags-resolution

## Observability Architecture
The Herotag resolution mechanism runs client-side in the visitor's browser, querying MultiversX public REST endpoints (`/tokens/ECAT-4ebd0f/accounts` and `/accounts/{address}`).

```text
[Client Browser]
      │
      ├──> MultiversX Accounts Indexer (/tokens/ECAT-4ebd0f/accounts?size=10)
      │      └── Returns: Top 10 Accounts, Balances, Assets Metadata
      │
      ├──> MultiversX Account Profiles (/accounts/{address})
      │      ├── Non-blocking concurrent queries (Promise.allSettled)
      │      ├── 2000ms AbortController timeout boundary
      │      └── Normalizes herotags: '@username' (stripping '.elrond')
      │
      ├──> In-Memory Identity Cache (cachedHerotags Map)
      │      └── Prevents duplicate requests during 30s polling intervals
      │
      └──> Client Error Boundaries & UX Guards
             ├── Automatic fallback to truncated address (erd1...xxxx) on timeout
             └── Preserves full erd1... address for clipboard copy actions
```

---

## Service Level Objectives (SLOs)

| Metric | Target | Measurement Method | Alert / Degraded State |
|--------|--------|---------------------|------------------------|
| **Account Identity Resolution Latency** | < 400ms (p95) | Concurrent roundtrip timing | p95 > 1000ms over 3 intervals |
| **Identity Cache Hit Rate** | >= 90% | Ratio of cached vs. fresh lookups | Cache empty after initial page load |
| **Herotag Resolution Availability** | >= 99.0% | Account query success rate | MultiversX gateway returns 429/500 |
| **Zero Layout Distortion** | 100% | CSS ellipsis truncation | Username overflowing table cell width |

---

## Incident Response Runbooks

### Runbook 1: MultiversX Account API Rate Limiting (HTTP 429)
- **Symptom**: New holders display truncated addresses instead of herotags.
- **Cause**: High traffic or shared IP limits on public `api.multiversx.com`.
- **Mitigation**:
  - The client gracefully falls back to truncated addresses without throwing uncaught exceptions.
  - Existing resolved herotags remain preserved in `cachedHerotags`.
  - Background polling continues on the 30-second timer.

### Runbook 2: Network Timeout on Herotag Queries
- **Symptom**: Leaderboard table renders addresses first, then herotags appear after 1–2 seconds.
- **Expected Behavior**: The two-stage rendering model ensures table metrics (Rank, Balance, Share %) are immediately visible; herotags populate progressively as responses arrive.
