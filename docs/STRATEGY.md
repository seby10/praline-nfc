# Part 1 — Strategic analysis

## The actual problem

The café isn't asking for a link page. It's asking to convert a moment of
*idleness* — the two minutes between ordering and the coffee arriving — into
three business outcomes: a Google review, a follow, and a customer who knows
what else is on the menu. The table card is the only advertising channel where
the customer is already seated, already happy, and has nothing else to do.

That framing changes the design. A generic Linktree optimises for "here are all
our links." This page optimises for **one review per ten taps**.

## UX goals

**For the customer** — the tap must pay off in under a second, and every answer
they might want must be reachable without pinch-zooming: what's on the menu,
what's the Wi-Fi password, how do I call someone over, where's the bathroom-adjacent
practical stuff. Wi-Fi is the sleeper feature: it's the single most common reason
a customer would *voluntarily* tap a card on a table, and it drags them past the
review CTA on the way.

**For the owner** — zero recurring cost, zero technical maintenance, prices
editable in under a minute, and honest numbers about whether the thing works.
Critically: **the tags must never need re-encoding**. Once 20 cards are printed,
laminated and locked, going back to them is a project.

**Tension to resolve:** the review ask and the customer's goal are not the same.
Asking for a review before they've been served is worthless and slightly rude.
So the review CTA sits *below* the primary actions — visible on first scroll,
never a popup, never an interstitial. It earns the click by being the third
thing you see, not the first.

## Technical requirements and pitfalls

**iOS never auto-opens a URL.** iPhone XS and later (iOS 14+) read tags in the
background, but only while unlocked, and they show a *notification banner the
user must tap*. iPhone 7/8/X require opening the NFC reader in Control Center
first. There is always one extra tap. Design the card copy for that.

**A meaningful share of Android phones in Ecuador have no NFC hardware.** Budget
Motorola/Samsung A-series and most Chinese imports below ~$200 ship without it.

⇒ **The QR code is not a backup. It is a co-primary path.** Both go on the card.

**Metal tables detune NFC.** A standard PET tag laid on a steel or aluminium
tabletop will read weakly or not at all. If the tables are metal, the tags must
be ferrite-backed ("on-metal" tags). Wooden tables — no problem.

**An unlocked public tag is a security hole.** Anyone with a phone and a free app
can rewrite an unlocked tag to point at a phishing page, and it will still look
like the café's card. Every tag must be locked read-only after writing. This is
irreversible, so it has to be right the first time.

**Other traps:** tags stacked in a drawer read as garbage; steam and spilled
milk kill unlaminated paper tags; `http://` URLs trigger browser warnings —
always `https://`; app-specific NDEF record types (Launch App, Android
Application Record) break on iOS entirely.

## Stack recommendation

**Custom static HTML on Cloudflare Pages, behind a domain the café owns.**

| Option | Verdict |
|---|---|
| **Linktree / Beacons** | No. ~$5–10/mo to remove their branding, still can't match the café's identity, ships hundreds of KB of JS, no ES/EN toggle, no table numbers, and the analytics belong to Linktree. A menu inside a Linktree is a list of ugly buttons. |
| **Canva website** | No — for the *web* menu. Canva sites are image-heavy (frequently 1–3 MB), render as scaled-down desktop layouts on phones, and can't be instrumented. Keep Canva for the **printed** menu; it's good at that. |
| **PDF menu** | No. A PDF on a phone means pinch, zoom, drag. It's the most common mistake cafés make. |
| **Custom static HTML** | **Yes.** ~30 KB, one file, no dependencies, no build step, loads in well under a second on 4G, free forever, and the café owns the domain and the numbers. |

Two decisions do most of the work:

1. **The tag encodes a URL the café controls** (`praline.cafe/?t=07`), never a
   Linktree/Instagram URL directly. The destination can be redirected forever
   without touching a single locked tag. This is what makes it a system rather
   than a gimmick.
2. **The menu is native HTML, not an embedded PDF or Canva frame.** It's the
   most-used feature; it should be the fastest thing on the page.
