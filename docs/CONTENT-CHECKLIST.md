# What I still need from Praline

Everything below is a placeholder in `index.html`. Nothing else is blocking.

| # | Item | Where it goes | How to get it |
|---|------|---------------|---------------|
| 1 | **The real menu** | `CONFIG.menu` | Export the Canva menu as PDF or send the text. I need item name + price, and which items you want described. English names optional — I'll translate. |
| 2 | **Google Place ID** | `CONFIG.review` | [Place ID Finder](https://developers.google.com/maps/documentation/places/web-service/place-id) — search the café, copy the `ChIJ…` string. Or in Google Business Profile: *Ask for reviews* → copy the `g.page/r/…/review` link and use that instead. |
| 3 | **WhatsApp number** | `CONFIG.whatsapp` | Country code + number, digits only: `593` + number without the leading 0. |
| 4 | **Street address** | `CONFIG.address` | Exact, as printed on the door. |
| 5 | **Opening hours** | `CONFIG.hours` + `hoursLabel` | Both need updating — one drives the live *Open now* dot, one is the text people read. |
| 6 | **Wi-Fi password** | `CONFIG.wifi` | Set to `""` to hide the row. |
| 7 | **TikTok / Facebook** | `CONFIG.tiktok`, `CONFIG.facebook` | Delete the line if the account doesn't exist — the tile disappears on its own. |
| 8 | **Logo** | the `.seal` SVG in the hero | An SVG is ideal. PNG with transparency works. Right now it's a placeholder monogram. |
| 9 | **Domain** | Cloudflare | Something short and typeable — it gets printed on the card as the QR fallback. |
| 10 | **Table count** | — | How many tags to buy and number. |

Nice to have: 2–3 photos of the interior (for the Open Graph share image), and
confirmation of whether prices include the 15% IVA + 10% service.
