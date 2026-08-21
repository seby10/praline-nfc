# Part 3 — Visual & UI/UX design

Rebuilt from the *Manual de Identidad Corporativa* and the menu PDF. The
earlier proposal was invented in the absence of brand material; the manual
supersedes it. Where the two disagreed, the manual won.

## What the manual specifies

| | Manual | On the page |
|---|---|---|
| Wordmark | `PRALINÉ` (accented) over `coffee house`, centred lockup | Reproduced as a centred lockup |
| Display face | **Le Jour Serif** — *"Personal Use Only"* | **Prata** (see licensing note) |
| Secondary face | **EngraversGothic BT** | **Julius Sans One** for the same engraved-caps role |
| Colour | 7 swatches, 3 of them green | 4 kept, 3 greens retired at your direction |

### ⚠ The display face is not licensed for commercial use

The manual's own typography page labels Le Jour Serif **"Personal Use Only."**
That covers the logo, the menu, packaging and signage — not just the website.
Either buy a commercial licence for it, or treat the current logo as a
raster/vector asset that stays as-is and use a licensed face for everything
set in type. This is worth resolving before anything else goes to print.

## Colour

Green is retired per your instruction. It survives in exactly one place — the
live *Open now* dot — where green means "open", not "brand". Everything else
runs on chocolate, cream and the manual's dusty rose, which is also what the
menu PDF already uses for its banner accents.

| Token | Light | Dark | Source |
|---|---|---|---|
| `--ground` | `#EFE3D6` | `#2A1A14` | Manual cream; dark is that cream's chocolate inverse |
| `--raised` | `#F7F0E7` | `#38241C` | derived lift |
| `--ink` | `#5A3A2E` | `#EFE3D6` | **Manual chocolate** — 7.9:1 on the manual's cream |
| `--muted` | `#7A6154` | `#B49C8C` | derived, 4.6:1 |
| `--accent` | `#8A5754` | `#C9938F` | manual rose, adjusted to 4.7:1 so it can carry text |
| `--accent-soft` | `#A27572` | `#A27572` | **Manual rose exactly as published** — rules, fills, stars |
| `--sand` | `#E9D8D2` | `#4A2F2C` | replaces the manual's green `#DCDCCA` |

Two notes on how the palette is actually used. The manual's rose at `#A27572`
is only 3.2:1 on cream — fine for a rule or a star, unreadable as body text —
so text-bearing rose is darkened to `#8A5754` while every decorative use keeps
the published value. And the primary button is filled **chocolate, not rose**:
cream on rose fails contrast, cream on chocolate clears it at 7.9:1.

**Retired:** `#A9B5A2`, `#A8A898`, `#565243`, `#DCDCCA`.

## Typography

Neither manual face is available for web licensing, so both are matched:

- **Prata** replaces **Le Jour Serif** — a didone with the same vertical stress
  and fine hairlines. Set against the real logo it is close enough that the
  wordmark reads as the brand rather than as a substitute.
- **Julius Sans One** replaces **EngraversGothic BT** — thin, wide, caps-only.
  It does the manual's engraved-caps job for labels, eyebrows and menu
  categories.
- **Jost** carries body copy, item names and prices. The manual sets its body
  text in EngraversGothic caps, which is unreadable at 16px on a phone; Jost is
  a geometric sans in the same family as the lowercase `coffee house` in the
  logo, so the voice carries without the legibility cost.

The engraved caps at `.2em` tracking are what make the page look like *this*
brand rather than a generic café template. They appear on every label, every
menu category and every button sub-line.

> Swap the real logo in by replacing the `.wordmark` / `.lockup-sub` block with
> the exported SVG. Prata approximates the R–A swash but cannot reproduce it.

## Layout

Centred hero — mirroring the manual's centred lockup — then left-aligned bands
below, because running text and price lists are read, not admired. Bands are
divided by hairlines; buttons are 1px-bordered with a 3px radius, soft enough
for a patisserie and still not a generic app pill.

```
┌─────────────────────────────┐
│                       ES|EN │
│         P R A L I N É       │   Prata, centred lockup
│        coffee house         │   Jost 300
│         ───────────         │   rose rule, draws on load
│   BAÑOS DE AGUA SANTA       │   engraved caps
│  Los días empiezan y        │   their own tagline, from the menu
│   terminan en Praliné.      │
├─────────────────────────────┤
│ EMPIEZA AQUÍ                │
│ ▐ Ver la carta          → ▌ │   chocolate fill
│ ▐ Escríbenos WhatsApp   → ▌ │   carries the table number
├─────────────────────────────┤
│ ★★★★★                       │
│ ¿Te llevas un buen recuerdo?│
│ ▐ Dejar una reseña      → ▌ │
├─────────────────────────────┤
│ SÍGUENOS      [ Instagram ] │
├─────────────────────────────┤
│ VISÍTANOS                   │
│ ◷ Horario      ● Abierto    │
│ ◉ Dónde estamos CÓMO LLEGAR │
├─────────────────────────────┤
│ MESA 07  REPOSTERÍA ARTESANAL│
└─────────────────────────────┘
```

**The menu** is 70 items across 10 categories, in a full-screen sheet with a
scrolling category bar that tracks your position. Items with a description get
the description; simple price lists get classic dotted leaders. Four categories
carry an upsell strip in rose-tinted sand — the $0.75 syrups, the $0.75 ice
cream, the house wine — because those are pure margin and they are currently
buried in the printed menu.

## Motion

The rose rule draws outward from the centre under the wordmark while the bands
rise behind it on a 60ms stagger. Once, on load, then nothing. Disabled under
`prefers-reduced-motion`.

## Copy

The tagline is theirs, lifted off the menu's last page: *"Los días empiezan y
terminan en Praliné."* The review ask leans on the manual's own positioning —
the brand says it *"no vende postres, construye recuerdos"*, so the ask is
framed as a memory, not a rating:

> **¿Te llevas un buen recuerdo?**
> Somos un proyecto pequeño y cada reseña cuenta. Si te gustó, cuéntalo en
> Google — son 20 segundos y nos ayuda muchísimo.

## The physical card

85 × 55 mm PVC, 0.76 mm, rounded 3 mm corners. **Cream `#EFE3D6` stock with the
wordmark and rule in chocolate**, and the rose as a spot gloss or foil on the
rule alone — one metallic element, not three. Matte body, gloss accent.

Avoid paper laminate: it delaminates in a humid climate.

**Front:** the lockup, the rule, and `Toca con tu teléfono / Tap your phone`
in engraved caps with a small NFC wave mark.
**Back:** QR at ≥25 mm in **plain black on white** (rose-on-cream fails older
camera apps), the printed domain, and the table number set large in Prata so it
doubles as table signage.

**Mount it angled ~30° in a caddy.** A card lying flat becomes a coaster.

If the tabletops are metal, order ferrite-backed tags and test one on a real
table before committing to the run.
