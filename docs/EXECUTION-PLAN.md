# Part 2 — Execution plan

Ten steps, roughly a week of calendar time, most of it waiting on printing.

## 1. Domain and hosting (30 min)

Buy a short domain — `praline.cafe`, `pralinebanos.com`. It gets printed on the
card next to the QR, so it must be typeable by someone whose phone has no NFC.

Cloudflare Pages → Connect to Git → this repo. Build command empty, output
directory `/`. Add the custom domain. HTTPS is automatic and mandatory.

## 2. Fill in the content (30 min)

Everything from `docs/CONTENT-CHECKLIST.md` into the `CONFIG` block in
`index.html`. Commit. The site is live.

## 3. Set up the redirect layer (15 min) — do not skip

Do **not** point the tags at `praline.cafe/?t=07` directly either. Point them at
a path you can re-route:

```
praline.cafe/t/07   →  301  →  praline.cafe/?t=07
```

In Cloudflare: Rules → Redirect Rules → wildcard `praline.cafe/t/*` to
`praline.cafe/?t=$1`. If the café ever rebrands, changes platform, or wants the
tags to point at a seasonal promo for one month, that's a one-line change
instead of re-encoding and re-laminating twenty locked cards.

## 4. Buy hardware

- **NTAG215** stickers or cards (504 bytes — far more than a URL needs, but the
  headroom is worth the ~2¢). NTAG213 works fine if that's what's available.
- **On-metal / ferrite-backed** versions *only if the tabletops are metal*.
  Test one tag on an actual table before ordering twenty.
- Buy 25% more than you have tables. Some will fail, some will be stolen.

## 5. Encode the tags (5 min for the first, 30 sec each after)

Use **NFC Tools** (free, iOS + Android) or **NXP TagWriter** (Android).

1. *Write* → *Add a record* → **URL/URI** — this record type and no other.
   Never "Launch app", never a custom MIME type; those break on iOS.
2. Type the full URL including `https://`: `https://praline.cafe/t/07`
   (the writer stores `https://` as a 1-byte prefix code, so the URL costs
   almost nothing).
3. Write. **Test it on both an iPhone and an Android before locking.**
4. *Other* → **Make read-only**.

> **Locking is permanent.** A locked tag can never be rewritten. Verify the URL
> resolves correctly on two phones first. This is exactly why step 3 exists —
> lock the tags, keep the flexibility in the redirect.

Number the physical cards to match: table 07 gets `/t/07`.

## 6. Design and print the card

Spec in `docs/DESIGN.md`. Print the **QR code on the same card** — it's not a
fallback, roughly a third of taps will be QR scans.

## 7. QA before deployment

Test on, at minimum:

- an iPhone 12+ (background read → banner → tap)
- an older iPhone (Control Center NFC reader)
- a mid-range Android
- **a phone with no NFC** — the QR must work standing at the table
- a browser set to English (the page must open in English, not Spanish)
- a phone in airplane mode → 4G only, no Wi-Fi, and time the load

Check the *Open now* dot at 7am and at 11pm.

## 8. Brief the staff (15 min)

The highest-leverage step, and the one everyone skips. Staff should say, when
dropping the bill: *"If you enjoyed it, there's a card on the table — one tap
and you can leave us a review."* A card nobody mentions gets tapped maybe 5% as
often as a card the staff points at.

## 9. Instrument it

Turn on **Cloudflare Web Analytics** (free, cookieless, no consent banner
needed) or Plausible. Add the one-line snippet before `</body>`.

The page already fires named events through `track()` — they'll flow to
Plausible, GA4 or GTM automatically if any of those is present, and no-op
otherwise:

| Event | Question it answers |
|---|---|
| `page_view` (+ `table`) | Are the cards being tapped? Which tables? |
| `menu_open` | Is the menu the reason people tap? |
| `review_click` | The number that matters. |
| `whatsapp_click` | Is table-service-by-WhatsApp real demand? |
| `wifi_copy` | Wi-Fi is the hook — this proves it. |
| `social:instagram` | Follower growth attribution. |
| `lang_switch` | What share of customers are foreign? Informs the printed menu too. |

## 10. Measure the only metric that counts

Write down the **Google review count and average rating today, before the cards
go out.** Check weekly. Reviews-per-week before vs. after is the whole business
case; `review_click` only tells you how many people started.

A realistic target for a busy café: **2–5 additional reviews per week**, from
roughly 1 review per 10–15 review-CTA clicks. If `review_click` is healthy but
review count isn't moving, the Place ID is wrong — verify the link opens the
write-a-review box directly and not the café's profile page.

## Ongoing

Menu price change = edit `CONFIG.menu`, commit, live in 20 seconds. The tags are
never touched again.
