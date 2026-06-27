# COMP4381 Flight Delay Project
**Group name:** Delay Detectives  
**Project title:** Building a Data Science Pipeline for Flight Delays Around the World  

## Team members
- Ahmad Daghra — #1230188
- Kamel Shbeeb — #1221719
- Yusra Tareq — #1210900

## Project goal
Analyze airport punctuality and schedule delays across multiple countries and build a two-stage Phase 4 modeling pipeline at the airport-day unit of analysis.

## Data sources
- EUROCONTROL Daily Punctuality – Airports:
- OurAirports airport metadata: https://ourairports.com/data/

## Repository structure
- `data/raw/` raw datasets
- `data/processed/` final cleaned dataset
- `notebooks/` Jupyter notebooks (Phase 3 and Phase 4)
- `figures/` exported plots
- `report/` report sections / PDF

## How to run (Phase 3)
1. Open `notebooks/phase3_New.ipynb`
2. Run all cells from top to bottom (no manual steps needed if data exists in `data/raw/`)

## Phase 3 outputs
- Cleaned dataset: `data/processed/phase3_airport_day_clean.csv`
- Figures: `figures/`

## Phase 4 overview
Phase 4 uses the Phase 3 cleaned airport-day dataset to build a course-safe two-stage prediction system with Pandas, NumPy, Matplotlib, and Scikit-learn.

Stage 1 is a Logistic Regression classifier that predicts whether an airport-day has a significant arrival delay:
- Target: `target_delayed_15`
- Metrics: Accuracy, Precision, Recall, F1-score, Confusion Matrix, and ROC/AUC

Stage 2 is a Linear Regression model that estimates expected arrival delay minutes:
- Target: `target_delay_minutes`
- Metrics: MAE, MSE, RMSE, and R²

The regression model is trained on all airport-day rows. In the final two-stage system, the delay-minute estimate is reported only when the classification model predicts a significant delay.

## How to run (Phase 4)
1. Open `notebooks/phase4_modeling.ipynb`.
2. Restart the kernel.
3. Run all cells from top to bottom.

The notebook uses a robust project-relative path for the input dataset, so it can be run from the repository root or from the `notebooks/` folder as long as `data/processed/phase3_airport_day_clean.csv` exists.

Command-line execution from the repository root:

```bash
python -m jupyter nbconvert --execute --to notebook --inplace notebooks/phase4_modeling.ipynb
```

## Phase 4 outputs
- Final notebook: `notebooks/phase4_modeling.ipynb`
- Input dataset: `data/processed/phase3_airport_day_clean.csv`
- Classification confusion matrix: `figures/phase4_confusion_matrix.png`
- Classification metrics chart: `figures/phase4_classification_metrics.png`
- ROC curve: `figures/phase4_roc_curve.png`
- Regression actual vs. predicted plot: `figures/phase4_actual_vs_predicted.png`
- Regression residual scatter plot: `figures/phase4_residuals.png`
- Regression residual histogram: `figures/phase4_residual_histogram.png`
- Feature importance plots: `figures/phase4_stage1_feature_importance.png`, `figures/phase4_stage2_feature_importance.png`
