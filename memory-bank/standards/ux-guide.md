# UI/UX Guide

## Overview
UI/UX standards and design system choices for the MultiversX token tracking web application, built around a modern, premium crypto dashboard experience.

## Design System & Visual Theme
- **Theme**: Dark mode first.
- **Palette**:
  - MultiversX Primary / Accent: `#23F7DD` (Neon Cyan/Teal)
  - Secondary Accent: `#007BFF` / `#4C82FB`
  - Background Base: `#0B0E14` (Deep obsidian)
  - Card & Container Surface: `rgba(18, 24, 38, 0.75)` with frosted glassmorphism (`backdrop-filter: blur(14px)`)
  - Border Highlights: `rgba(35, 247, 221, 0.15)`
  - Text Primary: `#F0F4F8`
  - Text Muted: `#8B949E`
  - Metric Positive (Gain): `#00E676` (Neon Green)
  - Metric Negative (Loss): `#FF5252` (Coral Red)
- **Typography**: Clean modern sans-serif (`system-ui, -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, sans-serif`) with `font-variant-numeric: tabular-nums` for rock-steady numerical crypto price counters.

## Styling Approach
- **CSS Architecture**: Vanilla CSS using custom properties (CSS variables) for tokens in `style.css`.
- **Layout**: Flexbox and CSS Grid layouts.
- **Motion & Micro-interactions**: Smooth transitions (`cubic-bezier(0.4, 0, 0.2, 1)`), subtle glow effects on hover, pulse animations on live price updates.

## Accessibility Standards
- **Contrast**: WCAG 2.1 AA compliant color contrast ratios for all critical text and price indicators.
- **Dynamic Updates**: `aria-live="polite"` on price counters and status badges for screen reader announcements.
- **Semantic HTML**: Buttons, labels, inputs, and article containers with appropriate accessibility roles.

## Responsive Strategy
- **Approach**: Mobile-first design.
- **Breakpoints**:
  - Mobile: `< 640px` (stacked cards, compact metrics)
  - Tablet: `640px - 1024px` (dual-column layout)
  - Desktop: `> 1024px` (expansive dashboard grid with live charts/stats)
