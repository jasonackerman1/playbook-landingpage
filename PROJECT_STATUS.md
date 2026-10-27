# Digital Playbooks Landing Page — Project Status

**Live:** https://jasonackerman1.github.io/playbook-landingpage/ (GitHub Pages, legacy build from `main`)
**Repo:** `jasonackerman1/playbook-landingpage`

## What it is
One landing page ("Sales Enablement Resources") with a card for each Konica Minolta playbook, each linking to its production URL on `wapps.mykonicaminolta.com`. Card order: Accelerate, Salesforce, Healthcare, Public Sector, Legal, GC/IP (Graphic Communication / Industry Print).

## Files
- `index.html`: the main page (dashboard-style header bar, KM Academy logo, card grid).
- `index-styled.html`: a variant styled like konicaminolta.us, in case it's embedded on the intranet.
- Both files are standalone (inline CSS). Change both when a change applies to both.

## Current state (2026-10-27)
- **Feedback & Requests button is ON HOLD (hidden)** on both pages. It's wrapped in an `<!-- ON HOLD -->` comment; remove the wrapper to restore. Its link is still a placeholder (`https://forms.office.com/r/PLACEHOLDER`), and needs a real Microsoft Forms URL before it comes back.

## Next step
- Create the Microsoft Form, swap in its URL, and un-hide the button when ready.
- Decide whether `index-styled.html` gets used for an intranet embed.
