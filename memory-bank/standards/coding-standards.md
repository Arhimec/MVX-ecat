# Coding Standards

## Overview
Standards for writing clean, accessible, and maintainable Vanilla Web code (HTML5, CSS3, ES6+ JavaScript) with clear separation of concerns across document structure, styling, and application logic.

## Code Formatting
- **Indentation**: 2 spaces for HTML, CSS, and JavaScript.
- **Line Length**: Soft wrap around 100-120 characters.
- **Quotes**: Double quotes in HTML attributes; single quotes (or template literals) in JavaScript.
- **Semicolons**: Always included in JavaScript.
- **CSS**: Modern CSS syntax with kebab-case class names, organized CSS custom properties (variables) defined on `:root`.

## Linting & Quality
- **Base Standards**: Modern ECMAScript (ES2022+).
- **Strict Mode**: Use `'use strict';` or standard module-level strict execution.
- **Avoid Global Pollution**: Encapsulate logic inside modules or init scopes.
- **Code Hygiene**: No dead or commented-out code; remove debug `console.log` statements from final release code.

## Naming Conventions
| Element | Convention | Example |
|---------|------------|---------|
| Variables & Functions | camelCase | `tokenPrice`, `fetchTokenDetails()` |
| Constants & Config | UPPER_SNAKE_CASE | `API_BASE_URL`, `DEFAULT_POLL_INTERVAL` |
| CSS Classes | kebab-case | `.token-card`, `.price-badge` |
| HTML IDs | kebab-case | `#token-search-input`, `#price-display` |
| Files | kebab-case | `index.html`, `style.css`, `app.js` |

## File Organization
**Pattern**: Modular Vanilla Web structure:
```text
MVX-ecat/
├── index.html       # Semantic HTML layout and UI scaffolding
├── style.css        # Design tokens, layouts, responsive styles, animations
├── app.js           # API interaction, state management, DOM event handling
└── memory-bank/     # SpecsMD AI-DLC governance and context
```

## Testing Strategy
- **Verification Method**: Browser runtime testing, network payload validation against MultiversX API, and UI state verification (loading, loaded, error/offline states).
- **Coverage**: Critical user paths (loading token, polling/updating price, handling invalid token identifier or network failure).

## Error Handling
- **Async Pattern**: `try/catch` wrapping all asynchronous `fetch` calls.
- **User-Facing States**: Always render user-friendly error banners or fallback indicators in the UI rather than silent failures or raw console crashes.
- **Network Resilience**: Check `response.ok` before JSON parsing and handle HTTP 404 / 429 / 500 cleanly.

## Logging
- **Console Log Levels**:
  - `console.error`: For failed network requests or unexpected runtime exceptions.
  - `console.warn`: For deprecations or non-blocking API limits.
  - `console.info`: For major lifecycle events (e.g. tracking initialized, socket/poll connected).
- **Rules**: Never log sensitive user data or private keys.
