# AI in Dental Education — Perceptions, Psychometrics & Explainable ML

## Project Description

This repository contains the full analysis pipeline and manuscript for a cross-sectional study examining dental students' perceptions of artificial intelligence (AI) in their education. The project combines **psychometric validation** (reliability analysis, exploratory factor analysis) with **explainable machine learning** (six regression algorithms benchmarked against a leakage-controlled predictor set, interpreted using SHAP) to identify which perception domains most strongly predict students' perceived overall learning benefit from AI — termed **PAILE (Perceived AI Learning Enhancement)**.

The study surveyed dental students across six conceptual domains — AI Adoption, Academic Learning, Clinical Learning, Teaching Enhancement, AI Risk, and Learning Efficiency — using a 19-item Likert-scale questionnaire, and asked a single question with two competing analytical lenses: **does AI adoption drive perceived benefit, or does perceived teaching enhancement?** The answer, converging across both classical regression and explainable ML, is Teaching Enhancement.

### Key Features

- **End-to-end reproducible pipeline**: raw survey CSV → cleaned dataset → psychometrics → regression → ML → SHAP explainability, in a single script/notebook
- **Leakage-controlled prediction**: the ML predictor set explicitly excludes the sub-components used to construct the outcome variable (PAILE), avoiding target leakage
- **Complete-case analysis**: a single, consistent sample (no mixed imputation/listwise-deletion across sections) used identically for every statistical and ML step
- **Six benchmarked ML models**: Linear Regression, Ridge, LASSO, Support Vector Regression, Random Forest, XGBoost — compared via 10-fold cross-validation and an independent held-out test set
- **Explainable AI**: global and directional SHAP analysis of the best-performing model


### Repository Structure

```
.
├── README.md                              # This file
├── AI_Dental_Analysis_CORRECTED.ipynb     # Analysis pipeline (notebook form)
├── Supplementary Data XLS

```



### Data

Raw survey data are **not included** in this repository to protect participant privacy, consistent with the study's ethical approval and informed-consent terms. To run the pipeline on your own data, supply a CSV with the same column structure (demographics + 19 Likert items) and point `DATA_FILE` in the script/notebook to its location.

### Requirements

- Python 3.12
- pandas, NumPy, SciPy, statsmodels, scikit-learn, factor_analyzer, SHAP, XGBoost, Matplotlib, seaborn

Install with:
```bash
pip install pandas numpy scipy statsmodels scikit-learn factor_analyzer shap xgboost matplotlib seaborn
```

Analyses were originally run on a standalone laptop (Intel Core i5 processor, 8 GB RAM); no GPU or high-performance computing resources are required.

### Usage

```bash
python AI_Dental_Analysis_CORRECTED.py
```
or open `AI_Dental_Analysis_CORRECTED.ipynb` in Jupyter and run all cells top to bottom. Update the `DATA_FILE` path in the first configuration cell/step to point to your raw CSV before running.

### Summary of Findings

- Sample: N = 295 complete cases (78.6% female, mean age 21.1 years)
- Questionnaire reliability: Cronbach's α = 0.62–0.92 across six domains
- Exploratory factor analysis supported a three-factor structure (KMO = 0.91)
- Regression: AI_Adoption and Teaching_Enhancement were significant predictors of PAILE (p < 0.001); no problematic multicollinearity (VIF ≤ 1.80)
- Best ML model: Random Forest (test R² = 0.618, RMSE = 0.337)
- SHAP: Teaching_Enhancement was the dominant predictor of perceived AI learning benefit, ahead of AI_Adoption, Academic_Performance, and AI_Risk

Full methodology, tables, and figures are reported in the manuscript under `manuscript/`.

### Citation

Research Paper Communicated. to be updated 

### License

[ CC-BY-4.0]

