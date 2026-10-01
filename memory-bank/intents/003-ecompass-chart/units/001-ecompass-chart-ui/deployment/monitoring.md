---
version: "v1.2.0"
unit: "001-ecompass-chart-ui"
intent: "003-ecompass-chart"
configured: "2026-09-30T23:58:30Z"
status: "active"
---

# Observability & Monitoring: 001-ecompass-chart-ui

## Observability Architecture
The eCompass interactive chart is delivered via a sandboxed iframe communicating with the e-compass.io cloud infrastructure, coupled with a client-side dual-view switcher and fallback Overview SVG curve.

```text
[Client Browser]
      │
      ├──> eCompass Interactive Embed (https://e-compass.io/token/ECAT-4ebd0f)
      │      ├── Sandboxed Iframe (allow-scripts allow-same-origin allow-popups)
      │      ├── Skeleton Loader Screen (cosmic spinner & CSS shimmer)
      │      └── Quick Action Link (Open in eCompass ↗)
      │
      ├──> Dual-Mode View Switcher State
      │      ├── Default: eCompass DEX Chart view
      │      └── Alternative: Native SVG Overview Curve with Timeframe Selectors
      │
      └──> Client Error Boundaries & UX Guards
             ├── Skeleton fade-out on iframe onload
             └── Native SVG overview fallback available on 1-click
```

---

## Service Level Objectives (SLOs)

| Metric | Target | Measurement Method | Alert / Degraded State |
|--------|--------|---------------------|------------------------|
| **eCompass Embed Availability** | >= 99.5% | HTTP status & frame load checks | Target endpoint returns non-200 or connection timeout |
| **Iframe Load Time** | < 2.0s (p95) | Window onload event timing | Loader visible for > 5 seconds |
| **View Toggle Latency** | < 50ms | Browser DOM toggle response | Noticeable visual lag or layout shift |
| **Responsive Adaptation** | 100% | Viewport resize handling | Viewport < 768px exceeding 420px height |

---

## Incident Response Runbooks

### Runbook 1: eCompass Service Degraded or Unreachable
- **Symptom**: Iframe displays connection failure or fails to resolve `e-compass.io`.
- **Cause**: Upstream DNS, CDN, or maintenance event on `e-compass.io`.
- **Mitigation**:
  1. Users can immediately click the **Overview Curve 📈** button in the top toolbar to switch to the native SVG price chart.
  2. The external link (`Open in eCompass ↗`) allows visitors to verify upstream status directly.
  3. No breaking exceptions cascade to the price tracker or holder leaderboard.

### Runbook 2: Restricted Browser Iframe Policies
- **Symptom**: In strict enterprise browser environments with complete iframe blocking, the iframe container remains blank.
- **Mitigation**:
  - The skeleton loader provides visual context and the external link `#btnOpenEcompass` is always clickable in the toolbar, directing the user directly to `https://e-compass.io/tokens/ECAT-4ebd0f`.

### Runbook 3: Slow Network Connections (Mobile 3G/4G)
- **Symptom**: Prolonged skeleton screen display while DEX candlestick data downloads.
- **Expected Behavior**: The skeleton loader prevents blank content flashes and maintains layout stability at 420px height until the frame has finished loading.
