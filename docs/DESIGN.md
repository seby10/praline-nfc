# Part 3 — Visual & UI/UX design

## Direction: "Basalt & Praline"

The obvious move for a coffee brief is cream paper, a high-contrast serif and a
terracotta accent. Every AI-generated café page on the internet looks like that,
and so do half the real ones.

Baños de Agua Santa is not that place. It's a town wedged in a green Andean
gorge under an active volcano — black basalt, cloud forest, waterfalls, thermal
water steaming out of dark rock after sundown. And *praline* is caramelised
sugar and hazelnut: amber, glossy, confectionery.

So the page is **dark-first and volcanic**, with caramel as the only bright
thing on it. It also happens to be the correct functional call — the card gets
tapped over a candlelit table far more often than in direct sun, and a dark page
is easier on the eyes and on an OLED battery at 9pm.

## Colour

| Token | Dark (primary) | Light | Role |
|---|---|---|---|
| `--ground` | `#16130F` | `#E7E8E0` | Basalt / pale mineral stone. Both are hue-biased, never neutral grey. |
| `--raised` | `#201B16` | `#F1F1EA` | The review band and social tiles lift off the ground. |
| `--ink` | `#EDE4D6` | `#16130F` | Steam over hot water. |
| `--ink-soft` | `#9A8C78` | `#5C564C` | Warm taupe — a grey biased toward the amber, so it reads as chosen. |
| `--amber` | `#D99A4E` | `#A9682A` | **Praline.** The one bold move. Darkened for the light theme so it holds contrast on stone. |
| `--verde` | `#7E9A76` | `#3F5A3C` | Cloud-forest green. Used once, for the live *Open now* dot. |

Boldness is spent entirely on the amber. Everything around it stays quiet.

## Typography

**Gloock** (display) — a contemporary high-contrast serif with heavy, glossy
stems. It reads *confectionery* rather than *artisanal bakery*, which ties the
type directly to the café's name. Uncommon enough that the page won't look like
every other landing page.

**Archivo** (body, UI, prices) — a warm grotesque with proper Spanish
diacritics (á, é, ñ all sit correctly, which Inter handles blandly) and real
tabular figures, so the price column lines up.

Two families only — every extra font is another round-trip on 4G.

- Wordmark: Gloock, `clamp(3.6rem, 19vw, 5.6rem)`, line-height `.86`
- `COFFEE HOUSE`: Gloock, `.34em` tracking, amber — set as a rule, not a word
- Labels: Archivo 600, 11px, `.18em` tracking, uppercase
- Prices: Archivo 600, `tabular-nums`, amber

## Layout

A single column of full-bleed **bands** separated by amber hairlines — the strata
of a menu board, or of the gorge. Left-aligned throughout, not centred.

Buttons have a **2px radius and a hard 2px border**: an enamel table sign, not a
soft app pill. That one detail does more to break the templated look than any
colour choice.

```
┌─────────────────────────────┐
│ ⊙ seal                ES|EN │   language, always reachable
│                             │
│  P r a l i n e              │   Gloock, huge, hero as thesis
│  ──────────────────────     │   the amber rule
│  C O F F E E   H O U S E    │
│  Baños de Agua Santa        │
├─────────────────────────────┤
│ EMPIEZA AQUÍ                │
│ ▐ Ver la carta          → ▌ │   amber fill — the primary act
│ ▐ Escríbenos WhatsApp   → ▌ │   carries the table number
├─────────────────────────────┤
│ ★★★★★                       │   raised band — visually distinct
│ ¿Te gustó tu café?          │
│ ▐ Dejar una reseña      → ▌ │   third thing seen, never a popup
├─────────────────────────────┤
│ SÍGUENOS                    │
│ [ IG ]  [ TT ]  [ FB ]      │
├─────────────────────────────┤
│ VISÍTANOS                   │
│ ◷ Horario      ● Abierto    │   live, computed in café time
│ ◉ Dirección     CÓMO LLEGAR │
│ ≋ Wi-Fi              COPIAR │   tap to copy — the real hook
├─────────────────────────────┤
│ MESA 07     HECHO EN BAÑOS  │
└─────────────────────────────┘
```

**Order is an argument.** Menu first because it's what they came for. Review
third because asking before you've delivered is rude. Wi-Fi last because it's
the thing people hunt for — and hunting drags them past the review CTA.

## Motion

One orchestrated load, then nothing. The amber rule **pours** left-to-right
under the wordmark (620ms) while the bands rise behind it on a 60–80ms stagger.
Scattered hover effects and scroll animations are what make a page feel
generated; a single well-timed entrance feels designed. Fully disabled under
`prefers-reduced-motion`.

## Copy

Written into the page, in both languages. The review ask is the part that
matters:

> **¿Te gustó tu café?**
> Somos una cafetería pequeña en Baños. Una reseña tuya en Google ayuda a que
> otros viajeros nos encuentren — toma 20 segundos.

Three things are doing work there: *pequeña* (small businesses get more
goodwill), *otros viajeros* (Baños runs on tourism — the reader recognises
themselves), and *20 segundos* (naming the cost defuses the objection). The
button says **"Se abre directo en Google"** so nobody worries about where the
tap leads.

Every button says what happens. "Ver la carta", then a menu. "Copiar", then
*Contraseña copiada*.

## The physical card

**Size** — 85 × 55 mm, standard credit-card format. Big enough for a scannable
QR, small enough to sit in a table caddy next to the sugar without becoming
clutter.

**Material** — matte black PVC, 0.76 mm, with the amber printed as a **spot
gloss or gold foil** on the wordmark and the rule. Matte-plus-gloss is the
cheapest available luxury signal, and it survives spilled milk. Avoid paper
laminate — it delaminates in a humid town, and Baños is humid.

**Round the corners** (3 mm). Sharp-cornered PVC cards chip and then look cheap.

**Front:**

```
        ⊙                     seal, foil
     Praline                  Gloock, foil
   ─────────────              the amber rule, foil
   COFFEE HOUSE
   ── ── ── ── ──
   ⌇ Toca con tu teléfono
     Tap your phone here      + small NFC wave mark
```

**Back:** the QR code (min 25 mm square, high contrast — black on white, *not*
amber on black, which fails on older camera apps), the printed domain
`praline.cafe` in Archivo, and the table number set large in Gloock. The table
number has to be readable by staff across the room, so it doubles as table
signage.

**Mounting** — self-adhesive dot in a wooden or brass caddy, angled ~30°. Do not
lay it flat on the table: a flat card gets used as a coaster, and a coaster gets
wet.

**Non-negotiable:** if the tabletops are metal, order ferrite-backed tags and
test one on an actual table before committing to the run.
