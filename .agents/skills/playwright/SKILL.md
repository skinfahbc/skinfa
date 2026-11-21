---
name: playwright
description: Browser testing and automation for SKINFA/SISE. Use when validating pages, interactions, forms, navigation, responsive layouts, accessibility, screenshots, or debugging frontend behavior with Playwright.
---

# Playwright — SKINFA project testing guide

This project guide is adapted from the Playwright browser-automation skill:
https://github.com/lackeyjb/playwright-skill

It describes how an agent should use Playwright in a compatible development environment. It does not itself install the Playwright npm package, browser binaries, helper scripts, or a running browser.

## Purpose
Use a real browser to verify what users actually experience. Do not treat successful code edits or a successful build as proof that the page works.

## Before testing
1. Inspect the repository and identify its framework, package manager, scripts, and existing test setup.
2. Prefer the project's existing Playwright configuration and conventions. Do not create a second configuration unnecessarily.
3. Detect the current dev server and use its actual URL. If none is running, use the project's documented start command when the environment permits; otherwise ask for the URL or explain what is missing.
4. Prefer local, preview, or staging environments. Do not run destructive tests against production.
5. Use only credentials and test accounts supplied or configured for testing. Never invent credentials, print secrets, or expose authentication state.
6. Use isolated test data. Avoid real purchases, payments, customer messages, account changes, or destructive admin actions unless the user explicitly authorizes them.

## Locator and assertion standards
Prefer user-visible, resilient locators in this order:
1. `getByRole()` with an accessible name.
2. `getByLabel()` for form fields.
3. `getByPlaceholder()` only when it reflects a stable user-facing placeholder.
4. `getByText()` for visible content.
5. `getByTestId()` when the project defines a deliberate test contract.

Avoid brittle CSS/XPath selectors when a semantic locator is possible. Use Playwright's auto-waiting and web-first assertions. Do not add fixed sleeps or rely on `networkidle` as a generic readiness signal.

## SKINFA test coverage
When relevant, verify:
- Main navigation, menus, links, route changes, and browser back/forward behavior.
- Product gallery controls, image ratios, variant selection, product details, and add-to-cart behavior.
- Cart quantity changes, removal, totals, empty state, and persistence where implemented.
- Forms: labels, validation, error messages, success states, and keyboard submission.
- Messenger and support flows using safe test accounts and non-sensitive test content.
- Admin controls and upload flows using test data only.
- Loading, empty, error, disabled, and success states.
- Persian RTL direction, text wrapping, mixed Persian/Latin content, and numeral display.

Do not assert that a feature exists unless it is present in the current implementation or explicitly specified by the user.

## Responsive and visual checks
At minimum, when the page is responsive, inspect:
- Desktop: 1440 × 900
- Tablet: 768 × 1024
- Mobile: 390 × 844
- Narrow mobile: 320px width for overflow and collision checks

At each size, check horizontal overflow, clipped content, overlapping elements, sticky/fixed bars, modal fit, touch target size, and readable Persian text. Capture screenshots when visual comparison is useful. Compare before/after screenshots if available; do not claim a visual regression pass without reviewing the output.

## Accessibility checks
Check keyboard navigation, visible focus, semantic roles and names, form labels, image alternative text, dialog behavior, and reduced-motion behavior where applicable. Playwright checks do not replace a dedicated accessibility audit.

## Test design
- Keep tests independent and deterministic.
- Use explicit expectations for important user outcomes, not merely that a click did not throw.
- Wait for a meaningful state change: URL, visible heading, status message, or updated data.
- Prefer API/database setup only when the project already has safe test fixtures and the test environment is known.
- Do not silently swallow console errors, failed requests, or assertion failures.
- Do not weaken assertions just to make a test pass.

## Example
```js
import { test, expect } from '@playwright/test';

test('product can be added to the cart', async ({ page }) => {
  await page.goto(process.env.BASE_URL);
  await page.getByRole('link', { name: /products|محصولات/i }).click();
  await page.getByRole('button', { name: /add to cart|افزودن به سبد خرید/i }).first().click();
  await expect(page.getByRole('link', { name: /cart|سبد خرید/i })).toBeVisible();
});
```

Adapt route names and accessible labels to the actual application. The example is illustrative and must not be reported as an executed test.

## Reporting
For every browser-testing task, report:
- The URL/environment and browser used.
- The tests and viewport sizes actually checked.
- Passes and failures, with concise evidence.
- Screenshots or trace paths only when they were actually created and verified.
- Anything not tested, especially authentication, payment, production data, or real-device behavior.

Never claim that Playwright ran, a test passed, or a screenshot exists unless the command completed and the result was inspected.
