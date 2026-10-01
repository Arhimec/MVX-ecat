---
version: "v1.0.0"
unit: "001-price-tracker-ui"
intent: "001-ecat-price-tracker"
configured: "2026-09-30T19:53:00Z"
status: "active"
---

# Observability & Monitoring: 001-price-tracker-ui

## Observability Architecture
The ECAT Price Tracker operates as a high-performance, client-side web application querying MultiversX public REST infrastructure. Observability is structured across client telemetry, API endpoint health, and UX resilience.

```text
[Client Browser] 
      │
      ├──> MultiversX REST API (api.multiversx.com)
      │      ├── /tokens/ECAT-4ebd0f
      │      └── /economics
      │
      └──> Telemetry & Error Boundary
             ├── Network Status Badge: [Live Network / Connecting... / Error]
             ├── Page Visibility Guard: [Halt polling when tab hidden]
             └── Graceful Degradation: [Retain last known good cache]
```

---

## Service Level Objectives (SLOs)

| Metric | Target | Measurement Method | Alert Threshold |
|--------|--------|---------------------|-----------------|
| **Client Availability** | 99.9% uptime | CDN synthetic ping (200 OK) | Uptime < 99.5% over 15m |
| **API Latency (p95)** | < 350ms | MultiversX REST API dual fetch | p95 > 800ms over 5m |
| **Data Freshness** | <= 60 seconds | Browser polling clock (30s interval) | No fresh data for > 3m |
| **Fetch Error Rate** | < 0.2% | Client-side catch blocks | Consecutive failures > 3 |

---

## Telemetry & Client Indicators

1. **Pulse Indicator (`#liveStatusPill`)**:
   - **Green Glow**: Live updates receiving fresh blocks from MultiversX network.
   - **Amber / Connecting**: In-flight request or initial load.
   - **Red Glow**: Consecutive fetch failures triggered; fallback values preserved.
2. **Resource Optimization**:
   - `document.visibilityState`: Polling automatically freezes while user is away from tab.
   - Prevents MultiversX public API IP rate throttling (429 Too Many Requests).

---

## Incident Response Runbooks

### Runbook 1: MultiversX Public API Rate Limiting (HTTP 429)
- **Symptom**: Red pulse indicator, console warnings on `api.multiversx.com`.
- **Cause**: Spike in concurrent users exceeding MultiversX public gateway shared rate limit (approx. 2 requests/sec unauthenticated).
- **Remediation**:
  1. Increase polling interval from `30000ms` (30s) to `60000ms` (60s) in `index.html`.
  2. Implement an optional API proxy / Cloudflare Worker with cached responses (TTL 15s).
  3. Configure MultiversX dedicated API key header (`api-key: <TOKEN>`) on gateway.

### Runbook 2: Network Degradation / Outage on EGLD Economics
- **Symptom**: USD price displays correctly, but EGLD pair displays `--` or fallback.
- **Cause**: `https://api.multiversx.com/economics` experiencing downtime or shard latency.
- **Remediation**:
  1. Client automatically suppresses crash via `.catch(() => null)` isolation.
  2. USD market metrics remain fully operational.
  3. Last known EGLD valuation is retained in memory.

### Runbook 3: Token Liquidity Pool Migration
- **Symptom**: Sudden drop or change in volume / price.
- **Cause**: Liquidity migrated to a new MultiversX DEX pool or wrapper.
- **Verification**:
  - Check on-chain token explorer: `https://explorer.multiversx.com/tokens/ECAT-4ebd0f`.
  - Validate locked DEX liquidity pairs on xExchange / AshSwap / OneDex.
