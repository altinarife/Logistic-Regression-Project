# Predicting COVID-19 Mortality with Logistic Regression

## Project Overview

This capstone project uses machine learning to predict whether a COVID-19 patient will die within 30 days based on triage information, including age, gender, and eight blood biomarkers.

The main objective is to evaluate logistic regression and compare its performance with more flexible machine learning models. Recall is an important metric because missing a patient who is at risk of death is a costly error.

## Dataset

The dataset contains **17,542 patients** and the following features:

- Age
- Gender
- CRP
- D-Dimer
- Ferritin
- LDH
- Troponin
- IL-6
- WBC
- NLR

**Target variable:** `Death` — whether the patient died within 30 days.

The dataset contains approximately equal numbers of deaths and survivors.

## Data Preprocessing

The following preprocessing steps were performed:

- Encoded gender as Male = 1 and Female = 0.
- Handled missing values using median imputation for numerical features and mode imputation for gender.
- Treated impossible ages as missing values.
- Capped extreme numerical values at the 1st and 99th percentiles.
- Standardized features using `StandardScaler`.
- Split the data into training and test sets using an 80/20 stratified split.

## Machine Learning Models

The following models were evaluated:

- Logistic Regression
- Logistic Regression with an engineered age-over-80 feature
- Tuned Logistic Regression using `GridSearchCV`
- Gradient Boosting
- Random Forest

## Results

| Model | Accuracy | Recall | ROC-AUC |
|---|---:|---:|---:|
| Logistic Regression | 0.787 | 0.814 | 0.851 |
| Logistic Regression + Age Flag | 0.851 | 0.846 | 0.907 |
| Tuned Logistic Regression + Age Flag | 0.858 | 0.881 | 0.907 |
| Gradient Boosting | 0.918 | 0.993 | 0.946 |
| Random Forest | 0.919 | 0.998 | 0.961 |

The Random Forest achieved the highest ROC-AUC among the evaluated models. Adding an age-over-80 feature also substantially improved logistic regression performance.

## Key Findings

- Age was the strongest predictor of mortality in this dataset.
- NLR and D-Dimer were also associated with mortality.
- Feature engineering helped logistic regression capture a nonlinear age-related pattern.
- More flexible models achieved higher predictive performance than baseline logistic regression.
- Improving recall involved trade-offs with precision.

## Tools and Technologies

- Python
- Pandas
- NumPy
- Scikit-learn
- Matplotlib / Seaborn
- Jupyter Notebook
- Logistic Regression
- GridSearchCV
- Random Forest
- Gradient Boosting

## Limitations

The dataset appears to be simulated because of the unusually sharp mortality pattern around age 80. Results were evaluated on a single train/test split and have not been validated on an external hospital population.

**This project is for educational purposes only. It is not a clinically validated model and must not be used to make medical decisions.**

## Author

Created as a machine learning capstone project.
