---
name: skinfa-ui-craft
description: Apply Emil Kowalski-inspired design-engineering principles when building or reviewing SKINFA interfaces, animations, gestures, and mobile web interactions.
---

# SKINFA UI Craft

Use this project skill when implementing or reviewing frontend UI, especially navigation, menus, dialogs, sheets, carousels, product galleries, chat, dashboards, and mobile layouts.

This is a project-specific guide inspired by the public concepts in Emil Kowalski's skills collection. It is not a copy of the upstream package.

## Design priorities
- Make the interface intentional, calm, premium, and distinctive; avoid generic template styling.
- Preserve SKINFA's existing brand language and established design decisions. Do not redesign unrelated areas.
- Prioritize hierarchy, spacing, typography, contrast, alignment, and clear interaction states before decoration.
- Every interactive control needs a clear purpose, visible feedback, and a working action.
- Prefer subtle borders, layered surfaces, restrained shadows, and consistent radii over excessive gradients, glow, or ornamental effects.
- Keep Persian RTL layouts correct at all viewport sizes.

## Motion and animation
- Animate with purpose: communicate state changes, spatial relationships, and feedback.
- Prefer transform and opacity for smooth animation; avoid animating layout-heavy properties when possible.
- Prefer ease-out for entrances, ease-in for exits, and spring-like motion only when it supports the interaction.
- Keep most UI transitions short and responsive; avoid slow decorative motion that delays tasks.
- Respect the prefers-reduced-motion media preference.
- Make animations interruptible where practical. Reversing or repeating an interaction should not cause jumps.
- Do not animate every element; choose moments where motion improves comprehension.

## Touch and mobile-native behavior
- Design for touch on narrow screens: comfortable hit areas, clear pressed states, no hover-only actions.
- Account for safe areas, browser viewport changes, virtual keyboards, and scrolling behavior.
- Prevent accidental horizontal overflow and unintended page scroll locking.
- Carousels and swipe interactions must be predictable and must not hijack normal vertical scrolling.
- Avoid input styles that trigger unwanted mobile browser zoom.
- Test responsive states at small widths and with long Persian text.

## Gestures and overlays
- Drag interactions should track the pointer/finger directly and respond naturally to release velocity.
- Sheets, popovers, and dialogs should have clear entry/exit origins and dismiss behavior.
- Keep keyboard, focus, escape-key, and screen-reader behavior usable where relevant.
- Never make essential functionality depend only on animation or gesture.

## Review checklist
1. Check desktop, tablet, and narrow mobile layouts.
2. Check loading, empty, error, success, and long-content states where relevant.
3. Verify every button, link, menu, form, and gesture actually works.
4. Review animation timing, easing, origin, interruption, and reduced-motion behavior.
5. Check contrast, focus visibility, RTL direction, and text wrapping.
6. Confirm no unrelated page, data flow, authentication, checkout, or backend behavior changed.
7. Summarize changed files and anything that still needs real-device testing.

## Working rules
- Inspect the existing implementation before editing.
- Make the smallest complete change that solves the requested task.
- Do not replace established components or libraries without a concrete reason.
- Do not change production data, secrets, environment variables, authentication, or deployment settings as part of visual work.
- Never claim a change was tested on a physical phone unless it actually was.
