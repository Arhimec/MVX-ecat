# Tech Stack

## Overview
Lightweight static frontend application for tracking MultiversX token prices, built using native web standards with zero build tooling or compilation overhead.

## Languages
- **HTML5**: Semantic web document structure.
- **CSS3**: Modern styling with custom properties (CSS variables), Flexbox/Grid, and responsive design.
- **JavaScript (ES6+)**: Client-side logic, asynchronous API fetching, and direct DOM manipulation.

*Rationale*: Zero setup friction, maximum runtime performance, and instant live reloading in any standard web browser without dependencies.

## Framework
- **Vanilla Web (None)**: Native DOM APIs, `fetch` for HTTP queries.

*Rationale*: The application scope is focused (displaying token metrics and live price tracking from MultiversX public APIs). Avoiding heavy frameworks eliminates unnecessary build complexity and bundle size.

## Authentication
- **None**: Public MultiversX APIs (e.g. `api.multiversx.com`) do not require authentication for public token queries.

## Infrastructure & Deployment
- **Static Web Hosting**: Ready for immediate local execution (opening `index.html`), GitHub Pages, Cloudflare Pages, Vercel, or Netlify.

## Package Manager
- **None required**: Native browser execution without `npm`/`pnpm` dependencies.

## Decision Relationships
- The choice of Vanilla JavaScript directly aligns with zero-build static hosting and standard browser `fetch` calls against MultiversX REST endpoints.
