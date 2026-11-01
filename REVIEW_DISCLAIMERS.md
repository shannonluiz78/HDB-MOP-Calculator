# Home Equity Studio V4.1.4 — Contextual Disclaimer Enhancement

**Build:** V4.1.4 Disclaimer Update (review/test package)  
**Date:** 1 November 2026  
**Scope:** Customer wording, contextual warnings, PDF/WhatsApp disclosures. **No change to formulas or financing logic.**

## Changes

1. **Step 1: HDB sale** — Contextual notice that the estimated CPF refund due is not necessarily the amount reusable after completion. A conditional warning is displayed for buyers aged 55+ because CPF refunds may replenish the Retirement Account first.
2. **Step 2: Funds and borrowing** — CPF OA currently available is explicitly distinguished from expected sale refunds. Link to CPF Board's Housing Usage Calculator. The 55+ warning appears only when the buyer's entered age is 55 or older.
3. **Step 3: Next home** — Context notes for ABSD citizenship/remissions, HDB grants/HFE amounts, remaining-lease CPF restrictions, and New EC eligibility. Links to HDB/IRAS/CPF official guidance where useful.
4. **Step 4: Timing** — Notice appears if the user selects a pending sale and explains that expected cash/CPF refunds are not currently available.
5. **Step 5: Results** — General disclaimer plus property-type-specific notices, estimated loan/CPF warnings, and conditional age-55/pending-sale notices. A S$0 funding gap must not be mistaken for purchase or loan approval.
6. **PDFs** — Both A4 and mobile PDFs now show condensed, scenario-specific cautions without adding new pages. The previous report formatting and downloadable output are retained.
7. **WhatsApp** — Generated messages carry relevant age-55, pending-sale, CPF use, HDB or New EC caution statements, in addition to existing assumptions and figures.
8. **Privacy page** — Clarifies that a zero estimated funding gap is not confirmed affordability or eligibility.

## Evidence and QA

- **82/82** independently reconstructed financial scenario checks passed in Chromium against the updated HTML. These are test assertions, *not* certification of every underlying regulatory eligibility condition.
- **24/24** additional checks passed covering conditional notices, results page, A4 and mobile PDF generation, WhatsApp wording, JS errors and page behaviour at 320/390/768/1024/1448 pixel viewports. The browser reports some layout scrollWidth bookkeeping, but independent tests confirmed `scrollX=0` on attempted horizontal navigation at all tested widths.
- The `compute()` and `show()` financial scenario logic blocks were compared directly with the source V4.1.4 and confirmed unchanged.
- PDFs generated as two pages each. PDF pages rendered visually and examined for significant overlaps/truncation.

## Remaining boundaries

These disclaimers **do not correct an inaccurate calculation** or prove eligibility. They do not replace verifying actual CPF amounts, loan approval, HFE eligibility, IRAS remissions, ownership status and transaction timing. For real client use, obtain official documents and professional confirmation.

The **BTO/SBF page remains informational only** and was not converted into a calculation module. The live Vercel site has not been updated.

## Official verification links

- CPF Housing Usage Calculator: https://www.cpf.gov.sg/member/tools-and-services/calculators/cpf-housing-usage
- CPF refunds at age 55+: https://ask.gov.sg/cpf/questions/cmlft9uxq002mx4vp5ddp4zky
- HDB Flat and Grant Eligibility: https://www.hdb.gov.sg/buying-a-flat/flat-grant-and-loan-eligibility
- IRAS ABSD remission conditions for HDB/new EC: https://www.iras.gov.sg/taxes/stamp-duty/for-property/appeals-refunds-reliefs-and-remissions/common-stamp-duty-remissions-and-reliefs-for-property/Acquisition-of-HDB-Flats-and-new-Executive-Condominium-%28EC%29-Units
