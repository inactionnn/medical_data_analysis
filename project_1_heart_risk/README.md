# Heart Cardiovascular Risk Analysis: A Visual Data Exploration

## Introduction

In this project, I explored a synthetic dataset of patients and cardiovascular risk factors. The data includes clinical measurements, lifestyle information, and final risk assessments. The goal was to understand which factors most strongly influence heart disease risk and build predictive models.

## Initial Data Overview

The dataset contains 17 columns and several thousand rows with no missing values. For each patient, we have age, blood pressure, cholesterol, stress levels, sleep quality, physical activity, and other parameters. Each record includes both a numerical risk score (0-100) and a risk category (Low, Medium, High).

## Target Variable Distribution

The numerical risk score is nearly uniformly distributed, which is good for model training. The risk categories are also relatively balanced, though Medium risk patients slightly outnumber Low and High risk groups.

<img width="1584" height="483" alt="image" src="https://github.com/user-attachments/assets/4d619fcf-6888-47a5-840d-167b9231b914" />


## Numerical Factors Analysis

To understand how each factor relates to risk, I divided patients into four groups based on risk quartiles and created box plots for all numerical features.

Age increases steadily across risk groups. Blood pressure, especially systolic, rises with risk. Cholesterol follows a similar pattern. Physical activity and daily steps decrease in high-risk patients. Stress levels increase, while sleep quality and diet quality show moderate decreases.

*[Insert figure: 12 small box plots showing each numerical factor across risk quartiles]*

## Correlations

The correlation matrix reveals strongest associations with age, systolic blood pressure, and cholesterol. Surprisingly, BMI shows relatively weak correlation with risk. Physical activity shows moderate negative correlation, while stress shows positive correlation.

*[Insert figure: Heatmap of correlation matrix for all numerical features]*

## Categorical Factors

Smoking status shows a clear pattern. Never smokers are predominantly low risk. Former smokers shift toward medium risk. Current smokers show predominantly high risk.

Family history also predicts higher risk categories.

*[Insert figure: Two stacked bar charts - one for smoking status, one for family history]*

## Regression Modeling

I tested several regression models to predict the numerical risk score: Linear Regression, Ridge, Lasso, Random Forest, and Gradient Boosting. Gradient Boosting performed best with an R² score around 0.85.

The predicted vs actual values plot shows points clustered near the diagonal line, indicating good model performance. Error distribution appears normal without significant bias.

*[Insert figure: Scatter plot of predicted vs actual values with residual histogram]*

## Classification Modeling

For classifying patients into risk categories, I tested Logistic Regression, Random Forest, and Gradient Boosting. Random Forest achieved the best accuracy at approximately 89%.

The confusion matrix shows the model rarely confuses Low and High risk, though it sometimes misclassifies between adjacent categories.

*[Insert figure: Confusion matrix for the best classification model]*

## Feature Importance

Age emerges as the strongest predictor, followed by systolic blood pressure, cholesterol, and diastolic blood pressure. Physical activity and stress also rank highly. Smoking status appears in the top features but lower than expected, possibly because its effects are captured through other variables.

*[Insert figure: Horizontal bar chart of feature importance from the best model]*

## Model Comparison

For regression, Gradient Boosting outperformed other models. For classification, Random Forest achieved the highest accuracy. Linear models struggled with the complexity of the data, while tree-based methods better captured non-linear relationships.

*[Insert figure: Comparison charts for regression and classification models]*

## Key Takeaways

Even in synthetic data, the analysis reveals patterns consistent with real cardiology: age and blood pressure are primary risk drivers, lifestyle factors matter significantly, and machine learning models effectively stratify cardiovascular risk. Future work with real data could explore interaction effects between risk factors.
