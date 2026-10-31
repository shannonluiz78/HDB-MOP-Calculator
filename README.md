# Home Equity Studio V4.0 — Customer Test Build

**Prepared for Luiz Lee · Huttons · CEA R057632A**

## What's in this build

- `index.html` — simple customer landing page; primary focus is HDB Sell & Upgrade.
- `sell-upgrade.html` — five-step guided journey: HDB Sale → Your Funds → Next Home → Purchase Costs → Results.
- `bto-sbf.html` — separate BTO/SBF information and future-planner page. The full BTO/SBF financial calculator is **not** built in V4.0.
- `assets/home-equity-logo.webp` and `assets/luiz-lee.webp` — approved branding and advisor portrait.
- `robots.txt`, `sitemap.xml` — proposed SEO files for the stated Vercel domain.

## How to test

1. Extract this entire ZIP into one folder. **Keep the `assets/` folder beside the HTML files.**
2. Open `index.html` with Chrome or Edge, then select **Start my Sell & Upgrade plan**. If your browser restricts local files, upload all files to a preview Vercel project first.
3. Change sale price, outstanding loan, CPF refund, available cash/CPF and income. Progress through all five steps.
4. Try Private Property, New EC, and Resale HDB; also test a zero-loan case and an insufficient-funds case.
5. At Results, try **Mobile PDF**, **A4 PDF** and **Send my results** (WhatsApp opens with a message ready for the customer to send).

## Publishing

Upload **all three HTML files, both assets and SEO files** to the root of a GitHub/Vercel static site. Do not upload just `index.html`, or the calculator and branding links will fail. The canonical URLs and sitemap currently reference `https://hdb-mop-calculator.vercel.app/`; change them if publishing to a different permanent domain.

This package does not update the existing live website. Test in a preview deployment before replacing the production site.

## Formula continuity and limitations

The three financial calculation/report scripts from V3.2.2 were carried forward. Their calculation functions, rates and financing logic were preserved. A PDF layout-only improvement increases page height for New EC mobile PDF notes to prevent footer overlap. The guided interface is new.

Input values are retained only in the **browser tab's session storage** to support step navigation and refresh; no backend login or lead database is included. Avoid shared-device use for confidential financial figures. WhatsApp sends no message without the customer pressing Send.

The figures remain indicative and do not establish HDB/HFE eligibility, CPF availability, IRAS reliefs, or mortgage approval. The original assumptions have not been recertified for every possible household and transaction; confirm them against MAS, HDB, CPF and IRAS before relying on a real client case.

## Authoritative references

- MAS macroprudential loan framework: https://www.mas.gov.sg/publications/macroprudential-policies-in-singapore
- HDB housing loan: https://www.hdb.gov.sg/buying-a-flat/flat-grant-and-loan-eligibility/housing-loan/housing-loan-from-hdb
- IRAS BSD: https://www.iras.gov.sg/taxes/stamp-duty/for-property/buying-or-acquiring-property/buyer%27s-stamp-duty-%28bsd%29
- IRAS ABSD: https://www.iras.gov.sg/taxes/stamp-duty/for-property/buying-or-acquiring-property/additional-buyer%27s-stamp-duty-%28absd%29
