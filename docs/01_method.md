# Method & caveats — UK Crime case study

## Sources (all Open Government Licence v3.0)
- **Home Office — Police recorded crime, Police Force Area tables** (`prc-pfa-mar2013-onwards`): force × financial quarter × offence code × count, 2012/13 → 2025/26.
- **Home Office — Outcomes open data, year ending March 2025**: force × offence × outcome type × count.
- **ONS — Population estimates for police force areas, mid-1991 to mid-2024**: single year of age & sex, summed to a total per PFA (mid-2024 used).
- **ONS Open Geography — Police Force Areas (Dec 2023) Boundaries EW (BUC)**: choropleth geometry.

## Headline period
**Year ending March 2025 (2024/25)** — the last *complete* financial year. The 2025/26 sheet held only Q1–Q3 at the time of analysis, so using it would understate a full year. Multi-year trend uses 2012/13–2024/25.

## Processing decisions
1. Load all year sheets; the first 8 columns are consistent (the 2013/14 sheet has 3 stray duplicate header columns, dropped by taking columns 0–7).
2. `Number of Offences` coerced to numeric; 3 `N/a` cells → 0 (negligible).
3. **Territorial vs central:** 6 "forces" are not geographic areas — Action Fraud, CIFAS, Cifas, Financial Fraud Action UK, UK Finance (central fraud reporting) and British Transport Police (no resident population). Excluded from the 43-force geographic analysis.
4. **Fraud excluded from per-area rates** (recorded centrally, not by territorial force); reported separately (~1.28M).
5. **Per-capita** = crimes ÷ ONS mid-2024 resident population × 1,000. Force names reconciled by normalising `&` → `and` (only "Devon & Cornwall" differed); all 43 matched.

## Reconciliation (2024/25)
| Component | Offences |
|---|---|
| Territorial forces, excl. fraud | 5,225,477 |
| Fraud (central) | 1,281,354 |
| British Transport Police (non-fraud) | ~81,996 |
| **Total recorded (all bodies)** | **6,588,827** |

## Caveats that change the read
- **Recorded crime ≠ actual crime** — depends on reporting and police recording. Part of the 2013–2019 rise reflects improved recording (HMICFRS-driven), not only real increases; CSEW measures victimisation differently.
- **City of London rate ≈ 607/1,000** is a denominator artifact (≈9k residents vs a very large daytime/commuter population). Flagged, never used as the headline.
- **England & Wales only** — Scotland and Northern Ireland use separate recording systems.
- **No offender demographics** exist in UK open crime data; no nationality/ethnicity claims are made.

## Key figures
- E&W overall rate: **84.5 / 1,000** (excl. fraud).
- Highest rates (excl. City of London artifact): Cleveland 119.0, West Yorkshire 113.0, Greater Manchester 105.9.
- Mix: Violence 36.8%, Theft 33.3%, Criminal damage 8.7%, Public order 8.4%.
- Shoplifting: 340k (22/23) → 440k (23/24) → 526k (24/25).
- Outcomes: Charged/summonsed **8.6%**; no suspect identified **39.8%**.
