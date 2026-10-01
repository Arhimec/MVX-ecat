---
version: "v1.1.0"
unit: "001-leaderboard-activity-ui"
intent: "002-holder-leaderboard"
configured: "2026-09-30T20:12:45Z"
status: "active"
---

# Observability & Monitoring: 001-leaderboard-activity-ui

## Observability Architecture
The Holder Leaderboard and Live Activity feed operate within the client browser, directly communicating with MultiversX public REST endpoints (`/tokens/ECAT-4ebd0f/accounts` and `/tokens/ECAT-4ebd0f/transfers`).

```text
[Client Browser]
      │
      ├──> MultiversX Accounts API (/tokens/ECAT-4ebd0f/accounts?size=10)
      │      └── Renders: Top 10 Leaderboard, Tier Badges, Supply Share Bar
      │
      ├──> MultiversX Transfers API (/tokens/ECAT-4ebd0f/transfers?size=10)
      │      └── Renders: Live Activity Stream, Relative Time, Tx Links
      │
      └──> Client Error Boundaries & UX Guards
             ├── Tab Visibility Optimization (pauses background polling)
             ├── Cached State Preservation (no empty screen on rate limits)
             └── Clipboard API with Animated Toast Feedback (#copyToast)
```

---

## Service Level Objectives (SLOs)

| Metric | Target | Measurement Method | Alert / Degraded State |
|--------|--------|---------------------|------------------------|
| **Accounts API Latency** | < 350ms (p95) | Endpoint roundtrip timing | p95 > 800ms over 5 consecutive intervals |
| **Transfers API Latency** | < 350ms (p95) | Endpoint roundtrip timing | p95 > 800ms over 5 consecutive intervals |
| **Data Freshness** | <= 60 seconds | Browser polling clock (30s interval) | No fresh transactions for > 5 minutes |
| **Client Error Boundary Rate** | < 0.1% | Catch block activations | > 3 consecutive fetch failures |

---

## Incident Response Runbooks

### Runbook 1: MultiversX Indexer High Latency or 429 Throttle
- **Symptom**: Leaderboard or activity feed displays "temporarily busy / retrying in 30s".
- **Cause**: Shared MultiversX public gateway rate limit exceeded during periods of high market volatility.
- **Automated Mitigation**:
  - The client automatically preserves `cachedHolders` and `cachedTransfers` in memory.
  - Existing DOM is kept intact without destructive clearing.
  - Page Visibility API ensures background tabs do not compound request volume.
- **Manual Escalation**:
  - Increase `POLL_INTERVAL_MS` from 30,000ms to 60,000ms.
  - Provision a dedicated MultiversX API proxy with Cloudflare edge caching (TTL: 20s).

### Runbook 2: Empty Recent Transfers (Quiet Trading Periods)
- **Symptom**: Transfers feed displays "No recent transfers recorded on-chain yet."
- **Verification**: Check on-chain explorer: `https://explorer.multiversx.com/tokens/ECAT-4ebd0f`.
- **Expected Behavior**: When no transfers occurred recently, the UI gracefully informs the visitor rather than throwing an error.

### Runbook 3: Clipboard Copy Permission Denial
- **Symptom**: Clicking copy button fails on older mobile browsers.
- **Mitigation**: Built-in fallback to `document.execCommand('copy')` triggers automatically when `navigator.clipboard` is restricted.
