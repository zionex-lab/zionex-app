# zionex.app — Zionex umbrella page (Phase 1)

Single static file: `index.html`. No build step, no dependencies.
Fonts come from Google Fonts; everything else is inline.

## Before going live — 3 things to fill in

1. **Waitlist endpoint** — `index.html`, in the `<script>` at the bottom:
   - Web3Forms: create a key at https://web3forms.com, paste into `ACCESS_KEY`.
   - Formspree: set `ENDPOINT = "https://formspree.io/f/xxxxxxx"` and leave `ACCESS_KEY` unused.
   Until a key is set, the forms show *"Waitlist not connected yet"* rather than faking success.
2. **Email address** — `hello@zionex.app` appears 3x (contact card, footer, error message).
3. **The four ideas** — the `<article class="unit">` blocks in `#bench`. These are placeholders
   built from the "close to money" list (invoicing, leads, payments) + email order intake.
   Swap in your real ones; keep it at 3–4.

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
