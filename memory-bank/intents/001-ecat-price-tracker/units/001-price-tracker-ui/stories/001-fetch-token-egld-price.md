---
id: 1
title: Fetch Token & EGLD Price Data
unit: 001-price-tracker-ui
intent: 001-ecat-price-tracker
priority: Must
status: complete
created: 2026-09-30T19:34:50.000Z
implemented: true
---

# Story 001: Fetch Token & EGLD Price Data

## User Story
**As a** landing page visitor
**I want** the page to automatically fetch the latest ECAT token data and MultiversX EGLD price
**So that** I have immediate access to accurate, up-to-date market information.

## Acceptance Criteria
- [ ] Fetches token information from `https://api.multiversx.com/tokens/ECAT-4ebd0f`.
- [ ] Concurrently fetches EGLD economic metrics from `https://api.multiversx.com/economics`.
- [ ] Parses token supply, price, accounts, transactions, and EGLD USD price.
- [ ] Computes the ECAT/EGLD exchange ratio (`ecatPriceUsd / egldPriceUsd`).
- [ ] Safely catches network failures and reports structured errors without uncaught exceptions.
