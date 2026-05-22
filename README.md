# Retail Fraud Detection Analysis

# Project Overview

This project explores fraud detection using statistical and machine learning techniques in R. The objective was to identify behavioral patterns associated with fraudulent retail transactions and compare the predictive performance of several classification models.

The analysis focuses not only on predictive accuracy, but also on:

- feature engineering
- model interpretability
- variable selection
- realistic fraud detection considerations

Several models were developed and compared, including:

- Logistic Regression (GLM)
- Ridge Regression
- Lasso Regression
- Decision Tree
- Random Forest

---

# Business Objectives

The project was designed to answer the following business questions:

1. Can fraudulent retail transactions be detected using customer and transaction behavior variables?

2. Which predictive model provides the best performance for fraud detection?

3. Which transaction patterns appear most strongly associated with fraudulent activity?

---

# Dataset

## Dataset Used

`retail_fraud_detection_100k.csv`

## Source

Kaggle Retail Fraud Detection Dataset

The dataset contains simulated retail transaction data, including:

- transaction behavior
- payment information
- device usage
- location information
- historical fraud indicators
- transaction frequency metrics

---

# Tools & Libraries

## Tools

- R
- RStudio

## Main Libraries

- tidyverse
- caret
- glmnet
- ranger
- randomForest
- rpart
- rpart.plot
- pROC
- corrplot
- vip
- yardstick

---

# Project Workflow

## 1. Data Import

- Imported raw transaction dataset
- Inspected variable structure and data types

---

## 2. Exploratory Data Analysis (EDA)

- Distribution analysis
- Fraud vs non-fraud comparisons
- Correlation analysis
- Histograms and density plots
- Categorical variable analysis

---

## 3. Data Cleaning & Preprocessing

- Converted categorical variables into factors
- Removed unnecessary variables
- Prepared modeling dataset

---

## 4. Feature Engineering

Created additional variables to better capture fraud behavior patterns:

- transaction time periods
- weekday vs weekend activity
- interaction features
- transaction velocity indicators

---

## 5. Train/Test Split

- 80/20 stratified split using `caret`

---

## 6. Modeling

The following models were trained and evaluated:

- Full Logistic Regression (GLM)
- Partial GLM using significant variables only
- Ridge Logistic Regression
- Lasso Logistic Regression
- Decision Tree
- Random Forest

---

## 7. Model Evaluation

Models were evaluated using:

- Confusion Matrix
- ROC Curve
- AUC Score

---

# Key Findings

Several behavioral variables appeared strongly associated with fraudulent activity, including:

- unusual transaction locations
- high transaction frequency
- multiple transactions within short periods
- failed transaction attempts
- transaction velocity indicators

The Random Forest model achieved the highest AUC score, suggesting superior predictive performance compared to linear models.

However, Logistic Regression remained valuable for interpretability and business understanding through coefficient analysis and odds ratios.

---

# Important Analytical Considerations

During the analysis, some variables initially produced near-perfect prediction behavior in the GLM model, leading to:

- quasi-perfect separation
- unstable coefficients
- unrealistic predictive performance

This prompted additional model refinement and variable review to improve:

- interpretability
- realism
- statistical coherence

A reduced “partial GLM” model was therefore created using statistically significant variables selected through likelihood ratio tests (`drop1()`).

---

# Results Summary

| Model | Purpose |
|---|---|
| Full GLM | Interpretable baseline model |
| Partial GLM | Reduced interpretable model using statistically significant variables |
| Ridge/Lasso | Regularized logistic regression |
| Decision Tree | Explainable nonlinear model |
| Random Forest | Best predictive performance |

Final results showed that tree-based ensemble methods captured nonlinear fraud behavior more effectively than linear models.

---

# Future Improvements

Potential future improvements include:

- Hyperparameter tuning optimization
- Cross-validation strategies
- XGBoost implementation
- More realistic class imbalance handling
- Feature importance explainability using SHAP values
- Comparison with additional variable selection techniques

---

# Repository Structure

```text
├── data/
├── Retail_Fraud.Rmd
├── Retail_Fraud.html
├── README.md
```

---

# Author

## Ali Jazzar

- Actuarial Analyst
- Data Analytics & Statistical Modeling Enthusiast
- Passionate about fraud analytics, predictive modeling, and data-driven decision-making
