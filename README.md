# Credit Portfolio VaR/ES (Excel mini-model)

A small, transparent credit portfolio loss model built in Excel. It is designed as an application artifact: simple enough to explain, but complete enough to demonstrate quantitative readiness.

- Inputs: loan-level **PD (1y)**, **EAD**, guarantee type and coverage
- Outputs: **EL**, **VaR(99%)**, **ES(99%)**
- Extras: 3 stress scenarios + a basic calibration view (PD buckets)

> Confidentiality: the original loan-level dataset is not shared. This repo includes a **synthetic sample** to reproduce the workflow.

## Files
- `excel/credit_portfolio_var_es.xlsx` - the model workbook (public build: synthetic data)
- `docs/one-page-memo.pdf` - one-page risk note (for quick review)
- `docs/results_table.csv` - stress results table (exported)
- `data/synthetic_loan_pool.csv` - synthetic sample dataset (optional demo)
- `docs/screenshots/` - replace placeholders with real screenshots (recommended)

## Quick start (Excel)
1. Open `excel/credit_portfolio_var_es.xlsx`
2. Go to `Stress` and choose **Base / Mild / Severe**
3. Copy the recommended parameters and paste into `Simulation` (as values), then press **F9**
4. Read EL / VaR / ES on `看板` (Dashboard)

Tip: Because the simulation uses `RAND()`, results change each refresh. For a “final” number, paste the headline results into `Stress -> 结果记录` as values.

## Headline results (alpha=0.99, N=3,000)
| Scenario | PD x | LGD + | rho | EL (sim, bn RMB) | VaR99 (bn) | ES99 (bn) |
|---|---:|---:|---:|---:|---:|---:|
| Base | 1.00 | 0.00 | 0.10 | 5.30 | 19.68 | 23.69 |
| Mild | 1.20 | 0.03 | 0.15 | 6.69 | 29.89 | 36.15 |
| Severe | 1.50 | 0.06 | 0.20 | 8.76 | 43.79 | 52.74 |

## Model notes (short)
- LGD is a documented heuristic (guarantee type + coverage cap at 100%).
- Defaults are simulated with a one-factor Gaussian model (systemic factor + asset correlation `rho`).
- Validation is a lightweight calibration check (predicted vs observed default rate by PD buckets).

## Suggested screenshot set (for SOP / resume link)
- Dashboard (`看板`)
- Validation (`Validation`)
- Stress table (`Stress`)
- Simulation parameter area (`Simulation` top-right)

## Resume bullet (copy/paste)
Built an Excel credit portfolio loss model using PD/LGD/EAD to produce EL, VaR99 and ES99 under baseline and stressed scenarios, with a basic calibration check and documented limitations. (link)

