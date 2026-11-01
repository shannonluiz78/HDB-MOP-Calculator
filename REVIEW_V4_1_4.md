# Home Equity Studio V4.1.4 — Change & Independent Regression Review

**Date:** 1 November 2026 (Singapore)  
**Baseline:** Approved V4.1.3 landing page + existing calculator. Live Vercel website was **not changed**.  
**Approval status:** Test build, **not** a loan, CPF or HDB eligibility certification.

## Fixed this round

| Finding | Previous effect | V4.1.4 correction | Verification |
|---|---|---|---|
| F01 — Invalid/blank commission | Invalid nonnumeric commission could be normalised to an empty number input, then treated as zero, overstating net sale cash and permitting export | Required financial entries must be explicit numeric values; blank or malformed inputs show `CHECK INPUT` and block result exports. Deliberate `0` remains valid | `seller_bad_commission`, blank/zero tests, PDF/WA invalid-input tests |
| F02 — Outdated WhatsApp version | Text said `V4.1.2` | Updated to `V4.1.4` with current result figures and agent contact | Supplementary WhatsApp capture |
| F03 — Pending-sale funding ambiguity | Potential after-sale capital could resemble money available today | Separate **Potential after HDB sale** from **cash spendable for selected timing after reserve**. Sale-pending cash/CPF refund excluded from current purchase. Both timing and cash now appear in page-one PDF and WhatsApp | Pending-sale and completed-sale edge tests, PDF render |
| F04 — Eligibility warning ranked below cash gap | A customer could see “cash gap” rather than the more consequential unresolved EC/HDB/CPF status | `ELIGIBILITY MUST BE CONFIRMED` takes precedence when eligibility is unresolved; the estimated numerical cash gap is still displayed separately | Foreign HDB + EC income ceiling tests; PDF and WA labels |
| F05 — Stale funding in side panel | Invalid inputs could leave prior spendable funds visible | Invalid calculation clears side-panel funding and timing labels | Invalid seller and purchase-input browser checks |

## Independent tests

- **82** recreated scenario assertions: **82 PASS**, **0 FAIL**, **0 ERROR**.
- **12** original supplemental tests: **12 PASS**, **0 FAIL**.
- **12** new focused edge cases & screen-width checks: **12 PASS**.
- **5** image/PDF functional checks with actual bundled images: **5 PASS**.
- All numeric outputs across the **81 originally passing scenarios** matched the prior version's published independent audit for checked fields. The previously invalid-commission case correctly produces no valid result, rather than generating misleading figures.
- A4 and mobile **two-page PDFs** generated in headless Chromium with bundled logo and agent portrait successfully loaded.
- Five-step navigation and no horizontal overflow at **320/390/768/1024/1448** viewport widths passed in Chromium. No hosted Vercel or native iPhone Safari test was performed.

## Cases to review next (do NOT automatically claim verified eligibility)

1. **CPF funds**: At age 55+, refunds may first replenish the RA. Exact property CPF usage can depend on buyer ages, remaining lease, outstanding ownership, prior withdrawals and valuation; see CPF's [Housing Usage Calculator](https://www.cpf.gov.sg/member/tools-and-services/calculators/cpf-housing-usage). The current model labels unverified CPF as conditional and sometimes excludes it conservatively.
2. **Mixed or joint purchasers / ABSD**: IRAS offers specific HDB/new EC remission on HDB approval, but a single buyer profile cannot establish every joint-ownership circumstance. [Official remission source](https://www.iras.gov.sg/taxes/stamp-duty/for-property/appeals-refunds-reliefs-and-remissions/common-stamp-duty-remissions-and-reliefs-for-property/Acquisition-of-HDB-Flats-and-new-Executive-Condominium-%28EC%29-Units).
3. **HFE, HDB loans and housing grants**: Actual amounts and conditions come from a valid HFE letter; 3.0% HDB assessment vs 2.6% concessionary repayment illustration must not be treated as loan approval. [HDB financing](https://www.hdb.gov.sg/buying-a-flat/financial-planning-for-a-flat-purchase/credit-to-finance-a-flat-purchase).
4. **Second HDB loan**: CPF refunds, cash proceeds, timing and prior subsidised housing can change eligible loan amounts.
5. **Full cashflow and transaction timing**: Some duties and bridging needs are conditional; the current potential-capital headline is **not** cash actually accessible before the sale.
6. **BTO/SBF planner**: Still informational and not a functioning BTO/SBF calculator.
7. **Accessibility / crawlability**: Approved desktop landing page is built from image artwork with clickable regions. Retain until a separate semantic redesign is approved.

## Deployment and confidence boundaries

- Keep the fixed **V4.1.3 homepage** unchanged. Only `sell-upgrade.html` and version wording on `bto-sbf.html`/`privacy.html` were changed.
- The calculator is still an **illustrative financial planning tool**, not a property eligibility assessment.
- Test the entire ZIP on a **separate Vercel preview** and an actual iPhone/iPad before production; do not replace the live website automatically.
- The 82 scenario inputs were reconstructed from a user-supplied test matrix; passing each assertion is narrower than official financial eligibility clearance.
