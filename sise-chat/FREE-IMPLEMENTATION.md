# SISE chat — free implementation track

This track uses the existing GitHub feature branch and current Supabase project only.
It does not create a Supabase development branch, a new project, or any paid resource.

## Safety boundary
- Work stays on `feature/sise-chat-luxury`; `master` and `backup/sise-chat-original` are not modified.
- No production SQL is executed by this work.
- No Render deployment or merge is performed.
- The existing public-chat message table and its token-validated edit/delete RPCs remain the source of truth.
- Do not weaken the existing `chat_edit` / `chat_delete` token checks.

## Already prepared
- Luxury glass styling is scoped to the public chat and mirrored in the admin page.
- Existing message, image, sticker, reply, edit, and delete flows are preserved.
- This draft adds a proposed schema for persistent reactions and read receipts:
  `migrations/20261119_chat_features_draft.sql`.

## Important database note
The SQL draft is deliberately not applied. It creates reaction/read tables with RLS enabled and no browser-access policies. This is a safe default: the browser cannot access these tables until token-validated RPCs and matching policies have been reviewed and added.

## Free implementation sequence
1. Finish the front-end presentation on the feature branch and validate mobile/desktop markup.
2. Add client-side Realtime Presence/Broadcast integration using the existing Supabase Realtime service, with polling fallback. Presence should not be stored as permanent rows.
3. Add server-side RPCs for reactions and read receipts. Validate the caller's existing chat identity/token hash before allowing writes; never trust a client-supplied `uid` alone.
4. Test against a local/mock fixture or a separately approved environment. Do not test schema changes against production.
5. Only after explicit approval, prepare a production migration and deployment plan.

## What "free" means here
No new paid infrastructure is provisioned. Existing GitHub and hosting plan limits still apply. Realtime and database usage remain subject to the current Supabase project's included quotas; this work does not assume unlimited usage.
