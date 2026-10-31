# Home Equity Studio V4.1 — Review QA (31 October 2026)

## Completed
- New homepage based on the approved layout: large symbol-only user logo, real user-supplied smart-casual photo, HDB Sell & Upgrade CTA, separate BTO/SBF card, customer journey cards.
- Advisor section includes name **Luiz Lee**, designation **Associate Senior Marketing Director**, agency **Huttons Asia Pte Ltd**, agent registration **R057632A**, estate agent licence **L3008899K**, WhatsApp Business **+65 8980 9229** and CEA verification link.
- Existing five-step Sell & Upgrade calculation flow retained; main UI restyled and labelled V4.1.
- V4.1 PDF reports include the separate spare CPF OA input in the potential-capital planning total and show actual property-specific CPF available on page two.
- Agent's official portrait now appears on PDF page one. Both A4 and mobile report links work.
- BTO/SBF remains on its separate **information only** page, not a functioning calculator.
- Privacy and disclaimer page added, along with robots.txt and sitemap.xml.

## Browser checks
Headless Chromium (rendered in-memory because the environment restricts navigation to local file URLs):

| Test | Result |
|---|---|
| Homepage at 320 / 390 / 768 / 1024 / 1440 px | Pass, no horizontal overflow, local images load |
| Calculator five-step navigation | Pass |
| Default estimated HDB sale cash / potential capital | S$298,970 / S$508,970 |
| Additional cash S$200,000 and spare CPF OA S$230,000 | Potential capital becomes S$938,970 |
| Private property loan / EC loan tests | S$1,125,000 / S$987,708 under illustrative assumptions |
| Resale HDB no-loan scenario | S$0 loan and cash-gap warning |
| PDF download | Pass: two-page A4 and two-page mobile PDFs |
| Page 2 CPF detail | Actual CPF used by scenario reported separately from planning capital |
| Mobile results overflow | Pass after removing oversized decorative pseudo element |
| BTO/SBF / Privacy pages (390 / 768 / 1440 px) | Pass, no horizontal overflow |
| Browser JavaScript errors | None observed |

## Important caveats
- Live Vercel deployment and Safari on an actual iPhone/iPad are **not tested**. Review the site on the final hosted URL before publishing broadly.
- The PDFs are image-backed and are not text-searchable; they contain clickable WhatsApp links. A tagged, accessible text PDF may be added in a future version.
- Potential total capital includes estimated CPF refund and separately entered existing CPF OA **before** property-specific CPF usage restrictions. Page two estimates a capped usable amount for the selected purchase. Neither is confirmed CPF approval.
- All loans, MSR, TDSR, LTV, duties, HFE and EC eligibility are indicative. Bank/HDB/CPF/IRAS and legal verification is still required.
- BTO/SBF property photos are illustrative concept artwork, not specific developments.
- Confirm CEA Public Register information and agency marketing approval before production publication. Current phone details were supplied by the user and have not been independently matched to the user's registration record in this build.
