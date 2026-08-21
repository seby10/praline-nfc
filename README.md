# PRALINÉ coffee house — NFC table system

A single self-contained landing page that opens when a customer taps the NFC
card on their table. Full 70-item menu, socials, Google review CTA,
WhatsApp-from-your-table, Wi-Fi password — bilingual ES/EN, ~36 KB, no build
step, no dependencies.

Palette and typography follow the Manual de Identidad Corporativa; the three
greens are retired at the owner's direction. See `docs/DESIGN.md`.

```
index.html   the entire site (HTML + CSS + JS + icons inlined)
docs/        strategy, execution plan, design spec, content checklist
```

## Change anything

Open `index.html` and find the block marked **EDIT EVERYTHING IN THIS BLOCK**.
Links, hours, Wi-Fi password and all 70 menu items live there as plain text.
Save, push, done — Cloudflare rebuilds in ~20 seconds.

Each menu item is `{ es, en, p, n }` — Spanish name, English name, price, and an
optional description. A category can carry a `note` for an upsell strip.

Every value written `‹REEMPLAZAR›` is a placeholder that still needs the real
one. See `docs/CONTENT-CHECKLIST.md`.

## Deploy

```
Cloudflare Pages → Connect to Git → this repo
  Build command:    (leave empty)
  Output directory: /
```
Then add the domain (e.g. `praline.cafe`) and turn on **Web Analytics**.

## Table numbers

The tag on table 7 encodes `https://praline.cafe/t/07`. The page reads `t` and:

- pre-fills the WhatsApp message with *"I'm at table 07"*
- stamps the table on the footer chip
- attaches the table to every analytics event, so you can see which tables
  actually get tapped

Tags are identical apart from that one number.

## Local preview

```
python3 -m http.server 8000
```
