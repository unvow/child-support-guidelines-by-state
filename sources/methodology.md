# Methodology

## Overview

This dataset compiles child support guideline parameters from all 50 U.S. states into a machine-readable format. The data was collected from primary legal sources — state statutes, court rules, and administrative codes — and cross-referenced against secondary compilations.

## Data Collection

### Primary Sources
- **State statutes and codes** — The authoritative source for each state's guideline model, income definitions, percentage rates, and adjustment mechanisms.
- **Court-published guideline schedules** — Many states publish their child support schedules as appendices to court rules or as standalone documents. These contain the specific dollar amounts and percentages used in calculations.
- **Administrative agency rules** — In some states (e.g., Wisconsin DCF 150, Montana ARM 37.62), child support guidelines are promulgated by executive agencies rather than courts.

### Secondary Sources (Cross-Reference)
- **National Conference of State Legislatures (NCSL)** — State-by-state comparison of guideline model types and statutory citations.
- **Justia 50-state surveys** — Used to verify statute citations and identify recent amendments.
- **State child support enforcement agency websites** — For guideline worksheets, calculators, and instructional materials.

## Model Type Classification

States are classified into three guideline models:

1. **Income Shares** (41 states) — Both parents' incomes are combined to determine total child support obligation from a schedule, then each parent's share is allocated proportionally by income. Based on economic research into what intact families spend on children at various income levels.

2. **Percentage of Income** (6 states: Alaska, Mississippi, Nevada, North Dakota, Texas, Wisconsin) — Child support is calculated as a percentage of the noncustodial parent's income only. Subtypes:
   - **Flat** — Same percentage applies regardless of income level (Alaska, Mississippi, Wisconsin)
   - **Varying** — Percentage varies by income bracket (Nevada, North Dakota, Texas)

3. **Melson Formula** (3 states: Delaware, Hawaii, Montana) — A variant of income shares that first ensures each parent retains a self-support reserve, then allocates primary support needs, and finally adds a standard-of-living adjustment (SOLA) from remaining income.

## Effective Percentage Rates

For income shares states, the `percentage_rates.csv` contains **effective percentages** — the child support obligation as a percentage of combined parental income at the median combined income level (~$7,000/month). These are derived from each state's published schedule tables and represent the typical percentage, not a statutory flat rate.

For percentage-of-income states, the rates are the statutory percentages codified in law.

## Income Thresholds

- **Combined income cap** — The maximum combined parental income covered by the guidelines schedule. Above this amount, the court has discretion.
- **Obligor income cap** — Used by percentage-of-income states that cap the obligor's income for calculation purposes (e.g., Texas net resources cap).
- **Self-support reserve** — The amount an obligor retains for basic living expenses, typically tied to the federal poverty level (approximately $1,255–$1,398/month for a single person in 2024).

All income cap and threshold values in `income_thresholds.csv` are normalized to **monthly** amounts regardless of how the state statute defines them. Some states define caps annually (e.g., New York: $183,000/year → $15,250/month) or weekly (e.g., New Jersey: $3,600/week → $15,600/month). The `statute_citation` column links to the original source for anyone needing the raw statutory value.

## Percentage Rate Brackets

Most states have a single effective rate per child count. **Nevada** is an exception — NAC 425.140 defines a three-tier system where different percentages apply to different income brackets ($0–$6,000/month, $6,001–$10,000/month, and above $10,000/month). The `percentage_rates.csv` file accommodates this using the `income_bracket_low` and `income_bracket_high` columns, resulting in 15 rows for Nevada (3 brackets × 5 child counts) instead of the usual 5.

## Currency and Dates

- All dollar amounts are in U.S. dollars.
- Income thresholds are monthly amounts.
- Effective dates reflect the most recent published guidelines as of the dataset compilation date.
- Currency year indicates when the dollar amounts were last updated.

## Limitations

- Child support calculations involve many variables beyond what this dataset captures (e.g., specific income bracket tables, tax adjustments, deviation factors). This dataset provides the structural parameters, not a complete calculator.
- Some states update guidelines more frequently than the 4-year federal review cycle. The dataset reflects the most recent published guidelines at the time of compilation.
- Parenting time adjustment mechanisms vary significantly in complexity. The dataset captures threshold triggers and method types but not the full mathematical formulas.

## Updates

This dataset is maintained and updated as states publish new guidelines. Federal law (42 U.S.C. § 667) requires states to review guidelines at least every four years, so most states will update on a rolling basis.
