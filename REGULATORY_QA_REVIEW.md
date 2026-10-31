# Home Equity Studio V4.1.2 — Regulatory and Functional Review

**Review date:** 31 October 2026. **Deployment:** review build only; production has not been changed.

## What was checked

The user-supplied `MOP Calculator expanded-test-matrix.md` (77 cases reported from an independently executed Node harness) and `MOP calculator fix-spec.md` were examined. Those documents contain a test report and a proposed correction specification, **not the original test runner, raw JSON output, or 77-case executable fixture**. The 77 scenarios have **not** been independently re-executed in full here.

I verified the material policy points against the official HDB, CPF, IRAS and MAS web pages on 31 October 2026; then built and browser-tested the changes below.

## Confirmed fixes incorporated in V4.1.2

1. **Homepage card alignment:** corrected the absolute-positioned desktop link targets and removed mismatched hover outlines. The approved Singapore skyline artwork and its images remain unchanged. Desktop and mobile destinations tested.
2. **Seller input validation:** rejects nonnumeric/negative sale price, loan balance, CPF refund, commission, legal costs, income, debt, extra cash and CPF input. Rejects commissions >10% instead of silently accepting impossible figures; clears current displayed results on invalid input and prevents PDF/WhatsApp from exporting stale results.
3. **Shortfall and CPF handling:** negative net sale cash is shown explicitly as an estimated sale shortfall. When sale proceeds cannot cover the required CPF refund, no *unverified* refund is included in next-home funding. For buyers 55+, anticipated sale CPF refund is also withheld from the modelled purchase funding until the OA amount is verified after possible RA allocation. Existing OA entered separately remains a *potential* source.
4. **HDB-specific ABSD treatment:** for an HDB acquisition assumed approved by HDB, Singapore Citizen acquirer/joint acquirer -> full remission; Singapore PR-only acquirer(s) -> 5% payable as applicable under IRAS remission conditions. Unverified HDB buyer eligibility remains a review requirement. Do **not** apply this HDB special treatment to private residential purchases.
5. **EC citizenship contradictions:** an SC profile conflicting with 'No SC household' now blocks the purchase output instead of automatically granting remission. A joint SC assumption requires confirmation.
6. **HDB-loan assessment:** uses at least **3.0%** to estimate loan eligibility, and keeps **2.6%** as the Oct–Dec 2026 concessionary repayment illustration. Actual HFE financing is authoritative.
7. **Income ceiling labels:** S$16,000 for families and S$24,000 aggregate for extended families under applicable current HDB loan rules, plus S$8,000 eligible singles. Extended-family per-nucleus rules require HFE confirmation. Earlier/unknown HFE policy has a dedicated 'review required' option. New EC already retains the S$16k/S$18k project-cohort selector.
8. **Stamp duty precision:** taxable BSD and ABSD are floored to whole Singapore dollars with a S$1 applicable minimum. A zero statutory duty remains zero. Verified against edge cases and the S$1.5m baseline.
9. **CPF lease limits:** for a resale HDB with a lease of 20 years or less, CPF use is zero. If lease does not cover youngest buyer to age 95, *unverified CPF usage is excluded* and the case is flagged. HDB loan is held at zero without a confirmed HFE amount in the latter case. This is conservative, not a substitute for the CPF Housing Usage Calculator.
10. **Baseline purchase quantum:** illustrative funding upper bound is capped by a hypothetical 25% downpayment condition, not simply equity + TDSR loan. The display explicitly says this is not an approved affordability ceiling, and directs customers to the individual purchase check for LTV, duty, cash and CPF rules.
11. **Reports:** PDFs display a `REVIEW REQUIRED · FUNDING UNCONFIRMED` warning when appropriate, even if arithmetic shows S$0 additional cash required. Contact and disclaimers retained.

## Independent tests performed on this build

- **25 browser-based focused assertions:** 25 passed, 0 failed (including negative inputs, sale baseline/break-even, BSD/ABSD edge cases, HDB SC/SPR remission, HDB lease/CPF controls, income ceilings, New EC citizenship and income-cohort cases).
- **13 scenario browser checks:** baseline, negative loan/income, sale deficit, age 55+, HDB SC/PR purchase, HDB loan 3% assessment, HDB S$15k household, short-lease HDB, EC contradiction, EC income and zero-loan HDB; all completed without JavaScript page errors. Several scenarios deliberately return `CHECK INPUT`, `ESTIMATED CASH GAP` or `ELIGIBILITY REVIEW` as designed.
- **Homepage alignment tests:** desktop 1448/1280, responsive 1024/768/390/320; no horizontal overflow or JavaScript page errors. Click targets checked at desktop card centres.
- **PDF downloads:** A4 and mobile PDF download actions each produced valid **two-page PDFs** in Chromium and were rendered for visual inspection.
- **Unverified in this review:** 77-case third-party test suite as a whole, real iPhone Safari, a live Vercel hosted build, independent HDB/CPF/IRAS case-by-case underwriting, full accessibility and performance audits.

