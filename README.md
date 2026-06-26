# Predicting Drinking Water Potability from Chemical Properties

**Practical Machine Learning — Green Data Science 2025/2026**  
Instituto Superior de Agronomia, ULisboa  
**Author:** Luís Vale — Student ID: 25952

---

## 📌 Project Overview

This project applies machine learning to predict whether a water sample is safe to drink based solely on its chemical properties. It is a **binary classification problem** (potable = 1, not potable = 0) with real environmental relevance — automated water quality monitoring could reduce reliance on slow and costly manual lab testing.

**Dataset:** [Water Quality and Potability — Kaggle](https://www.kaggle.com/datasets/adityakadiwal/water-potability)  
3,276 water samples · 9 chemical features · Binary target

---

## 📁 Repository Structure

```
├── water_potability_project.ipynb   # Main notebook (code + results)
├── water_potability_report.docx     # Full project report
├── water_potability.csv             # Dataset
└── README.md
```

---

## Features

| Feature | Description |
|---|---|
| ph | pH value of the water |
| Hardness | Capacity of water to precipitate soap |
| Solids | Total dissolved solids (ppm) |
| Chloramines | Amount of chloramines (ppm) |
| Sulfate | Amount of sulfates dissolved (mg/L) |
| Conductivity | Electrical conductivity (μS/cm) |
| Organic_carbon | Amount of organic carbon (ppm) |
| Trihalomethanes | Amount of trihalomethanes (μg/L) |
| Turbidity | Measure of light-emitting property (NTU) |

---

## Methods

Each model is wrapped in a **scikit-learn Pipeline** (imputer → scaler → classifier) to prevent data leakage. Hyperparameters were tuned with **GridSearchCV** using **5-fold StratifiedKFold**, optimising F1-score.

| Model | Role |
|---|---|
| Logistic Regression | Linear baseline |
| Random Forest | Ensemble — bagging |
| XGBoost | Ensemble — gradient boosting |

---

## Results (Test Set)

| Model | F1 | ROC-AUC | Recall |
|---|---|---|---|
| Logistic Regression | 0.000 | 0.546 | 0.000 |
| **Random Forest** | **0.457** | **0.641** | **0.408** |
| XGBoost | ~0.44 | 0.624 | ~0.39 |

Best model: **Random Forest** (ROC-AUC = 0.641)

---

## How to Run

1. Open the notebook in **Google Colab**: upload `water_potability_project.ipynb` and `water_potability.csv`
2. Uncomment the first cell to install dependencies:
   ```python
   !pip install shap xgboost -q
   ```
3. Run all cells in order

---

## AI Usage

Parts of the code in this notebook were generated with AI assistance (Claude, Anthropic). All AI-generated sections are documented with `# prompt:` comments at the start of the relevant code blocks, as required by the course guidelines.

---

## References

- Kadiwal, A. (2021). *Water Quality and Potability*. Kaggle.
- Géron, A. (2019). *Hands-On Machine Learning with Scikit-Learn, Keras and TensorFlow*. O'Reilly.
- Lundberg, S. M., & Lee, S.-I. (2017). A unified approach to interpreting model predictions. *NeurIPS*, 30.
- World Health Organization. (2022). *Guidelines for Drinking-Water Quality* (4th ed.). WHO Press.
