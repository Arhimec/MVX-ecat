---
intent: 003-ecompass-chart
phase: inception
status: context-defined
updated: 2026-09-30T20:20:10Z
---

# 003-ecompass-chart - System Context

## System Overview
The eCompass Chart Module integrates the live MultiversX DEX candlestick and liquidity pool charting engine (`e-compass.io`) directly into the $ECAT landing page. It introduces an interactive view mode switcher in the price card, allowing visitors to alternate between the comprehensive eCompass candlestick trading terminal and the simplified SVG trajectory curve.

## Context Diagram

```mermaid
graph TD
    User["Web Visitor / Trader"] -->|Views & Toggles Chart| ECATApp["ECAT Webpage (index.html)"]
    
    subgraph Client Application
        ECATApp --> PriceCard["Price Card & Chart Studio"]
        PriceCard --> ModeSwitcher["Chart Mode Controller"]
        ModeSwitcher -->|Mode: eCompass| EcompassFrame["eCompass Iframe Container"]
        ModeSwitcher -->|Mode: Overview| SVGChart["Simplified SVG Price Chart"]
    end
    
    subgraph External Platforms
        EcompassFrame -->|HTTPS Embed| EcompassIO["e-compass.io/tokens/ECAT-4ebd0f"]
        User -->|Click Open in eCompass| EcompassPortal["eCompass Token Analytics Portal"]
    end
```

## External Integrations
- **eCompass MultiversX Token Portal (`https://e-compass.io/tokens/ECAT-4ebd0f`)**: Source for live interactive DEX candlestick charts, price history, and liquidity analytics.
- **MultiversX Explorer**: Deep link reference for on-chain contract and asset verification.

## High-Level Constraints
- Zero external build tool dependencies.
- Secure iframe sandboxing allowing necessary script execution and popups while protecting host DOM.
- Seamless cosmic dark styling (`#070B12`, cyan `#23F7DD`) with responsive height adjustment.
