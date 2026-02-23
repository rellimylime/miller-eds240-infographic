# eds240-infographic

Data visualization final project for EDS 240 (Winter 2026).

A deadpan parody PSA infographic examining three myths about drunk driving in California, using crash data from the CA Highway Patrol SWITRS database (2024).

---

## The Three Myths

1. **Sober drivers cause more crashes** — the majority of at-fault crashes involve sober drivers
2. **Drunk driving peaks at 2am** — sober crashes peak during rush hour; drunk crashes peak late night
3. **Drunk driving is what's killing Californians** — sober men alone account for more estimated deaths than all drunk drivers combined

---

## Repository Structure

```text
FPM-Assignments/
  exploration.qmd       # data cleaning, joining, and EDA; saves processed data
  drafting_viz.qmd      # submission script — three inline visualizations

data/
  processed/
    crash_clean.csv     # cleaned, filtered, joined crash + party data (tracked)
  raw/                  # gitignored — download instructions below
```

**Gitignored (not in repo):**

- `data/raw/` — raw SWITRS CSVs (large; download separately)
- `figures/` — generated plot outputs (reproduced by running the qmd files)
- `scratch/` — working R scripts and reference drafts used during development
- `investigate_myth3.R` — exploratory one-off script

---

## Data Source

CA Highway Patrol SWITRS database, 2024 export.

- Download portal: <https://iswitrs.chp.ca.gov>
- Two files needed: the **Crashes** CSV and the **Parties** CSV
- Place them in `data/raw/` before running `exploration.qmd`

The cleaning, filtering (to at-fault drivers), and joining of the two files is documented in `FPM-Assignments/exploration.qmd`. The processed output is saved there with `write_csv(crash_clean, here("data/processed/crash_clean.csv"))` and is committed to this repo, so you can skip straight to `drafting_viz.qmd` without re-downloading the raw data.

---

## Reproducing the Visualizations

1. Open `miller-eds240-infographic.Rproj` in RStudio
2. Run `FPM-Assignments/drafting_viz.qmd` — it loads from `data/processed/crash_clean.csv` and renders all three charts inline

To re-run cleaning from scratch: download the raw SWITRS CSVs, place in `data/raw/`, then run `exploration.qmd` first.
