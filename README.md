# Reproducing the Paper Analysis

This repository contains the public code and data needed to reproduce the shareable parts of the paper's analysis. All analysis materials live in [`public/`](./public/).

The most direct reproduction path is:

1. Use the included scored CSV files in [`public/data/`](./public/data/).
2. Run `Rscript public/run_r_analyses.R` to regenerate the statistical result tables.

The Python notebooks that start from the anonymized survey exports are also included, but they require a separate Python/Jupyter setup. Full instructions, file mappings, and known limitations are documented in [`public/README.md`](./public/README.md).
