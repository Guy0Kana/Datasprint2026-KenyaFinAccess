# Datasprint2026-KenyaFinAccess
Machine learning project for Strathmore Data Community DataSprint 2026, predicting financial status changes among Kenyan adults using the 2024 FinAccess Household Survey dataset.

# Financial Status Prediction in Kenya using FinAccess 2024 Data

## Overview

This project was developed for **DataSprint 2026**, organized by the Strathmore Data Community.

Using data from the **2024 FinAccess Household Survey**, the objective was to build a machine learning model capable of predicting whether a Kenyan adult's financial situation had:

- Improved
- Stayed the Same
- Worsened

The project combines exploratory data analysis, feature engineering, predictive modelling, and policy-focused recommendations to identify the factors most strongly associated with financial wellbeing.

---

## Problem Statement

Financial wellbeing is a key component of economic resilience and social development. Understanding the factors associated with changes in financial status can help policymakers, financial institutions, and development organizations design more effective interventions.

This project seeks to answer:

> Which demographic, financial behaviour, and financial health factors are most strongly associated with a Kenyan household's self-reported financial status?

---

## Dataset

Source:
- Kaggle dataset provided for DataSprint 2026

### Dataset Summary

- 20,871 respondents
- 28 variables
- Multiclass target variable:
  - Improved (20.5%)
  - Stayed the Same (26.9%)
  - Worsened (52.6%)

### Feature Categories

#### Demographics
- County
- Location Type
- Sex
- Age
- Household Size
- Education Level
- Marital Status
- Disability Status

#### Financial Behaviour
- Savings Usage
- Loan Usage
- Mobile Money Access
- Formal Financial Service Usage
- Financial Product Ownership

#### Financial Health
- Financial Literacy
- Financial Health Indicators
- Emergency Fund Access
- Financial Difficulty Indicators

---

## Project Workflow

### 1. Data Cleaning

- Missing values in `barriers_bank` were filled with `"No barrier"`
- Data types were inspected and validated
- Categorical variables were encoded for modelling

### 2. Exploratory Data Analysis (EDA)

Key areas explored:

- Target class distribution
- Demographic characteristics
- Financial inclusion indicators
- Financial resilience indicators
- Relationships between predictors and financial status

### 3. Feature Engineering

Three derived features were created:

#### Income Band

Monthly income was grouped into meaningful income categories to improve interpretability.

#### Resilience Score

A composite measure combining:

- Shock exposure
- Emergency fund access
- Financial health indicators

Higher values indicate stronger financial resilience.

#### Financial Access Score

A composite measure representing the degree of participation in formal financial services.

---

## Data Leakage Assessment

Several financial health variables were assessed for potential target leakage due to their conceptual similarity to the target variable.

Cross-tabulation analysis showed meaningful associations with financial status, but no evidence of near-perfect target separation. These variables were therefore retained while being interpreted cautiously during model evaluation.

---

## Models Evaluated

### Logistic Regression

Used as a baseline multiclass classifier.

### Random Forest

Used to capture non-linear relationships and feature interactions.

### XGBoost

Used as the final ensemble model due to its strong performance on structured tabular data.

---

## Evaluation Metric

The target variable was imbalanced, making accuracy a misleading metric.

Models were therefore evaluated using:

### Weighted F1-Score

This metric balances precision and recall while accounting for class imbalance.

---

## Results

| Model | Weighted F1 Score |
|---------|---------|
| Logistic Regression | 0.500 |
| Random Forest | 0.505 |
| XGBoost | 0.505 |

XGBoost achieved the best overall performance, although all three models produced similar results.

This suggests that financial status is a complex and multidimensional outcome influenced by factors that may not be fully captured in the survey data.

---

## Key Findings

### Financial Resilience Matters More Than Financial Access

The strongest predictors of financial status were related to:

- Financial resilience
- Emergency preparedness
- Financial wellbeing

Access-related variables such as mobile money access and financial literacy showed weaker relationships with financial outcomes.

### Top Predictors

- Resilience Score
- Marital Status
- Education Level
- Age
- Financial Access Score
- Monthly Income

---

## Recommendations

### Policymakers

- Strengthen programs that help households build financial resilience.
- Expand social protection and emergency support systems.

### Financial Institutions

- Develop affordable emergency savings products.
- Reduce barriers to accessing formal financial services.

### NGOs and Development Partners

- Support interventions that improve households' ability to cope with financial shocks.
- Focus on resilience-building alongside financial inclusion initiatives.

---

## Repository Structure

```text
.
├── data/
├── finaccess2024.ipynb //notebook
├── slides/
│   └── DataSprint2026_Presentation.pptx
└── README.md
```

---

## Technologies Used

- Python
- Pandas
- NumPy
- Matplotlib
- Seaborn
- Scikit-learn
- XGBoost
- Jupyter Notebook

---

## Author

Developed for **DataSprint 2026** by the Strathmore Data Community.
