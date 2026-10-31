# Home Equity Studio V4.1 — Review & Deployment

## Contents
- `index.html` — selected V4.1 visual homepage with user-approved casual portrait and symbol-only logo.
- `sell-upgrade.html` — 5-step HDB Sell & Upgrade calculator based on V4.0/V3.2.2.
- `bto-sbf.html` — separate BTO/SBF guide; no live BTO financial calculator is represented as complete.
- `privacy.html` — customer-facing disclaimer / data-flow explanation.
- `assets/` — the logo symbol, user photos, illustrative housing visuals and styling.
- `robots.txt`, `sitemap.xml` — search engine discovery documents for the intended production host.

## Test locally
Extract the ZIP, preserve folder structure, then open `index.html` in a browser. For the most reliable navigation and asset loading, serve the folder using an ordinary static file server (e.g. local development server). The app requires no backend for calculator/PDF generation.

## Publish
Upload all files and the `assets/` directory to your hosting project. Preview before replacing your live `hdb-mop-calculator.vercel.app` site. Review CEA registrations and confirm the advertised phone number matches the CEA Public Register.

## Financial methodology
Existing HDB sale and purchase-feasibility formulas are retained from the current calculator; the V4.1 changes focus on UI, explanatory labels, PDF branding and agent information. Capital summary includes *entered* spare CPF OA as a **potential** resource; specific housing purchase CPF restrictions are modelled separately in the next-home feasibility section. Do not treat total potential capital as an approved CPF withdrawal amount.

## Limitations
- No bank/HFE approval or guarantee; legal, CPF and agency review required.
- BTO/SBF page is explanatory, not a working construction timeline calculator.
- WhatsApp messages are drafted but require customer confirmation to send.
- The photographic property images are illustrative; they do not depict specific marketed developments.
