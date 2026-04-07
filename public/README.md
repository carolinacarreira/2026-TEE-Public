# Analysis — Public Materials

This folder contains the analysis scripts and anonymized data for the paper.

## Structure

```
public/
├── export/                          # Anonymized study 1 data (input for Python notebooks)
├── export_followup/                 # Anonymized follow-up study data
├── data/
│   ├── firststudy/                  # Scored CSVs for study 1 regressions
│   └── followup/                    # Scored CSVs for follow-up regressions
├── *.Rmd                            # R analysis scripts
├── *.ipynb                          # Python analysis notebooks
├── surveyfields.py                  # Field definitions for study 1
├── surveyfieldsfollowup.py          # Field definitions for follow-up study
└── *.csv                            # Output tables from R scripts
```

## How to reproduce the analysis

The analysis has two stages: (1) Python notebooks process the anonymized data into scored CSVs, and (2) R scripts run the statistical tests on those CSVs.

### Stage 1 — Python notebooks

**Requirements:** Python 3, pandas, seaborn, numpy

Run in order:

| Notebook | Input | Output |
|---|---|---|
| `analysis.ipynb` | `export/anonymized_data.csv` | Descriptive statistics and figures (study 1) |
| `analysis-followup.ipynb` | `export_followup/anonymized_data.csv` | Descriptive statistics and figures (follow-up) |
| `regression_export.ipynb` | `export/anonymized_data.csv` | `data/firststudy/*.csv` |
| `regression_followup.ipynb` | `export_followup/anonymized_data.csv` | `data/followup/*.csv` |

The scored CSVs in `data/` are already pre-generated, so you can skip to Stage 2 if you only want to reproduce the statistical tests.

### Stage 2 — R scripts

**Requirements:** R with packages `ordinal`, `lme4`, `dplyr`, `car`, `sjPlot`, `performance`, `broom`, `tidyverse`, `emmeans`, `ggplot2`, `MASS`, `brant`, `pscl`, `PMCMRplus`, `multcomp`, `RVAideMemoire`, `purrr`

Each script is self-contained and reads from `data/`:

| Script | Analysis | Output |
|---|---|---|
| `comprehension-regressions-firststudy.Rmd` | Logistic regressions on comprehension scores (study 1) | `BH_correction_1stStudy.csv`, `Holm_logistics_results_letters.csv` |
| `comprehension-regressions-followup.Rmd` | Logistic regressions on comprehension scores (follow-up) | `BH_corrections_survey2.csv`, `B-Holm_logistics_results_survey2.csv` |
| `willingness-safety-regressions-firststudy.Rmd` | Ordinal regressions on willingness and pre-study safety (study 1) | `BH_correction_1stStudy_will.csv`, `BH_correction_1stStudy_safety.csv` |
| `willingness-safety-regressions-followup.Rmd` | Ordinal regressions on safety perceptions (follow-up) | `BH_correction_2stStudy_will.csv`, `BH_correction_2stStudy_safety.csv` |
| `comprehension-features-vs-limitations.Rmd` | Wilcoxon tests: feature vs. limitation questions | `wilcox_BH_firststudy.csv`, `wilcox_BH_followup.csv` |
| `safety-aspects-info-vs-noinfo.Rmd` | Mann-Whitney U tests: safety aspects with vs. without TEE information | `Mann-Whitney_U_bh_corrections.csv` |

All output CSVs are pre-generated and included in this folder.
