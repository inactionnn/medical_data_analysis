# Heart Cardiovascular Risk Analysis: A Visual Data Exploration

## Introduction

In this project, I explored a synthetic dataset of patients and cardiovascular risk factors. The data includes clinical measurements, lifestyle information, and final risk assessments. The goal was to understand which factors most strongly influence heart disease risk and build predictive models.

## Initial Data Overview

The dataset contains 17 columns and several thousand rows with no missing values. For each patient, we have age, blood pressure, cholesterol, stress levels, sleep quality, physical activity, and other parameters. Each record includes both a numerical risk score (0-100) and a risk category (Low, Medium, High).

## Target Variable Distribution

The numerical risk score is nearly uniformly distributed, which is good for model training. The risk categories are also relatively balanced, though Medium risk patients slightly outnumber Low and High risk groups.

<img width="1584" height="483" alt="image" src="https://github.com/user-attachments/assets/c9977fbf-6699-4083-855d-37a655a013d5" />



## Numerical Factors Analysis

To understand how each factor relates to risk, I divided patients into four groups based on risk quartiles and created box plots for all numerical features.

Age increases steadily across risk groups. Blood pressure, especially systolic, rises with risk. Cholesterol follows a similar pattern. Physical activity and daily steps decrease in high-risk patients. Stress levels increase, while sleep quality and diet quality show moderate decreases.

<img width="988" height="484" alt="image" src="https://github.com/user-attachments/assets/bfe26a3d-68f6-4184-96e5-3b925c4772a4" />



## Correlations

The correlation matrix reveals strongest associations with age, systolic blood pressure, and cholesterol. Surprisingly, BMI shows relatively weak correlation with risk. Physical activity shows moderate negative correlation, while stress shows positive correlation.

<img width="939" height="842" alt="image" src="https://github.com/user-attachments/assets/6ad5a6b4-a998-468c-9347-52ef95cd25a0" />



## Categorical Factors

Smoking status shows a clear pattern. Never smokers are predominantly low risk. Former smokers shift toward medium risk. Current smokers show predominantly high risk.

Family history also predicts higher risk categories.

<img width="1584" height="1184" alt="image" src="https://github.com/user-attachments/assets/540fe689-df9b-4a8f-bbb7-cf9ca889d319" />



## Regression Modeling

I tested several regression models to predict the numerical risk score: Linear Regression, Ridge, Lasso, Random Forest, and Gradient Boosting. Gradient Boosting performed best with an R² score around 0.85.

The predicted vs actual values plot shows points clustered near the diagonal line, indicating good model performance. Error distribution appears normal without significant bias.

<img width="1584" height="584" alt="image" src="https://github.com/user-attachments/assets/bcce76ec-adf7-485d-912a-d40e8a72b6be" />



## Classification Modeling

For classifying patients into risk categories, I tested Logistic Regression, Random Forest, and Gradient Boosting. Random Forest achieved the best accuracy at approximately 89%.

The confusion matrix shows the model rarely confuses Low and High risk, though it sometimes misclassifies between adjacent categories.

<img width="1584" height="584" alt="image" src="https://github.com/user-attachments/assets/219bed80-a980-4ffd-a893-da2798a842c4" />



## Feature Importance

Age emerges as the strongest predictor, followed by systolic blood pressure, cholesterol, and diastolic blood pressure. Physical activity and stress also rank highly. Smoking status appears in the top features but lower than expected, possibly because its effects are captured through other variables.


## Model Comparison

For regression, Gradient Boosting outperformed other models. For classification, Random Forest achieved the highest accuracy. Linear models struggled with the complexity of the data, while tree-based methods better captured non-linear relationships.

<img width="1777" height="584" alt="image" src="https://github.com/user-attachments/assets/00fe74c3-abc9-4c45-8cb8-743508d3c7d7" />


## Key Takeaways

Even in synthetic data, the analysis reveals patterns consistent with real cardiology: age and blood pressure are primary risk drivers, lifestyle factors matter significantly, and machine learning models effectively stratify cardiovascular risk. Future work with real data could explore interaction effects between risk factors.
