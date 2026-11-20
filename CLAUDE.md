# punklotus.com: site build

This is Punk Lotus's own website, moving off Squarespace. Copy and voice rules live in the hub at `Projects/PUNK LOTUS/BRAND/` (Language Guide + Foundations), so read those before writing new copy.

- **Stack:** Astro (static output), deployed by Netlify from GitHub `kt-netizen/punklotus-site` (private). Node is installed locally at `~/.local/node/bin` (not system-wide), so use `export PATH=~/.local/node/bin:$PATH` first.
- **Run:** `npm run build` then `npx astro preview` (localhost:4321).
- **Pages:** `src/pages/*.astro`. Shared header, footer, SEO meta and schema are in `src/layouts/Base.astro`. Forms use Netlify Forms (`src/components/ContactForm.astro`) and land on `/thanks`.
- **Redirects:** `netlify.toml`. Keep every old Squarespace URL working (`/home` → `/`).
- **`_source/`** (gitignored) holds the Squarespace originals scraped 2026-11-20: page HTML, extracted copy, images.
- **Live-site fonts, as found:** Climate Crisis (headings), Droid Sans Mono (body; replaced here by Noto Sans Mono, its successor), Archivo (UI). Kirsty thinks Climate Crisis is hard to read, so a type rethink is pending.

## Switch-over checklist (not done yet)
1. Netlify: connect the repo, confirm the preview, and set up form notifications to kt@punklotus.com.
2. DNS: copy **every** record from Squarespace DNS (the Google Workspace MX `smtp.google.com` and the google-site-verification TXT), then point the domain at Netlify. Add SPF/DKIM/DMARC.
3. After going live: resubmit the sitemap in Google Search Console, then cancel the Squarespace plan. Don't cancel before DNS is confirmed working.
