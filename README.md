# Individual Credit Analysis Dashboard

A browser-based tool that analyses an individual loan applicant and suggests whether to approve, reduce or decline the loan.

**Live demo:** https://YOUR-USERNAME.github.io/credit-analysis-dashboard/

## What it analyses
- Credit score, late payments, card utilisation, recent enquiries, past defaults
- Age, employment type, years in current job, sector outlook, income
- Existing EMIs, proposed EMI, FOIR, residual income, savings cover
- The 5 Cs of credit: Character, Capacity, Capital, Collateral, Conditions
- Stress tests: rate rise, income fall, job loss
- Suggested analyst actions, grouped as High, Medium and Low priority
- One-page A4 credit appraisal report with Print and Save as PDF
- Smart Loan Improvement Advisor: ranks the borrower’s own weaknesses (FOIR, existing EMIs, LTV, savings, repayment history, card use, tenure, interest cost) and explains the why, benefit and action for each. Updates instantly and shows only relevant suggestions; healthy borrowers see what is working in their favour.

## Smart Bank Policy Search
Enter any bank name and a loan type. The dashboard sends a POST request with `bankName`, `loanType` and `loanAmount` (JSON) to the Cloudflare Worker and shows interest rates, fees, loan limits, tenure, minimum credit score, income and age criteria, eligibility text and source links. Official bank domains are listed first, conflicting or missing values are flagged, and nothing is applied to the calculations until you review and confirm each change. Applied limits can be reset in one click.

The loan amount also matches the retrieved rate tiers and checks your loan against the bank’s limits. The Worker must allow the page’s origin with CORS (`Access-Control-Allow-Origin`) and answer `OPTIONS` preflight requests.

## How to use
Open `index.html` in any browser, or visit the live demo. Enter the applicant details on the left. The decision, risk score, ratios and reasons update as you type. Three sample profiles are available at the top.

## Scoring model
| C | Weight |
|---|---|
| Character | 30% |
| Capacity | 30% |
| Capital | 15% |
| Collateral | 10% |
| Conditions | 15% |

FOIR policy: a single limit, 50% by default and editable in the Credit policy box, drives the eligibility decision, risk indicators, stress tests, maximum eligible loan and analyst actions. A request above the limit is reduced to the maximum eligible amount rather than declined outright.

Knock-out rules (any one declines the loan): past default, score below 650, three or more late payments, existing EMIs leaving no room for a new loan within the FOIR limit, or age outside 21–70 at maturity.

Thresholds follow common Indian retail-lending practice and are illustrative. Adjust them in the `calc()` function of `index.html` to match a lender’s policy.

## Disclaimer
Educational project. Not a substitute for a lender’s official credit policy or underwriting.

## Tech
Single HTML file with plain JavaScript and inline SVG. No build step, no dependencies.
