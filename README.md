# Individual Credit Analysis Dashboard

A browser-based tool that analyses an individual loan applicant and suggests whether to approve, reduce or decline the loan.

**Live demo:** https://YOUR-USERNAME.github.io/credit-analysis-dashboard/

## What it analyses
- Credit score, late payments, card utilisation, recent enquiries, past defaults
- Age, employment type, years in current job, sector outlook, income
- Existing EMIs, proposed EMI, FOIR, residual income, savings cover
- The 5 Cs of credit: Character, Capacity, Capital, Collateral, Conditions
- Stress tests: rate rise, income fall, job loss

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

Knock-out rules (any one declines the loan): past default, score below 650, three or more late payments, post-loan FOIR above 60%, or age outside 21–70 at maturity.

Thresholds follow common Indian retail-lending practice and are illustrative. Adjust them in the `calc()` function of `index.html` to match a lender’s policy.

## Disclaimer
Educational project. Not a substitute for a lender’s official credit policy or underwriting.

## Tech
Single HTML file with plain JavaScript and inline SVG. No build step, no dependencies.
