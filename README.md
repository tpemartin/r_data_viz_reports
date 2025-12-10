# R Data Visualization Reports

Data visualization workflows in R for municipal- and village-level datasets. The repo keeps cleaned/derived CSVs under `data/` and leaves raw inputs in `data/raw/` (git-ignored).

## Getting Started
- Requirements: R (4.3+), Quarto CLI, and packages `sf`, `dplyr`, `ggplot2`, `rmapshaper` (install with `install.packages(c("sf","dplyr","ggplot2","rmapshaper"))`).
- Raw spatial data (shapefiles, etc.) live in `data/raw/` and stay untracked; derived CSVs such as New Taipei income/household tables are committed under `data/` for reproducibility.

## Project Structure
- `data/` cleaned datasets ready for analysis (e.g., `income_distribution_by_village_2022_newTaipei.csv`, `village_household_population_statistics_2022_newTaipei.csv`).
- `data/raw/` source files, including the village boundary shapefile `村(里)界(TWD97經緯度)1141031/` (ignored by git).
- `codebook/` dataset notes and definitions (`income_distribution_by_village_2022_newTaipei.md`).
- `scripts/` R scripts for cleaning/visuals.
- `reports/` Quarto reports (e.g., `progress_tracking.qmd`).

## Usage
- Render the current progress report: `quarto render reports/progress_tracking.qmd`.
- Adjust data paths in scripts/reports if adding new raw sources under `data/raw/`.
- Save new exploratory notebooks or figures to `reports/`, and update matching codebook entries when datasets change.
