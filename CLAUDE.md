# Nacho Website

Static site for a friend group. Hosted on GitHub Pages. No build step — all files served as-is.

## Structure
- `index.html` — Nacho's birthday page (Three.js bg, GSAP animations, confetti)
- `tippingpayouts/index.html` — AFL footy tipping pot calculator with live GCQF stock price
- `tippingpayouts/price.json` — auto-updated by CI: `{"price": 4.12, "updated": "2026-03-25T..."}`
- `tippingpayouts/payouts.xml` — payout tier config (Capitalist/Socialist modes)
- `christmas/index.html` — Christmas page
- `CommissionersCup/index.html` — Golf tournament page
- `.github/workflows/fetch-price.yml` — fetches GCQF.AX hourly via yfinance, commits + deploys
- `.github/workflows/deploy.yml` — deploys to GitHub Pages on push to main

## Tipping payouts key values
```js
STARTING_AUD = 1400   // total pot collected
UNITS_GCQF   = 341    // units of GCQF.AX held
BUY_PRICE    = 3.96   // purchase price per unit (AUD)
ROLLING_POT  = 95.90  // current weekly rolling bet total
```
14 participants. Weekly rolling bet: Sedy won, Mosh won, rest pending.

## Workflows
- `fetch-price.yml`: runs hourly (cron `0 23 * * 0-4` + `0 0-5 * * 1-5`) during ASX hours (10am–4pm Melbourne). Uses yfinance + Python heredoc. Always commits price.json then deploys Pages in same job.
- `deploy.yml`: triggered by push to main (not by workflow commits — GitHub limitation).

## Patterns
- All pages are single self-contained HTML files (inline CSS + JS, no framework)
- Git root is `nachodog/` — always `cd nachodog/` before git commands
- Remote: `https://github.com/Herschy24/nachodog.git`, branch `main`
- Workflow-pushed commits use `[skip ci]` to avoid triggering deploy.yml (deploy happens inline in fetch-price.yml instead)
