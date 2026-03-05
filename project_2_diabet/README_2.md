# Diabetes Risk Prediction: A Comprehensive Data Analysis

## Introduction

In this project, I analyzed the Pima Indians Diabetes Dataset, which contains medical diagnostic measurements for 768 female patients. The goal was to identify key factors associated with diabetes and build predictive models to classify patients based on their diabetes status. This dataset is widely used in healthcare analytics and provides an excellent opportunity to practice data preprocessing, exploratory analysis, and machine learning techniques.

## Initial Data Overview

The dataset contains 768 records with 8 medical predictor variables and one binary outcome variable indicating diabetes presence (1) or absence (0). The features include glucose level, blood pressure, skin thickness, insulin level, BMI, diabetes pedigree function (family history), and age. Initial inspection revealed no missing values, but further analysis showed physiologically impossible zero values in several medical measurements.

## Data Quality and Preprocessing

Examination of the data revealed zero values in clinically relevant columns where zero is not physiologically possible. Glucose, BloodPressure, SkinThickness, Insulin, and BMI all contained zeros that likely represent missing or unrecorded data. These values were replaced with column medians to maintain data integrity while preserving the dataset size.

<img width="1484" height="1226" alt="image" src="https://github.com/user-attachments/assets/0c748417-13d5-4802-b156-a8a89df5f4dd" />

## Target Variable Distribution

The outcome variable shows moderate class imbalance. Approximately 65% of patients do not have diabetes, while 35% have diabetes. This imbalance is manageable and was addressed through stratified sampling during train-test splitting to maintain representative proportions.

<img width="1014" height="710" alt="image" src="https://github.com/user-attachments/assets/aec8beaa-4f8b-4020-beb5-5ab40004f24c" />


## Feature Relationships Analysis

To understand how each medical measurement relates to diabetes status, I created box plots comparing feature distributions between diabetic and non-diabetic patients. Glucose shows the most dramatic separation, with diabetic patients having consistently higher levels. BMI and Age also show clear differences, with diabetic patients trending toward higher values.

<img width="1484" height="1532" alt="image" src="https://github.com/user-attachments/assets/31b15b39-3a68-4d91-b10d-c18e5d1bcf0d" />


## Correlation Analysis

The correlation matrix reveals strongest associations with diabetes for Glucose (0.49), followed by BMI (0.29) and Age (0.24). Interestingly, Blood Pressure shows relatively weak correlation with the outcome. The diabetes pedigree function (family history) shows moderate correlation, confirming genetic factors play a role.

<img width="975" height="885" alt="image" src="https://github.com/user-attachments/assets/c6310950-e410-49f4-a0a4-7579e675b236" />


## Key Feature Interactions

The pairplot of Glucose, BMI, Age, and Insulin colored by diabetes status reveals important patterns. The glucose-BMI interaction shows clustering, with diabetic patients concentrated in regions of high glucose regardless of BMI. Age interacts with both glucose and BMI, showing older patients with elevated measurements are most likely to be diabetic.

<img width="1081" height="1021" alt="image" src="https://github.com/user-attachments/assets/714995fa-e8c3-4135-be1b-547584e2b8b1" />


## Model Performance Comparison

I evaluated four machine learning models: Logistic Regression, Random Forest, Gradient Boosting, and Support Vector Machine. Each model was trained on standardized features with 5-fold cross-validation. Gradient Boosting and Random Forest achieved the highest accuracies, demonstrating the value of ensemble methods for this healthcare prediction task.

<img width="1021" height="688" alt="image" src="https://github.com/user-attachments/assets/79a586ba-19df-4184-812c-09a04ed3cf35" />


## Best Model Performance

For the best-performing model (Gradient Boosting), I conducted hyperparameter tuning to optimize performance. The tuned model achieved approximately 78% test accuracy with an ROC-AUC score of 0.84, indicating good discriminative ability between diabetic and non-diabetic patients.

The confusion matrix shows the model correctly identifies most non-diabetic patients but has moderate success with diabetic patients, reflecting the class imbalance and inherent difficulty of the prediction task.


## Feature Importance Analysis

Random Forest feature importance reveals Glucose as the dominant predictor, accounting for nearly 40% of the model's predictive power. BMI and Age follow as the next most important features, confirming the clinical understanding that these are key diabetes risk factors. Insulin and Skin Thickness contribute least to predictions, possibly due to data quality issues or weaker direct relationships with diabetes onset.

<img width="1183" height="784" alt="image" src="https://github.com/user-attachments/assets/1990cb5c-ff52-4146-8851-e94ff038581a" />


## Model Comparison Summary

| Model | Test Accuracy | ROC-AUC Score | Key Strengths |
|-------|--------------|---------------|---------------|
| Logistic Regression | 0.77 | 0.83 | Interpretability, fast training |
| Random Forest | 0.78 | 0.84 | Handles non-linear relationships |
| Gradient Boosting | 0.78 | 0.84 | Best overall performance after tuning |
| SVM | 0.76 | 0.82 | Effective with clear margin separation |

## Key Takeaways

1. **Glucose is the strongest predictor** of diabetes in this dataset, confirming its central role in diabetes diagnosis and screening.

2. **BMI and Age are significant secondary factors**, supporting the clinical understanding that obesity and aging are major diabetes risk factors.

3. **Data quality matters**: Handling zero values in medical measurements was crucial for building reliable models.

4. **Ensemble methods outperform simpler models** for this classification task, capturing complex interactions between risk factors.

5. **The models achieve good but not perfect performance**, reflecting the multifactorial nature of diabetes and limitations of available measurements.
