# Project FirstJet

An independent airline economics and launch-scenario laboratory using First Jet Airways as a case study.

## Project question

Under what combination of fares, load factor, aircraft utilization, operating costs, and membership economics could a First Jet-style low-cost airline become economically viable?

This is **not** First Jet Airways' internal financial model or a prediction of its future results. It separates:

- company disclosures;
- government aviation data;
- comparable-airline benchmarks; and
- explicit scenario assumptions.

## Planned build sequence

1. Define the model and terminology.
2. Build a comparable-airline benchmark table.
3. Implement the single-aircraft economics engine.
4. Validate formulas with tests and sanity checks.
5. Add sensitivity analysis and an interactive prototype.
6. Add route, fleet, startup-capital, and uncertainty modules.

## Repository structure

```text
docs/                  Project decisions and model documentation
data/raw/              Original downloaded data (not committed by default)
data/processed/        Cleaned datasets used by the model
src/project_firstjet/  Python model package
tests/                 Automated model tests
```

## Status

Stage 0 — project framework and model specification.
