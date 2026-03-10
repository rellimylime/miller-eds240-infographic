# eds240-infographic

Data visualization final project for EDS 240 (Winter 2026).

A deadpan parody PSA infographic examining three myths about drunk driving in California, using crash data from the CA Highway Patrol SWITRS database (2024). The infographic is assembled inside a car-interior illustration in Affinity Designer; the three data panels are generated in R.

---

## The Three Myths

1. **Sober drivers cause more crashes** — the majority of at-fault crashes involve sober drivers (counts, not rates)
2. **Drunk driving peaks at 2am** — sober crashes peak during rush hour; drunk crashes peak late night; the mismatch implies alcohol isn't responsible for the most dangerous conditions
3. **Drunk driving is what's killing Californians** — sober men alone account for more estimated deaths than all drunk drivers combined (absolute deaths, not fatality rate)

---

## Repository Structure

```text
FPM-Assignments/
  exploration.qmd       # data cleaning, joining, and EDA; saves processed data
  drafting_viz.qmd      # production code — three inline visualizations + ggsave exports
  inspo1.jpg            # inspiration reference images
  inspo2.jpg
  myth1_sketch.png      # hand-drawn planning sketches
  myth2_sketch.png
  myth3_sketch.png
  myth1.pdf             # chart exports used in Affinity assembly
  myth2.pdf
  myth3.pdf

data/
  processed/
    crash_clean.csv     # cleaned, filtered, joined crash + party data (tracked)
  raw/                  # gitignored — download instructions below

docs/
  FPM4.pdf              # FPM #4 assignment instructions
  240Final.pdf          # EDS 240 final project description
  draft.png             # first Affinity layout draft

draft2.png              # current working draft of assembled infographic
draft2.af               # Affinity Designer source file for the infographic
```

**Gitignored (not in repo):**

- `data/raw/` — raw SWITRS CSVs (large; download separately)
- `figures/` — generated plot outputs (reproduced by running `drafting_viz.qmd`)
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
2. Run `FPM-Assignments/drafting_viz.qmd` — it loads from `data/processed/crash_clean.csv`, renders all three charts inline, and exports PDFs to `FPM-Assignments/`

To re-run cleaning from scratch: download the raw SWITRS CSVs, place in `data/raw/`, then run `exploration.qmd` first.

The final infographic layout (`draft2.af`) is assembled in Affinity Designer using the exported PDFs as placed assets.