## Remaining limitations before public production

- **Joint buyers, citizenship, HFE eligibility, grants, and ABSD remissions** are not fully determined by the current simplified form. HDB/IRAS decisions prevail. HDB routes intentionally show `ELIGIBILITY REVIEW` even when the numerical cash gap is zero.
- **Private-property CPF limit:** no complete age/lease/property-holding test exists for all owners. The displayed CPF allocation is a *potential upper bound*, not confirmed usable CPF; cases relying on CPF show `ELIGIBILITY REVIEW` until personally verified. For users age 55+, estimated sale refunds are excluded until the OA-available portion is confirmed.
- **Short-lease HDB:** because the actual CPF and HDB LTV proration cannot be safely computed without official inputs, this version excludes unverified CPF and will not assume a positive HDB housing loan without an HFE amount.
- **Sale shortfall:** requires loan redemption, market-value sale status and CPF refund reconciliation; this form does not certify that a seller has to top up cash or the precise CPF refund credited.
- **Stamp duty on HDB/EC:** the special HDB remission assumptions are conditional on HDB-approved acquisition. Mixed ownership and nationality require case review.
- **Concessionary housing loan:** loan tenure and recognised income can differ by actual applicants and HFE. Commission and bank treatment are indicative only.
- **Site implementation:** the desktop landing page is intentionally image-backed to match the approved visual. Important text inside the artwork is not individually accessible/SEO-editable; consider rebuilding it semantically before final public production.
- **BTO/SBF:** informational planning page only, not yet an active BTO or SBF mortgage/timeline calculator.

## Verified official sources

- IRAS HDB and new-EC ABSD remissions: https://www.iras.gov.sg/taxes/stamp-duty/for-property/appeals-refunds-reliefs-and-remissions/common-stamp-duty-remissions-and-reliefs-for-property/Acquisition-of-HDB-Flats-and-new-Executive-Condominium-(EC)-Units
- IRAS ABSD rates, rounding and minimum: https://www.iras.gov.sg/taxes/stamp-duty/for-property/buying-or-acquiring-property/additional-buyer%27s-stamp-duty-%28absd%29
- IRAS BSD rates, rounding and minimum: https://www.iras.gov.sg/taxes/stamp-duty/for-property/buying-or-acquiring-property/buyer%27s-stamp-duty-%28bsd%29
- HDB Credit to Finance a Flat Purchase (3% HDB assessment floor; 30% MSR; 75% LTV): https://www.hdb.gov.sg/buying-a-flat/financial-planning-for-a-flat-purchase/credit-to-finance-a-flat-purchase
- HDB Housing Loan from HDB (S$16k/S$24k/S$8k caps; second-loan conditions): https://www.hdb.gov.sg/buying-a-flat/flat-grant-and-loan-eligibility/housing-loan/housing-loan-from-hdb
- HDB HDB loan interest (Oct–Dec 2026 2.6%): https://www.hdb.gov.sg/managing-my-home/finances/loan-matters/interest-rate
- HDB New EC eligibility (S$16k/S$18k cohort rules): https://www.hdb.gov.sg/buying-a-flat/executive-condominiums/eligibility
- CPF lease and age-95 restrictions: https://www.cpf.gov.sg/service/article/how-much-cpf-savings-can-i-use-to-buy-a-property-if-its-lease-does-not-cover-the-youngest-buyer-to-age-95
- CPF refunds and RA/OA age 55+: https://www.cpf.gov.sg/service/article/when-i-sell-my-existing-property-what-can-i-do-with-the-sale-proceeds-that-are-refunded-to-my-cpf-accounts
- MAS macroprudential restrictions: https://www.mas.gov.sg/publications/macroprudential-policies-in-singapore

**Recommendation:** Treat this as a safer **V4.1.2 review candidate**, not an approved financial advice/eligibility engine. Review representative real HFE/CPF/IRAS cases before production.
