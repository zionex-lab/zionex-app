# zionex.app — Zionex umbrella page (Phase 1)

Single static file: `index.html`. No build step, no dependencies.
Fonts come from Google Fonts; everything else is inline.

## Before going live

1. ~~**Waitlist endpoint**~~ — done. Web3Forms key is set in `ACCESS_KEY`, submissions
   arrive at `hello@zionex.app`; verified end-to-end from a browser.
   Web3Forms free tier: **250 submissions/month**, and it rejects server-side POSTs —
   the form only works from a real page, which is also why `curl` cannot smoke-test it.
2. ~~**Email address**~~ — done. `hello@zionex.app` is live: Cloudflare Email Routing
   forwards it to a personal Gmail, Brevo relays outgoing replies. Full runbook lives in
   the memzix repo: `docs/devops/email-zionex-app.md`.
3. **The four ideas** — still placeholders, and this is the one that matters.
   The `<article class="unit">` blocks in `#bench` were built from the "close to money"
   list (invoicing, leads, payments) + email order intake. Swap in your real ones;
   keep it at 3–4. Until then the page collects signal about problems you may not
   intend to build, which is worse than collecting nothing.

## Spam handling

Each form carries a hidden `botcheck` checkbox (`.hp`, positioned off-screen and
`aria-hidden`). Web3Forms drops any submission where it is non-empty; the client-side
handler also bails out early. Do not remove it or rename the field — the name is what
Web3Forms matches on.

## Status chips

Each card carries a status chip in its header. The colour comes from `data-s` on `.chip`:

| `data-s`      | chip           |
|---------------|----------------|
| `validating`  | lime green     |
| `in-design`   | orange         |
| *(omitted)*   | grey — used for "Exploring" |

## Look

Light, single-theme on purpose: white ground, sky-blue glossy buttons, rounded boxes,
Nunito for headings + Source Sans 3 for text. No dark-mode variant — the palette is
painted explicitly so it holds up anywhere.

## Deploy

Any static host. Drop the folder in:

    npx serve .                      # local preview
    # Cloudflare Pages / Netlify / Vercel: point at this dir, no build command
    # nginx: root /path/to/zionex.app;

## Phase 2 (later)

When 1–2 pilots land, replace the `.unit` blocks with real cases carrying numbers
("invoice processing 6 h/week → 20 min"), each linking to its subdomain. Same markup,
same layout — no rebuild needed.
# zionex-app
