# Climate Risk and Mortgage Default: Loan-Level Evidence from Florida

Code accompanying the MSc dissertation *Climate Risk and Mortgage Default:
Loan-Level Evidence from Florida* (University College Dublin).

The project tests whether hurricane wind exposure carries independent
predictive signal for mortgage default beyond traditional underwriting
variables, using Fannie Mae conforming loans in Florida (2017 Q1 vintage,
tracked through December 2024).

## Repository structure

    notebooks/     Jupyter notebooks (data preparation, feature construction, modelling)
    data/          Instructions for obtaining the raw data (data files not included)
    requirements.txt

## Notebook execution order

| Notebook | Purpose |
|----------|---------|
| 02_hud_zip3_mapping        | Build weighted ZIP3-to-county crosswalk (for FEMA specification) |
| 03_fema_hurricanes         | Process FEMA disaster declarations |
| 04_fannie_mae_fl_restriction | Restrict Fannie Mae data to the Florida analysis sample |
| 05_summary                 | Sample summary statistics |
| 07_static_feature_table    | Build the static loan-level feature table |
| 12_climate_merge_hurdat2   | Construct HURDAT2 wind-exposure variables and merge onto loans |
| 10_M2_climate_logit        | Fit M1 and M2 logistic regressions; likelihood-ratio test |
| 15_final_robustness        | Final robustness checks across specifications |

Note: notebook numbering is not fully contiguous. Run in the order shown above.

## Data sources (not redistributed here)

- **Fannie Mae Single-Family Loan Performance Data** — Fannie Mae Data Dynamics.
  Subject to Fannie Mae's terms of use; not redistributed in this repository.
- **NOAA HURDAT2** — Atlantic hurricane track data, NOAA National Hurricane Center.
- **FEMA OpenFEMA Disaster Declarations** — OpenFEMA API.
- **HUD-USPS ZIP Code Crosswalk** — HUD USPS ZIP Code Crosswalk Files.
- **SimpleMaps US ZIP Codes Database** — free tier, used under attribution.

## Setup

    pip install -r requirements.txt

Paths at the top of each notebook must be updated to point to your local
copies of the raw data.

## Environment

Python 3.13. Key libraries: pandas, numpy, pyarrow, statsmodels,
scikit-learn, xgboost, shap.
