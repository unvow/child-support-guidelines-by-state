# Contributing to Child Support Guidelines by State

Thank you for helping improve this dataset. Accurate child support guideline data helps families, legal professionals, and policy researchers make informed decisions.

## How to Submit Corrections

1. **Open an Issue** — Describe the error, include the correct data, and cite the specific state statute or court rule.

2. **Submit a Pull Request** — Fork the repo, make your changes, and include:
   - The corrected data in the relevant CSV file
   - The statute citation in the `statute_citation` column
   - The source reference in the `source` column
   - An update to `sources/state_statutes.md` if citing a new source

## Data Standards

- All dollar amounts are in USD
- Use USPS standard state abbreviations (e.g., CA, TX, NY)
- Every row must include `statute_citation` and `source` columns
- Percentage rates should be expressed as decimals (e.g., 20.0 for 20%)
- Income thresholds and caps should reflect the most current published guidelines

## What We Accept

- Corrections to existing data with verifiable statute citations
- Updated figures from newly published guideline schedules
- New state data from official court rules or legislative changes
- Corrections to effective dates or review cycle information

## What We Don't Accept

- Data without a verifiable state statute or court rule citation
- Estimates or projections not based on published guidelines
- Data from unofficial calculators or third-party interpretations
- Promotional content or links to commercial services

## Questions?

Open an issue or contact us at [unvow.com](https://unvow.com).
