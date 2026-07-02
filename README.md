# Stellar Object Classification — SDSS DR17

[![Open in Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/AsserGharib1/StellarClassificationSdss17/blob/main/stellar_classification.ipynb)
[![View on nbviewer](https://img.shields.io/badge/view%20full%20notebook-nbviewer-F37626?logo=jupyter&logoColor=white)](https://nbviewer.org/github/AsserGharib1/StellarClassificationSdss17/blob/main/stellar_classification.ipynb)


Three-class classification (star / galaxy / quasar) of **100,000+ observations** from the Sloan Digital Sky Survey (SDSS17).

## Results

| Model (GridSearchCV-tuned) | Accuracy | ROC-AUC |
|---|---|---|
| **Random Forest** | **97.6%** | **0.996** |
| SVM | high | — |
| Logistic Regression | baseline | — |

## Pipeline

- Train/test split before any fitting (leakage-safe), mean imputation of injected nulls
- IQR-based outlier analysis on photometric bands (u, g, r, i, z)
- Feature/target exploration: redshift separability, band correlations
- Encoding + scaling, then `GridSearchCV` tuning for all three models
- Evaluation with confusion matrices, per-class precision/recall/F1, ROC-AUC

## Sample outputs

Sky positions by object class:

![Sky positions](figures/sky_positions.png)

Photometric feature correlations:

![Correlation matrix](figures/correlation_matrix.png)

Learning curve:

![Learning curve](figures/learning_curve_1.png)

## Repository contents

- `stellar_classification.ipynb` — full workflow with preserved outputs.
- `star_classification.csv` — SDSS DR17 sample (source: SDSS via Kaggle, *Stellar Classification Dataset – SDSS17*).

## Running

```bash
pip install -r requirements.txt
jupyter notebook stellar_classification.ipynb
```
