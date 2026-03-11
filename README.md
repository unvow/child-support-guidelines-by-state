# Child Support Guidelines by State

A comprehensive, machine-readable dataset of child support guideline parameters for all 50 U.S. states. Covers guideline models, income thresholds, percentage rates, parenting time adjustments, add-on expense rules, and minimum support amounts.

**No equivalent dataset exists anywhere.** This data is scattered across 50+ state court PDFs, statute codes, and administrative rules. This repo compiles it into clean, structured CSV files for the first time.

## Quick Facts

- **41 states** use the Income Shares model
- **6 states** use Percentage of Income (Alaska, Mississippi, Nevada, North Dakota, Texas, Wisconsin)
- **3 states** use the Melson Formula (Delaware, Hawaii, Montana)
- All states must review guidelines every **4 years** per federal law (42 U.S.C. § 667)

## Datasets

| File | Records | Description |
|------|---------|-------------|
| [`guideline_models.csv`](data/guideline_models.csv) | 50 | Model type, subtype, effective date, review cycle, statute citation |
| [`income_thresholds.csv`](data/income_thresholds.csv) | 50 | Income type (gross/net), combined income cap, self-support reserve |
| [`percentage_rates.csv`](data/percentage_rates.csv) | 260 | Base percentage rates by number of children (1–5) for each state |
| [`parenting_time_adjustments.csv`](data/parenting_time_adjustments.csv) | 50 | Overnight thresholds, adjustment methods, parenting time formulas |
| [`addon_rules.csv`](data/addon_rules.csv) | 150 | Childcare, medical, and education expense allocation rules |
| [`minimum_support.csv`](data/minimum_support.csv) | 50 | Minimum monthly support amounts and types |

**Total: 610 records across 6 datasets**

## Data Quality

- Every row includes a `statute_citation` linking to the specific state law
- Every row includes a `source` with a URL to the authoritative text
- Cross-referenced against NCSL, Justia, and state court publications
- No comment lines — all CSVs render correctly on GitHub

## Schema Quick Reference

### guideline_models.csv
```
state, state_abbr, model_type, model_subtype, effective_date, review_cycle_years, statute_citation, source
```
`model_type`: `income_shares` | `percentage_of_income` | `melson_formula`

### income_thresholds.csv
```
state, state_abbr, income_type, combined_income_cap, obligor_income_cap, minimum_income_threshold, self_support_reserve, currency_year, statute_citation, source
```

### percentage_rates.csv
```
state, state_abbr, num_children, base_percentage, income_bracket_low, income_bracket_high, notes, statute_citation, source
```

### parenting_time_adjustments.csv
```
state, state_abbr, threshold_type, threshold_value, threshold_unit, adjustment_method, notes, statute_citation, source
```

### addon_rules.csv
```
state, state_abbr, addon_type, allocation_method, notes, statute_citation, source
```

### minimum_support.csv
```
state, state_abbr, minimum_monthly_amount, minimum_type, notes, statute_citation, source
```

## Visualizations

Interactive charts and tables based on this dataset:

**[unvow.com/child-support-guidelines](https://unvow.com/child-support-guidelines)**

## Recent Notable Changes

| State | Change | Effective |
|-------|--------|-----------|
| Washington | Economic table expanded to $50,000/mo combined income; self-support reserve raised to 180% FPL | Jan 2026 |
| Pennsylvania | Updated income shares schedule with revised amounts | Jan 2026 |
| Georgia | New mandatory parenting time formula (x^2.5 power curve) | Jan 2026 |
| Virginia | First guideline schedule update in decades | Jul 2025 |
| Texas | Net resources income cap increased to $11,700/month | Sep 2025 |
| New York | Combined parental income threshold raised to $183,000/year | Mar 2024 |
| California | SB 343 changed add-on expense allocation | Sep 2024 |

## Sources

See [`sources/methodology.md`](sources/methodology.md) for data collection methodology and [`sources/state_statutes.md`](sources/state_statutes.md) for the complete list of statute citations.

## License

[CC BY 4.0](LICENSE) — Free to use with attribution.

## Contributing

Corrections and updates are welcome. See [CONTRIBUTING.md](CONTRIBUTING.md) for guidelines.

---

Maintained by [Unvow](https://unvow.com) — family law information and tools.
