# Pittsburgh Event Space — standalone site

Static site (no build step) targeting the **"Pittsburgh event space"** keyword cluster. Built in the POB Big Brand look (Anton / Martian Mono / Caveat · ink / fuchsia / teal / pink). Content and pricing sourced from the live `/pages/event-space` page; photos are live Cloudinary URLs (cloud `dcprxs9do`) already used in POB marketing.

## Deploy (Vercel)
1. New Vercel project → root directory = `event-space-site/` → deploy (it's plain HTML, zero config; `vercel.json` handles clean URLs).
2. Point the domain. Canonicals/sitemap/OG currently assume **`https://www.pittsburgheventhub.com`** — if the real domain differs, find-and-replace that string across this folder (11 files).
3. Submit `sitemap.xml` in Google Search Console.

## Shopify cleanup (after the new site is LIVE)
- Import `shopify-redirects.csv` in Shopify admin → Navigation → URL redirects, **then** unpublish these blog posts (redirects transfer the Google value; deleting without them 404s rankings away):
  - `/blogs/articles/10-best-event-venues-in-pittsburgh-in-2025`
  - `/blogs/articles/rooftops-in-pittsburgh-to-hold-your-next-event`
  - `/blogs/articles/best-event-spaces-for-small-parties-in-pittsburgh`
  - `/blogs/articles/bridal-shower-event-spaces-in-pittsburgh`
  - `/blogs/news/top-baby-shower-venues-in-pittsburgh-by-region-and-budge`
  - `/blogs/articles/the-best-wedding-venues-in-pittsburgh-pa`
  - `/blogs/articles/which-balloon-decor-ideas-are-perfect-for-event-spaces`
  - `/blogs/articles/the-creative-space-in-pittsburgh-where-event-businesses-actually-grow`
  - `/blogs/articles/discover-the-ultimate-event-space-in-pittsburgh-party-on-butler`
- Optional: also redirect `/pages/event-space` + `/pages/event-space-form` (rows included in the CSV) once the new site fully replaces them. Keeping the Shopify page live *and* the new site both targeting the same keyword = cannibalization, which is the current problem.
- Leave `/blogs/articles/the-pittsburgh-party-store-that-knows-your-vibe-before-you-do` on Shopify — it's a store/balloon post, not an event-space post.

## Booking form
The book section embeds the existing GHL "Get a Quote" survey (`W2bJprgLCnw7SujP8SE6`) — the same one used across partyonbutler.com, so leads flow into GHL exactly like today. Follow-up (nice-to-have): replace with a custom form posting to the `ghl-create-contact` Supabase edge function with `form_type: "Event Space Form"` and a new `source` (e.g. `pittsburgh-event-space-site`) for per-site attribution.

## Photos
Gallery/hero use the verified marketing Cloudinary shots (001099, 001185, 000931, 005502, 005471, IMG_4284, IMG_4234, the bubble-tower event shot) + product photos. To swap in dedicated venue photos later: upload to Cloudinary and replace URLs in `index.html` (hero + `.rail-track`) — each image appears in one obvious place.
