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



## Problem Statement

Financial inclusion has expanded significantly in Kenya over the past decade, particularly through mobile money and digital financial services. However, access to financial services does not necessarily translate into improved financial wellbeing.

This project seeks to answer two key questions:

> Can an individual's financial status be predicted using demographic, behavioural, and financial-health characteristics?

> Which factors are most strongly associated with improved, stable, or deteriorating financial outcomes?

Understanding these relationships can help stakeholders design interventions that strengthen household resilience and improve financial wellbeing.



## Dataset

### Source

- FinAccess 2024 Household Survey
- Published by:
  - Central Bank of Kenya (CBK)
  - Kenya National Bureau of Statistics (KNBS)
  - FSD Kenya

### Dataset Characteristics

| Attribute | Value |
|------------|--------|
| Observations | 20,871 |
| Variables | 28 |
| Target Classes | 3 |
| Missing Values | Primarily in `barriers_bank` |

### Target Variable

`financial_status`

| Class | Proportion |
|---------|---------|
| Worsened | 52.6% |
| Stayed the Same | 26.9% |
| Improved | 20.5% |

The target variable is imbalanced, with over half of respondents reporting that their financial situation worsened.

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



## Methodology

The project followed a structured machine learning workflow consisting of six stages:

### 1. Data Understanding

The dataset was examined to understand:

- Variable types
- Category distributions
- Missing values
- Potential data quality issues
- Class imbalance

Special attention was given to understanding the socioeconomic meaning of variables rather than treating them purely as modelling inputs.

### 2. Data Cleaning

Several preprocessing steps were performed:

- Missing values in `barriers_bank` were filled with `"No barrier"` as specified in the competition brief.
- Duplicate records were checked.
- Variable formats were standardized.
- Categorical values were reviewed for consistency.

### 3. Exploratory Data Analysis (EDA)

EDA focused on identifying patterns and relationships associated with financial status.

Areas explored included:

- Demographic characteristics
- Income distribution
- Financial inclusion indicators
- Mobile money usage
- Financial literacy
- Emergency fund access
- Shock exposure
- Financial health indicators

Cross-tabulations and proportional visualizations were used extensively to compare financial outcomes across groups.

Statistical tests, including Chi-Square tests of independence and Cramér's V, were used where appropriate to assess the strength of observed relationships.

### 4. Feature Engineering

Several derived variables were created to improve interpretability and modelling performance.

#### Income Band

Monthly income was grouped into socioeconomic categories to reduce the influence of extreme values and capture threshold effects.

#### Resilience Score

A composite score was constructed using:

- Shock exposure
- Emergency fund access
- Financial health indicators
- Financial difficulty indicators

Higher values indicate stronger financial resilience.

#### Financial Access Score

A composite measure representing participation in formal financial services, including:

- Formal savings
- Formal loans
- Mobile money access
- Formal service usage

The goal was to distinguish financial access from financial resilience and evaluate their relative importance.

### 5. Model Development

Three supervised machine learning algorithms were evaluated:

#### Logistic Regression

Used as a baseline model due to its simplicity and interpretability.

#### Random Forest

Used to capture non-linear relationships and feature interactions.

#### XGBoost

Used as the final ensemble model because of its strong performance on structured tabular data.

### 6. Model Interpretation

Feature importance analysis was conducted using XGBoost to identify the variables contributing most strongly to predictions.

This step helped translate model outputs into actionable insights and recommendations.




## Data Leakage Assessment

Several financial health variables were assessed for potential target leakage due to their conceptual similarity to the target variable, including:

- `nfhi_12`
- `nfhi_13`
- `accessto_13k_1month`
- `not_difficult`

Cross-tabulation analysis showed meaningful associations with financial status, but no evidence of near-perfect target separation. These variables were therefore retained while being interpreted cautiously during model evaluation.



## Exploratory Data Analysis Highlights

Several important findings emerged during EDA.

### Financial Resilience Outperformed Financial Access

Variables related to financial resilience showed stronger and more consistent relationships with financial status than variables related to financial access.

### Emergency Fund Access Was Highly Informative

Respondents who could raise KES 13,000 in an emergency were substantially more likely to report stable or improving financial conditions.

### Mobile Money Access Showed a Weak Relationship

Although statistically significant, the relationship between mobile money access and financial status was weak, suggesting that access alone does not guarantee improved financial outcomes.

### Financial Literacy Produced Mixed Results

Financial literacy scores displayed a less consistent relationship with financial outcomes than expected, indicating that knowledge alone may not translate into financial resilience.



## Models Evaluated

### Logistic Regression

Used as a baseline multiclass classifier.

### Random Forest

Used to capture non-linear relationships and feature interactions.

### XGBoost

Used as the final ensemble model due to its strong performance on structured tabular data.



## Evaluation Metric

The target variable was imbalanced, making accuracy a misleading metric.

Models were therefore evaluated using:

### Weighted F1-Score

This metric balances precision and recall while accounting for class imbalance.


## Results

| Model | Weighted F1 Score |
|---------|---------|
| Logistic Regression | 0.500 |
| Random Forest | 0.505 |
| XGBoost | 0.505 |

XGBoost achieved the best overall performance, although all three models produced similar results.

This suggests that financial status is a complex and multidimensional outcome influenced by factors that may not be fully captured in the survey data.


## Feature Importance

Feature importance extracted from the XGBoost model identified the strongest predictors of financial status.

### Most Important Features

1. Resilience Score
2. Marital Status
3. Financial Access Score
4. Age
5. Income Band

## Key Findings

### Financial Resilience Matters More Than Financial Access

The strongest predictors of financial status were related to:

- Financial resilience
- Emergency preparedness
- Financial wellbeing

Access-related variables such as mobile money access and financial literacy showed weaker relationships with financial outcomes.

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
