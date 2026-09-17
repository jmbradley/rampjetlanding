# rampjet.ai

A single holding page. No nav, no other routes.

- `index.html` — the page (self-contained CSS; Google Fonts for Instrument Serif and JetBrains Mono)
- `mark.png` — the flywheel mark, used as both the hero graphic and the brand icon
- `og-image.png` — share card, rendered from the page at 1200x630
- `favicon.svg`, `apple-touch-icon.png`
- `CNAME` — rampjet.ai on GitHub Pages; **a push to `main` is a production deploy**

The full Ramp/Jet site (Reach, Run, Insights, Advisors) moved to
**reworkbyrampjet.com** — repo `Ramp-Jet/reworkbyrampjet` — in Sept 2026.
Old rampjet.ai paths are not redirected, with one exception: the advisor PDF
(`/advisors/rampjet-advisor-one-pager.pdf`), which gets forwarded by email and so
outlives the site that hosted it. That path is a directory holding a redirect
stub -- a file there would be served as application/pdf and never render.

There is deliberately no contact email on this page yet.
