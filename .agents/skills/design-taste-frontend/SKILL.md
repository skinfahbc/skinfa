---
name: design-taste-frontend
description: Apply Taste Skill-inspired art direction and anti-generic frontend standards to SKINFA/SISE storefronts and web experiences. Use when building, redesigning, restyling, or reviewing frontend pages and components.
---

# Taste Skill — SKINFA project edition

Inspired by the open-source Taste Skill by Leonxlnx:
https://github.com/Leonxlnx/taste-skill
https://www.tasteskill.dev/

This is a project-adapted guide, not the complete upstream distribution. The upstream package includes a large asset library, scripts, browser checker, and finish gate that are not bundled in this file.

## Mission
Build interfaces that look deliberately art-directed for this brand and its customers—not like generic AI templates. Every page should communicate what is offered, show the real product or service, and make the next action obvious.

## Art direction before code
1. Identify the page's purpose and visitor intent: discover, compare, buy, manage, or get support.
2. Identify the product category, audience, primary action, real assets, and factual content.
3. Choose a coherent visual direction that fits SKINFA's established identity. Do not select a trendy style just because it is fashionable.
4. Define hierarchy, grid, typography, palette, image treatment, spacing rhythm, component language, and motion before implementation.
5. Make the page feel specific to SKINFA. Avoid repeated generic hero + three cards + gradient + floating blobs patterns.

## Visual standards
- Use a consistent grid and align major content edges. Keep spacing, type scale, radii, borders, and button treatments systematic.
- Give each section a clear job and a distinct composition; avoid repeating the same card grid down the whole page.
- Use typography with character and a clear hierarchy. Keep Persian typography readable and correct in RTL.
- Use a restrained palette with intentional contrast. Preserve current SKINFA brand colors and decisions unless the user requests a change.
- Prefer real product photography and truthful product UI. Never invent product features, prices, reviews, ratings, stock, customer logos, or testimonials.
- Do not use generic stock imagery as if it were the actual product. If a placeholder is unavoidable, label it clearly for replacement.
- Use real brand marks/icons when available; do not draw imitations of known logos.
- Avoid decorative gradients, excessive glassmorphism, gratuitous glow, emoji-as-icons, and nested cards without a clear purpose.

## Storefront and product-page rules
- Show the actual product clearly and at a useful scale. Do not bury it inside a small generic card.
- Keep image ratios consistent within a collection and avoid stretching or cropping away important product details.
- Product variants must update the displayed product image and selected state when applicable.
- Make price, availability, options, delivery information, and add-to-cart action easy to find—but show only facts supplied by the product data.
- Use captions or labels when they genuinely help customers understand a product; do not apply a blanket no-caption rule.
- Keep purchase actions prominent, trustworthy, and functional.

## Motion and interaction
- Use motion to explain state, provide feedback, and create a memorable but calm experience.
- Prefer transform and opacity for smooth animation. Use easing and duration consistently.
- Buttons, links, cards, menus, galleries, and dialogs need clear hover, focus, pressed, loading, and disabled states where relevant.
- Avoid scroll-jacking, random motion, gratuitous parallax, auto-advancing content, and animation that delays a task.
- Respect prefers-reduced-motion. Essential content and functionality must remain available without animation.
- Touch and swipe interactions must work on mobile without interfering with normal page scrolling.

## Responsive, accessibility, and performance
- Review at wide desktop, tablet, and narrow mobile widths (including around 390px).
- Check RTL direction, Persian numerals/text wrapping, long product names, safe areas, keyboard behavior, and virtual keyboards.
- Prevent horizontal overflow, clipped controls, overlapping content, and tiny touch targets.
- Use semantic elements, visible focus, meaningful labels, useful alt text, and adequate contrast.
- Optimize image sizes and loading; avoid layout shifts and unnecessary animation work.

## Existing-project redesign protocol
1. Audit the current page before changing it: identify what works, what is weak, and what must not change.
2. Preserve product truth, data flows, navigation, checkout, authentication, and existing working behavior.
3. Prioritize the highest-impact problems: hierarchy, layout, product visibility, typography, consistency, then decorative detail.
4. Make a coherent improvement rather than layering unrelated visual effects onto the old design.
5. Compare the rendered result before and after when browser screenshots are available.
6. Report what changed, what was checked, and what still needs real-device verification.

## SKINFA guardrails
- Treat SKINFA as a distinctive, premium shopping experience, not a generic SaaS dashboard.
- The storefront should feel editorial and product-led; admin tools should remain fast, clear, and operational.
- Keep the established Persian RTL experience and brand identity intact.
- Never alter Supabase, authentication, checkout, inventory, customer records, secrets, or deployment configuration during a visual task unless explicitly requested.
- Never claim browser checks or physical-device testing unless they were actually performed.
