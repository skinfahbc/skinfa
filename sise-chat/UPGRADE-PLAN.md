# SISE CHAT — Luxury Glass Upgrade

## Safety and branch policy
- Original snapshot: `backup/sise-chat-original` (do not edit).
- Active implementation branch: `feature/sise-chat-luxury`.
- Do not merge to `master`, deploy, or change the production Supabase project without explicit approval.

## Current implementation discovered
The public chat is embedded in the single-page `index.html` and duplicated in `admin.html`. It already supports:
- Supabase-backed public messages
- image upload and preview
- stickers
- reply-to-message
- edit and delete for authorized messages
- periodic polling (currently about every 4 seconds)

The current message schema has `reply_to`, `rname`, and `rtext`, but no persistent reaction, read receipt, or presence/typing records.

## Upgrade direction
Visual identity: restrained luxury glass — warm ivory, champagne gold, translucent surfaces, subtle borders, soft shadows, compact mobile-first spacing. Avoid oversized headers, heavy gradients, or decorative stars unrelated to the action.

## Implementation phases
1. **Visual layer** — apply scoped styles to public chat in both storefront and admin HTML; preserve all other site components.
2. **Message interactions** — persistent emoji reactions, copy, message action menu, forwarding, pinning, and report flow. Keep edit/delete/reply permissions server-enforced.
3. **Live state** — online presence, typing indicator, read receipts, and live message delivery using Supabase Realtime rather than 4-second polling.
4. **Conversation tools** — message search, unread count, jump-to-latest, notification preferences, and attachment handling.
5. **Admin experience** — unified inbox, unread/priority filters, customer/order context, canned replies, assign/close/reopen, and response metrics.
6. **Private + AI conversations** — keep public, manager-private, and AI channels visually consistent but data-isolated; product cards and order tracking should use existing SISE data safely.
7. **Verification** — test mobile/desktop, light/dark themes, guest/member/admin permissions, upload limits, reconnect behavior, and accessibility.

## Backend prerequisites
Before enabling database-backed features, create an isolated Supabase development branch and apply reviewed migrations there. Do not run schema changes against production as part of this work. The current Supabase project is live and must remain untouched until the user explicitly approves a production rollout.

## Current commit scope
Only the scoped CSS layer for `.ch`, `.ch-hd`, `.ch-list`, `.chm`, and `.ch-cp` has been added so far. No database schema, customer data, production settings, or deployment has been changed.
