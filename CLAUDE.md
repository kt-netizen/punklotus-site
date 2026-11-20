# punklotus.com: site build

This is Punk Lotus's own website, moving off Squarespace. Copy and voice rules live in the hub at `Projects/PUNK LOTUS/BRAND/` (Language Guide + Foundations), so read those before writing new copy.

- **Stack:** Astro (static output), deployed by Netlify from GitHub `kt-netizen/punklotus-site` (private). Node is installed locally at `~/.local/node/bin` (not system-wide), so use `export PATH=~/.local/node/bin:$PATH` first.
- **Run:** `npm run build` then `npx astro preview` (localhost:4321).
- **Pages:** `src/pages/*.astro`. Shared header, footer, SEO meta and schema are in `src/layouts/Base.astro`. Forms use Netlify Forms (`src/components/ContactForm.astro`) and land on `/thanks`.
- **Redirects:** `netlify.toml`. Keep every old Squarespace URL working (`/home` → `/`).
- **`_source/`** (gitignored) holds the Squarespace originals scraped 2026-11-20: page HTML, extracted copy, images.
- **Live-site fonts, as found:** Climate Crisis (headings), Droid Sans Mono (body; replaced here by Noto Sans Mono, its successor), Archivo (UI). Kirsty thinks Climate Crisis is hard to read, so a type rethink is pending.

## Live (since 20 Nov 2026)
- **DNS lives at GoDaddy** (nameservers ns55/ns56.domaincontrol.com). Squarespace DNS couldn't hand over to Netlify DNS because both use NS1.
- **Records:** A @ 75.2.60.5 (Netlify), CNAME www → punklotus.netlify.app, MX @ 1 smtp.google.com (Google Workspace), TXT google-site-verification, TXT SPF `v=spf1 include:_spf.google.com ~all`, TXT _dmarc `v=DMARC1; p=none;`.
- **Primary domain is `punklotus.com` (no www).** www 301s to it, and the canonical, sitemap and schema all use non-www.
- **Netlify visitor access** is set to "Previews only": production is public, deploy previews are private. Forms are enabled and tested.
- **Pushing to `main` deploys live.** Check the preview locally first.

## Still to do
1. Resubmit the sitemap in Google Search Console (`https://punklotus.com/sitemap-index.xml`).
2. Cancel the Squarespace site plan about a week after go-live (~27 Nov), once everything is confirmed.
3. DKIM in Google Workspace, then tighten DMARC (see `00-hq/open-loop.md`).
4. Gut-Check page + payment, FAQ page, Kirsty's drawings + handwriting font, and a voice check on the new copy lines.
