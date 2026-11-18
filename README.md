# HiddenGem Flow — Website

Live site: https://hiddengemflow.vercel.app/

The public website for **HiddenGem Flow**, the all-in-one Chrome extension
(draggable floating window, daily task websites, userscript manager, and
official Script Store). Local-first, no signup.

Live extension release: https://github.com/BidyutRoy2/hiddengem-flow/releases/tag/v3.0.0

## What is in this repo

- `index.html` — the whole site in one file. No build step,
  no backend, no framework. Open it in a browser and it works.
- `favicon.png` — the tab icon. `social-preview.png` — the 1200×630
  preview image used by the Open Graph / Twitter cards.
- `sitemap.xml` — the single-URL sitemap. `robots.txt` — allows all
  crawling and points at the sitemap.

## How Download works

Every Download button links straight to the extension zip on GitHub
Releases, so a click starts the download and the visitor stays on the site.

At runtime the page fetches the latest release from the public GitHub API
(`https://api.github.com/repos/BidyutRoy2/hiddengem-flow/releases/latest`)
and switches all Download links to that release's `.zip` asset
(the one named `hiddengem-flow-v*.zip`). If that lookup fails, the buttons keep
their fallback: the v3.0.0 asset
(`https://github.com/BidyutRoy2/hiddengem-flow/releases/download/v3.0.0/hiddengem-flow-v3.0.0-20261118.zip`).
GitHub serves release assets as `attachment`, so the click downloads the zip
directly.

## Deploy on Vercel

1. Import this repo as a new Vercel project.
2. Framework preset: none (static site). Build command: none. Output
   directory: the repo root (where `index.html` lives).
3. Free Hobby plan, `.vercel.app` subdomain. No environment variables needed.

The runtime dependencies outside this file are Google Fonts
(Outfit, IBM Plex Mono, Inter), loaded from Google's CDN with system-font
fallbacks; the GitHub releases API
(`https://api.github.com/repos/BidyutRoy2/hiddengem-flow/releases/latest`),
fetched at runtime to point the Download buttons at the latest release;
and the store index
(`https://raw.githubusercontent.com/BidyutRoy2/hiddengem-flow-store/main/index.json`),
fetched at runtime to render the Script Store cards (the hardcoded cards
in `index.html` stay as the fallback if that fetch fails).
Everything else — markup, styles, scripts, icons — is inline in
`index.html`.
