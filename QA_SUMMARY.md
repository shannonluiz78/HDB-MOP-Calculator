# V4.0 Test Summary · 28 October 2026

| Area | Test | Result |
|---|---|---|
| UI | 5 steps progress and back/next navigation | PASS (Chromium) |
| UI | 320, 390, 768, 1024, 1440 px widths | PASS — no horizontal overflow |
| HDB sale | Default 850k price / 320k loan / 210k CPF | S$298,970 estimated net cash |
| HDB sale | Changed sale price to S$950k | S$396,790 estimated net cash |
| CPF/Cash | Extra cash and spare CPF OA inputs | PASS — flows to purchase engine |
| Private Property | Baseline purchase-feasibility case | PASS |
| New EC | 30% MSR scenario | PASS |
| Resale HDB | No loan, income S$0 and 0-year tenure | PASS — completes wizard |
| Insufficient funds | High purchase price / lower income | PASS — cash gap flagged |
| PDF | A4 report | PASS — 2 pages |
| PDF | Mobile report | PASS — 2 pages; New EC notes/footer spacing corrected |
| WhatsApp | Customer results CTA retained | URL construction in source verified; live app handoff not independently tested |
| SEO | Single canonical per page; sitemap/robots present | PASS — static inspection |
| BTO/SBF | Dedicated information page | PASS — informational only |

**Test method:** Headless Chromium in-memory page tests. Local file and localhost navigation were blocked in the browser-testing environment, so a separately deployed preview URL and real iPhone Safari require customer-side confirmation.

**Formula continuity:** Original calculator script SHA-256 unchanged; purchase-feasibility script SHA-256 unchanged. PDF script modified only in report formatting, not financial formulas.

**Warnings:** Financial estimates are not formal eligibility determinations. New EC, HDB resale, CPF limits and stamp-duty exceptions require case-by-case verification.
