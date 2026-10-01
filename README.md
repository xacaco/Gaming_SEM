# Data Quality Control, Exploratory Analysis and Structural Equation Modeling of a Longitudinal Cohort (Python)

## Summary

A reproducible data quality control (QC) and exploratory data analysis (EDA) pipeline for a four-wave longitudinal study of **Big Five personality traits and video gaming exposure** in adolescents and emerging adults. The pipeline prepares the data for a **Random Intercept Cross-Lagged Panel Model (RI-CLPM)** and a **Latent Growth Curve Model**, which separates stable between-person differences from within-person change over time.

**Skills shown:** data cleaning and harmonisation across waves, missing-data diagnostics, outlier detection, within-person change analysis, sample description, and modelling in Mplus.

**Tools:** Python (pandas, NumPy, SciPy, statsmodels, matplotlib, seaborn, pyampute), Jupyter. The models are estimated in Mplus.

## Research context

The original project investigates how personality traits (especially Conscientiousness and Neuroticism) and video gaming exposure influence each other over time, and whether this reflects **selection** (personality predicts later gaming) or **socialisation** (gaming predicts later personality change). Cross-lagged models are only trustworthy if the data are clean and show real within-person variation, which is what this QC pipeline checks.

## What the notebook does

`Imagen_QC.ipynb` is organised in these sections:

1. **Data cleaning and processing**
   - Import of the raw wide-format file (about 1500 participants, 149 variables in the real data).
   - Renaming of long raw column names and regrouping into domains: metadata, personality (NEO and SURPS), video gaming exposure, gaming profiles, and gaming disorder items.
   - Transformation of categorical gaming responses into numerical values (the midpoint of each response category), and construction of an exposure index (**hours per day × days per week = hours per week**).
   - Non-gamers coded as zero exposure instead of missing.
2. **Missingness**
   - Extent of missing values by variable and wave.
   - Retention and attrition across waves.
   - Missingness structure, including a test of whether data are missing completely at random (MCAR).
3. **Outliers**
   - Cross-sectional outliers within each wave.
   - Longitudinal outliers (implausible changes between waves).
   - Characteristics of outlying participants.
4. **Within-person variability**
   - Change plots.
   - Reliable Change Index.
   - Effect sizes for intra-individual change.
5. **Retrospective bias**
   - Comparison of reported frequency and intensity of gaming, and checks of their consistency.
6. **Sample description**
   - Descriptive statistics and correlations.
   - Group comparisons: gamers vs non-gamers and sex differences (with multiple-comparison correction), and gamers vs non-gamers controlling for sex.
   - Exclusion criteria (participants with a pattern compatible with internet gaming disorder).
   - Differences across study centres.

## Key decisions and limitations

- Category midpoints are an approximation of true hours and days of play.
- Outliers are flagged with a 2.5 standard deviation rule, and participants are excluded only after inspecting them, not automatically.
- The simulated data come from simple random-intercept and autoregressive processes. They will not show the same effects, or the same missingness mechanism, as a real cohort, so the results demonstrate the *method*, not any substantive finding.
- Log transformation is applied to reduce skew in gaming exposure before modelling.

## Data availability

The original analysis used data from the IMAGEN project, which are only available to approved researchers under the cohort's data-sharing policy. Outputs and results discussions have been hidden in this file version.

## Author

**Xavier Calvet Colomé**
