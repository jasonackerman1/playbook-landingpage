# Digital Playbooks Landing Page — Project Status

**Live:** https://jasonackerman1.github.io/playbook-landingpage/ (GitHub Pages, legacy build from `main`)
**Repo:** `jasonackerman1/playbook-landingpage`

## What it is
One landing page ("Sales Enablement Resources") with a card for each Konica Minolta playbook, each linking to its production URL on `wapps.mykonicaminolta.com`. Card order: Accelerate, Salesforce, Healthcare, Public Sector, Legal, GC/IP (Graphic Communication / Industry Print). **GC/IP card hidden 2026-11-18** (content out of date) inside an `<!-- ON HOLD -->` comment on both pages; remove the wrapper to restore.

## Files
- `index.html`: the main page (dashboard-style header bar, KM Academy logo, card grid).
- `index-styled.html`: a variant styled like konicaminolta.us, in case it's embedded on the intranet.
- Both files are standalone (inline CSS). Change both when a change applies to both.

## Current state (2026-10-27)
- **Feedback & Requests button is ON HOLD (hidden)** on both pages. It's wrapped in an `<!-- ON HOLD -->` comment; remove the wrapper to restore. Its link is still a placeholder (`https://forms.office.com/r/PLACEHOLDER`), and needs a real Microsoft Forms URL before it comes back.

## Welcome line + French (2026-11-17)
- Both pages read IT's UserInfo API (`/sc/UserInfo/`, same as the Accelerate playbook) with inline code, no extra files.
- Everyone: "Welcome, First Last". On `index-styled.html` it's right-aligned above the third card; on `index.html`, the right side of the header.
- Canadian employee (`BCA-C`) whose preferred language is French: French loading screen, then the page translates to French (Canada) with Google Translate. Everyone else stays in English.
- Only works on the KM server under `/sc/playbooks`. Preview anywhere with `?mock=us`, `?mock=ca-en` or `?mock=ca-fr`.
- Switches `WELCOME` / `FRENCH` in the script at the bottom of each page.
- Google translates "Playbook" as "guide pratique"; it can be protected with `notranslate` if wanted.
- Tested live on GitHub Pages 2026-11-17 with `?mock=ca-fr` and `?mock=us`: works. A first test seemed broken only because the browser was showing its saved copy of the old page (GitHub Pages lets browsers reuse a page for 10 minutes); a refresh or private window fixes that.

## Google Analytics + GC/IP hidden (2026-11-18)
- **GC/IP card hidden** (content out of date) in an `<!-- ON HOLD -->` comment on both pages; remove the wrapper to restore. The grid now shows 5 cards (3 + 2 on wide screens).
- **GA4 tag** in `<head>` of both pages: measurement ID `G-7807ESGLX6` (standard gtag.js, sends page views on its own). Jason first sent a Tag Manager snippet (`GTM-5ZBMPCZP`); it was swapped for the plain GA4 tag so visits aren't counted twice.
- **Playbook click tracking:** each card has a unique `id` (`pb-accelerate`, `pb-salesforce`, `pb-healthcare`, `pb-public-sector`, `pb-legal`, `pb-gcip`) and a `data-playbook` name. A script before `</body>` sends a `playbook_click` event with `playbook_name` + `link_url` on every card click. New card = add both attributes, no GA setup needed.
- **GA setup done by Jason:** one event-scoped custom dimension named **Playbooks**, parameter `playbook_name` (one dimension covers every playbook).
- **Where to read it:** Reports → Engagement → Events → `playbook_click` (break down by Playbooks), or Explore → Free form (rows Playbooks, value Event count, filter Event name = `playbook_click`). Realtime shows clicks within a minute; standard reports take 24–48 hours.

## Next step
- FTP `index-styled.html` to the KM server, click a card, and confirm `playbook_click` shows in GA Realtime.
- FTP `index-styled.html` to the KM server and check the welcome line logged in.
- Create the Microsoft Form, swap in its URL, and un-hide the button when ready.
- Decide whether `index-styled.html` gets used for an intranet embed.
