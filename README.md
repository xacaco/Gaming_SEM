# Data Quality Control, Exploratory Analysis and Structural Equation Modeling of Longitudinal Panel Data (Python + Mplus)

## Summary

A reproducible data quality control (QC) and exploratory data analysis (EDA) pipeline for four-wave longitudinal panel data on **personality traits and video gaming exposure**. The pipeline prepares the data for a **Random Intercept Cross-Lagged Panel Model (RI-CLPM)** and a **Latent Growth Curve Model (LGCM)**. The RI-CLPM separates stable between-person differences from within-person change over time.

**Skills shown:** data cleaning and recoding, missing-data diagnostics, outlier detection, within-person change analysis, measurement agreement, sample description, and structural equation modelling in Mplus.

**Tools:** Python (pandas, NumPy, SciPy, statsmodels, matplotlib, seaborn, pyampute), Jupyter, Mplus.

> **All data in this repository are simulated.** Variable names, codings, sample size, wave structure and effect sizes are invented for demonstration and do not correspond to any real dataset.

## Research question

Do personality traits and video gaming exposure influence each other over time? If so, is it **selection** (traits predict later gaming) or **socialisation** (gaming predicts later trait change)? Cross-lagged models can only answer this if the data are clean and show real within-person variation, which is what the QC pipeline checks.

## Repository contents

| File | Description |
|---|---|
| `Panel_QC.ipynb` | Simulation, QC and EDA pipeline. Ends by exporting the analytic files for Mplus. |
| `RICLPM.inp` | Mplus RI-CLPM for one trait (`x1`–`x4`) and log exposure (`y1`–`y4`). |
| `LGCM.inp` | Mplus multi-group quadratic latent growth curve model for one trait, comparing groups and adjusting for sex and age. |

## What the notebook does

1. **Data preparation**
   - Simulation of a wide-format panel (waves `T1`–`T4`) with random-intercept and autoregressive processes.
   - Conversion of categorical intensity and frequency responses to numeric values (category midpoints), and construction of an exposure index: **hours/day × days/week = hours/week**.
   - Non-users coded as zero exposure instead of missing, and a two-part (user / amount) treatment of the zero-inflated exposure, with a log transformation.
2. **Missingness**
   - Amount of missing data by variable and wave.
   - Pairwise coverage and complete-case retention.
   - Little's MCAR test and logistic-regression checks of a MAR pattern, which justify FIML estimation.
3. **Outliers**
   - Cross-sectional outliers (±3 SD) within each wave.
   - Change outliers (implausible jumps between waves).
   - Outlier characteristics: association with user status, and directional consistency across waves.
4. **Within-person variability**
   - Spaghetti plots.
   - Reliable Change Index.
   - Cohen's *d* for paired change.
5. **Measurement agreement**
   - Rank agreement and distribution of differences between two reports of the same exposure.
6. **Sample description**
   - Descriptive statistics, and correlations of person-level means and of change scores (FDR-corrected).
   - Group comparisons (users vs non-users, sex differences), logistic regressions adjusted for sex, and model-based sex-adjusted trajectories.
   - Statistical exclusion rule based on a problematic-use screening score.

## Key decisions and limitations

- Category midpoints only approximate true hours and days of play.
- Outliers are flagged with SD-based rules and inspected before any exclusion; nothing is removed automatically.
- Missing data are handled with FIML under a MAR assumption, not with mean imputation, which would shrink within-person variance.
- Log transformation reduces skew in the exposure before modelling.
- Because the data are simulated, the results demonstrate the *method*, not any substantive finding.

## Author

**Xavier Calvet Colomé**
