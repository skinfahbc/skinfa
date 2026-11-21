---
name: impeccable
description: Use for shaping, critiquing, auditing, polishing, simplifying, hardening, animating, and improving SKINFA frontend interfaces. Covers UX, hierarchy, layout, typography, color, motion, accessibility, responsive behavior, edge cases, and design-system documentation. Not for backend-only work.
---

# Impeccable — SKINFA project edition

A project-local design workflow inspired by the public Impeccable project by Paul Bakaus (Apache-2.0): https://github.com/pbakaus/impeccable
This file is a lightweight SKINFA adaptation, not the complete upstream distribution or its CLI, hooks, detector, browser live mode, or command engine.

## First principles
- The user's brief and the existing SKINFA brand decisions win. Do not impose a generic trendy aesthetic.
- Refinement preserves existing identity, behavior, copy, and everything outside scope. Redesign only when explicitly requested.
- Finish the task: implement, inspect the rendered result when a browser is available, correct visible issues, and report any unverified behavior honestly.
- Match ambition to the surface: Persuade (marketing and storefront), Operate (admin, chat, checkout), Read (help and documentation), Experience (galleries and showcases).
- Keep Persian RTL, mobile behavior, accessibility, performance, and real content central to every decision.

## Workflow
1. Understand the requested surface, audience, user goal, constraints, and whether this is refinement or redesign.
2. Inspect the current implementation and visual system before editing. Reuse existing tokens and components where they are sound.
3. State a concise design direction internally before implementation: hierarchy, layout, typography, color, imagery, interaction, and motion.
4. Make focused changes. Avoid generic SaaS patterns, unnecessary cards, decorative gradients, excessive rounded containers, low-contrast text, and gratuitous animation.
5. Verify the actual rendered page at mobile and desktop sizes where possible. Check long Persian labels, overflow, focus, touch targets, keyboard behavior, loading/empty/error states, and reduced motion.
6. Summarize changed files, behavior, checks performed, and anything that still needs a real-device test.

## Design actions
When the user asks for:
- **shape**: plan the UX, page structure, and interaction model before coding.
- **init**: capture product context in PRODUCT.md (audience, use cases, value, tone, constraints).
- **document**: document the existing visual system in DESIGN.md.
- **extract**: identify reusable design tokens and components from the current code.
- **critique**: assess hierarchy, clarity, consistency, emotional resonance, and task completion; give prioritized findings.
- **audit**: inspect accessibility, responsive behavior, performance, semantic HTML, and interaction states.
- **polish**: perform a final visual and interaction refinement pass.
- **bolder / quieter / distill**: increase distinctiveness / reduce visual intensity / remove unnecessary complexity without harming usability.
- **harden**: handle errors, edge cases, localization, overflow, and resilient states.
- **onboard**: improve first-run, empty, and activation experiences.
- **animate**: add purposeful, interruptible motion and honor reduced-motion preferences.
- **colorize / typeset / layout / delight / overdrive**: improve color, typography, spacing and hierarchy, personality, or visual ambition while preserving product fit.
- **clarify**: improve labels, instructions, and error messages without changing factual meaning.
- **adapt**: improve device and viewport behavior, especially narrow mobile.
- **optimize**: improve loading, rendering, and interaction performance.
- **generate / live**: propose distinct alternatives for a named element; do not claim live browser tooling exists unless it is actually installed and running.

## SKINFA-specific guardrails
- Preserve the established SKINFA/SISE identity and current color decisions unless the request changes them.
- Make storefront imagery and product presentation feel premium, but do not distort product truth.
- Admin surfaces should optimize scanability and task speed, not marketing-style decoration.
- Every visible control must work; do not add decorative buttons or fake interactions.
- Avoid changing authentication, Supabase, checkout, inventory, customer data, or deployment behavior during visual tasks unless explicitly requested.
- Use transforms and opacity for motion where possible; avoid layout-thrashing animations.
- Respect prefers-reduced-motion. Never make essential functionality depend on animation or gestures.
- Ensure touch targets, safe areas, keyboard handling, RTL direction, and Persian text wrapping work on mobile.

## Completion standard
A task is not complete merely because code was written. Verify the changed surface when tools permit, fix issues found, and distinguish verified results from assumptions. Never claim browser, automated, or physical-device tests that were not run.
