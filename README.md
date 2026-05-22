# Retail Fraud Detection Analysis

## Project Overview

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

## Business Objectives

The project was designed to answer the following business questions:

1. Can fraudulent retail transactions be detected using customer and transaction behavior variables?

2. Which predictive model provides the best performance for fraud detection?

3. Which transaction patterns appear most strongly associated with fraudulent activity?

---

## Dataset

### Dataset Used

`retail_fraud_detection_100k.csv`

### Source

Source: Kaggle Retail Fraud Detection Dataset https://www.kaggle.com/datasets/noopurbhatt/retail-intelligence-fraud-detection-dataset

The dataset contains simulated retail transaction data, including:

- transaction behavior
- payment information
- device usage
- location information
- historical fraud indicators
- transaction frequency metrics

---
## Data Limitations

Several limitations were identified during the analysis process.

First, some variables appeared to be extremely predictive of fraudulent activity and initially produced near-perfect model performance in the GLM model. This resulted in statistical issues such as quasi-perfect separation, unstable coefficients, and unrealistic predictive behavior. These variables likely originated from pre-engineered fraud detection logic or previously modeled fraud indicators embedded within the dataset itself.

To create a more realistic fraud detection scenario and improve model interpretability, some highly deterministic fraud-related variables were removed or excluded from certain modeling stages. This allowed the models to rely more heavily on behavioral transaction patterns rather than near-direct fraud indicators.

Another important consideration is the class distribution of the dataset. The fraud and non-fraud classes were relatively balanced, which simplified the modeling process and reduced the need for advanced imbalance handling techniques. However, in real-world fraud detection systems, fraudulent transactions are typically rare events and datasets are often highly imbalanced. As a result, the predictive performance observed in this project may be more optimistic than what would be expected in a real production environment.

These limitations highlight the importance of understanding data generation processes, feature leakage risks, and the realism of modeling assumptions when developing fraud detection systems.

---
## Tools & Libraries

### Tools

- R
- RStudio

### Main Libraries

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
- lubridate

---

## Project Workflow

### 1. Data Import

- Imported raw transaction dataset
- Inspected variable structure and data types

---

### 2. Exploratory Data Analysis (EDA)

- Distribution analysis
- Fraud vs non-fraud comparisons
- Correlation analysis
- Histograms and density plots
- Categorical variable analysis

---

### 3. Data Cleaning & Preprocessing

- Converted categorical variables into factors
- Removed unnecessary variables
- Prepared modeling dataset

---

### 4. Feature Engineering

Created additional variables to better capture fraud behavior patterns:

- transaction time periods
- weekday vs weekend activity
- interaction features
- transaction velocity indicators

---

### 5. Train/Test Split

- 80/20 stratified split using `caret`

---

### 6. Modeling

The following models were trained and evaluated:

- Full Logistic Regression (GLM)
- Partial GLM using significant variables only
- Ridge Logistic Regression
- Lasso Logistic Regression
- Decision Tree
- Random Forest

---

### 7. Model Evaluation

Models were evaluated using:

- Confusion Matrix
- ROC Curve
- AUC Score

---

## Key Findings

### 1. Fraud Detection Feasibility

The analysis demonstrated that fraudulent retail transactions can effectively be detected using customer and transaction behavior variables. Several models achieved strong predictive performance, suggesting that transaction behavior contains meaningful fraud-related signals.

---

### 2. Best Performing Model

Among all evaluated models, the Random Forest model achieved the highest AUC score, indicating superior predictive performance compared to linear models such as Logistic Regression, Ridge, and Lasso Regression.

This suggests that nonlinear relationships and interaction effects between variables play an important role in fraud detection.

---

### 3. Important Fraud Indicators

Several behavioral variables appeared strongly associated with fraudulent activity, including:

- unusual transaction locations
- high transaction frequency
- multiple transactions within short periods
- failed transaction attempts
- transaction velocity indicators

These findings suggest that behavioral transaction patterns may be more informative for fraud detection than static customer characteristics alone.

---

### 4. Interpretability vs Predictive Performance

While Random Forest achieved the strongest predictive performance, Logistic Regression remained valuable for interpretability and business understanding through coefficient analysis and odds ratios.

This highlights the tradeoff between predictive power and model interpretability in fraud analytics.

---

## Modeling Challenges

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

## Results Summary

| Model | Purpose | AUC |
|---|---|---|
| Full GLM | Interpretable baseline model | 0.881 |
| Partial GLM | Reduced interpretable model using statistically significant variables | 0.881 |
| Ridge/Lasso | Regularized logistic regression | 0.880 / 0.881 |
| Decision Tree | Explainable nonlinear model | 0.839 |
| Random Forest | Best predictive performance | 0.906 |

Final results showed that tree-based ensemble methods captured nonlinear fraud behavior more effectively than linear models.

---
## Business Recommendations

- Prioritize behavioral monitoring
- Flag transaction bursts
- Monitor unusual geographic behavior
  
---
## Future Improvements

Potential future improvements include:

- Hyperparameter tuning optimization
- Cross-validation strategies
- XGBoost implementation
- More realistic class imbalance handling
- Feature importance explainability using SHAP values
- Comparison with additional variable selection techniques
- Additional feature engineering based on interaction effects between behavioral variables
  
---

## Repository Structure

```text
├── data/
├── Retail_Fraud.Rmd
├── Retail_Fraud.html
├── Images/
├── README.md
```

---

## Author

### Ali Jazzar

- Actuarial Analyst
- Data Analytics & Statistical Modeling Enthusiast
- Passionate about fraud analytics, predictive modeling, and data-driven decision-making
