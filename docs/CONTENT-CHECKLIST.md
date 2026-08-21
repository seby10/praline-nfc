# What's still outstanding

**Received:** menu (70 items, transcribed), brand manual (palette + type applied),
Instagram, Google Maps link. Prices confirmed IVA-inclusive from the menu itself.

## Blocking — the page ships without these but they're placeholders

| # | Item | Where | How to get it |
|---|------|-------|---------------|
| 1 | **Google Place ID** | `CONFIG.review` | [Place ID Finder](https://developers.google.com/maps/documentation/places/web-service/place-id). Or in Google Business Profile → *Ask for reviews* → copy the `g.page/r/…/review` link and paste that instead. **This is the whole point of the project — without it the review button goes nowhere.** |
| 2 | **WhatsApp number** | `CONFIG.whatsapp` | `593` + number without the leading 0, digits only. |
| 3 | **Street address** | `CONFIG.address` | As printed on the door. |
| 4 | **Real opening hours** | `CONFIG.hours` + `hoursLabel` | Both: one drives the live *Open now* dot, one is the text people read. |
| 5 | **Domain** | Cloudflare | Short and typeable — it gets printed next to the QR. |

## Needs a decision

| # | Question | Why it matters |
|---|---|---|
| 6 | **Ambato or Baños de Agua Santa?** | The brand manual says *"reconocida en Ambato"* twice; you said Baños. I've set `CONFIG.city` to Baños — confirm, or tell me if there are two locations (in which case the tags can point each café at its own city line). |
| 7 | **Le Jour Serif licensing** | The manual labels it *Personal Use Only*. See `docs/DESIGN.md` — this affects print and packaging, not just the website. |
| 8 | **Wi-Fi password** | `CONFIG.wifi`. Currently hidden. It's the single strongest reason a customer taps the card voluntarily — worth including. |
| 9 | **Which items are the favourites?** | The menu marks favourites with a ♥ that didn't survive the PDF. Tell me which and I'll flag them. |
| 10 | **TikTok / Facebook** | Currently hidden. Add the URL and the tile appears on its own. |

## Assets

| # | Item | Why |
|---|---|---|
| 11 | **Logo as SVG** | Prata approximates the wordmark but can't reproduce the R–A swash. One-line swap. |
| 12 | **The four brand icons** | The manual defines CAFE / BRUNCH / PASTELES / GALLETAS but the files aren't in the PDF. They'd make good menu category marks. |
| 13 | **2–3 interior photos** | For the link-preview image when someone shares the page. |

## One thing worth flagging about the menu PDF

The images in it still carry **Canva watermarks**. If that file goes to a
printer, the watermarks print. Re-export it from a Canva Pro account, or
replace the stock images, before any physical run.
