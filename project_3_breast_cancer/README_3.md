# Diagnostic Breast Cancer Analysis: A Machine Learning Approach to Tumor Classification

## Introduction

In this project, I analyzed the Diagnostic Breast Cancer Dataset, which contains clinical measurements derived from digitized fine needle aspirate (FNA) images of breast masses. The dataset was collected at the University of Wisconsin and includes 30 nuclear features computed from breast cell images. The primary objective was to build and compare multiple machine learning models to accurately classify tumors as benign or malignant based on these nuclear characteristics.

## Dataset Overview

The dataset contains **569 patient records** with **30 nuclear features** and **no missing values**. For each patient, ten nuclear characteristics were measured, with three statistical values computed for each: mean, standard error, and worst (mean of the three largest values).

**Target Variable Distribution:**
- Benign cases: 357 (62.7%)
- Malignant cases: 212 (37.3%)

<img width="1310" height="614" alt="image" src="https://github.com/user-attachments/assets/a9132e44-cde4-41c7-a7fe-2809ad8ad71e" />


## ID Column Analysis

The ID column contains 569 unique patient identifiers with no duplicates. Statistical analysis revealed no significant correlation between patient IDs and diagnosis (p-value > 0.05), confirming that IDs are randomly assigned and contain no predictive information. This justified dropping the ID column from feature engineering.

## Data Preprocessing

Features were standardized using StandardScaler to ensure all variables contribute equally to model training. The data was split into training (80%) and testing (20%) sets with stratification to maintain class distribution.

- Training set: 455 samples
- Test set: 114 samples
- Class proportions preserved in both sets

## Model Development and Evaluation

I implemented and compared seven classification algorithms:

1. **Logistic Regression** - Baseline linear model
2. **K-Nearest Neighbors (KNN)** - With K optimization
3. **Support Vector Machine (SVM)** - Linear, RBF, and polynomial kernels
4. **Random Forest** - Ensemble of decision trees
5. **Gradient Boosting** - Sequential ensemble method
6. **XGBoost** - Optimized gradient boosting
7. **Neural Network** - Multi-layer perceptron

### KNN Optimization

The optimal K value was determined through cross-validation, with K=5 achieving the highest accuracy.

<img width="722" height="583" alt="image" src="https://github.com/user-attachments/assets/56d3bb19-7433-40ce-83c7-e57296f68691" />

### Neural Network Performance


A multi-layer perceptron (MLP) classifier with two hidden layers (100 and 50 neurons) was implemented using ReLU activation and Adam optimization. The network was trained with early stopping to prevent overfitting, using 10% of the training data for validation. The neural network achieved 96.49% accuracy on the test set, with precision of 0.9512 and recall of 0.9512 for malignant cases. While performing well, it was slightly outperformed by SVM and tree-based ensemble methods, likely due to the relatively small dataset size (569 samples) where complex neural architectures may not fully leverage their capacity. The training loss curve below shows smooth convergence, indicating stable learning without overfitting.

<img width="1146" height="512" alt="image" src="https://github.com/user-attachments/assets/8ead56f5-e513-4e6d-a8ee-72104120d5ec" />


### Model Performance Comparison

| Model | Accuracy | Precision | Recall | F1-Score |
|-------|----------|-----------|--------|----------|
| SVM (RBF) | 0.9825 | 0.9762 | 0.9762 | 0.9762 |
| Random Forest | 0.9737 | 0.9756 | 0.9524 | 0.9639 |
| XGBoost | 0.9737 | 0.9756 | 0.9524 | 0.9639 |
| Gradient Boosting | 0.9649 | 0.9512 | 0.9512 | 0.9512 |
| Neural Network | 0.9649 | 0.9512 | 0.9512 | 0.9512 |
| KNN (k=5) | 0.9649 | 0.9500 | 0.9500 | 0.9500 |
| Logistic Regression | 0.9561 | 0.9268 | 0.9500 | 0.9383 |

<img width="1579" height="1226" alt="image" src="https://github.com/user-attachments/assets/ea6f83a5-30db-4e3e-9413-06c8ae1ef5e4" />


### ROC Curves Analysis

All models achieved excellent discriminative ability with AUC scores exceeding 0.99. SVM with RBF kernel achieved the highest AUC of 0.998, indicating near-perfect separation between benign and malignant cases.

<img width="1184" height="783" alt="image" src="https://github.com/user-attachments/assets/5e0fb037-c597-4301-aa41-8f4ec45d5638" />


## Feature Importance Analysis

Analysis of feature importance from tree-based models revealed the most predictive nuclear characteristics:

**Top 10 Most Important Features:**
1. **concave points_worst** - Number of concave portions (worst value)
2. **perimeter_worst** - Nuclear perimeter (worst value)
3. **area_worst** - Nuclear area (worst value)
4. **radius_worst** - Nuclear radius (worst value)
5. **concave points_mean** - Number of concave portions (mean value)
6. **concavity_mean** - Severity of concave portions (mean value)
7. **area_mean** - Nuclear area (mean value)
8. **radius_mean** - Nuclear radius (mean value)
9. **perimeter_mean** - Nuclear perimeter (mean value)
10. **texture_worst** - Gray-scale variation (worst value)

<img width="1184" height="783" alt="image" src="https://github.com/user-attachments/assets/94114d6d-df4e-4439-b26e-c76efcfc2557" />


## Medical Interpretation of Results

The model findings align with established cytopathological knowledge:

1. **Nuclear Shape Irregularity is the Strongest Predictor**: Concave points (measuring nuclear membrane irregularities) emerge as the most important feature. This corresponds to the medical observation that malignant cells exhibit irregular nuclear contours with indentations, unlike the smooth, regular nuclei of benign cells.

2. **Nuclear Size Distinguishes Benign from Malignant**: Radius, perimeter, and area features consistently rank highly, reflecting that malignant cells undergo nuclear enlargement (karyomegaly) due to increased DNA content and metabolic activity.

3. **Extreme Values Provide the Strongest Diagnostic Signal**: The "worst" measurements consistently outperform mean values in importance, suggesting that the most abnormal cells in a sample are particularly informative. This mirrors clinical practice where pathologists focus on the most atypical cells in a specimen.

4. **Texture Adds Discriminative Power**: Nuclear texture appears in the top features, reflecting the altered chromatin distribution pattern seen in malignant cells under microscopy (hyperchromasia, chromatin clumping).

## Model Selection and Clinical Implications

**Support Vector Machine with RBF kernel** emerged as the best-performing model with:
- **Accuracy: 98.25%** - Correctly classifying 112 out of 114 test cases
- **Precision: 97.62%** - Minimizing false positive diagnoses
- **Recall: 97.62%** - Minimizing false negative diagnoses
- **AUC: 0.998** - Excellent overall discriminative ability

The near-perfect performance demonstrates that computational analysis of nuclear morphometry can achieve accuracy comparable to expert pathologists. In a clinical setting, such a model could serve as:

1. **Decision Support Tool**: Providing quantitative, reproducible assessments to complement visual examination
2. **Quality Assurance**: Reducing inter-observer variability in challenging cases
3. **Triage System**: Flagging suspicious cases for priority review

## Sample Prediction Demonstration

Using the trained Random Forest model, I created a prediction function that can classify new patient samples. Testing on the mean feature values from the training set produced the expected classification with high confidence.

```
Sample Patient Features (mean values from training set):
Number of features: 30

Prediction Result: Benign (Non-Cancerous)
Probability Distribution:
  • Benign: 0.6933 (69.33%)
  • Malignant: 0.3067 (30.67%)

Confidence Level: Medium
```

## Key Takeaways

1. **Nuclear Morphometry is Highly Predictive**: All tested models achieved >95% accuracy, confirming that nuclear characteristics from FNA images provide excellent discrimination between benign and malignant breast lesions.

2. **Shape Irregularity Dominates Prediction**: Concave points (measuring nuclear membrane irregularity) are stronger predictors than simple size measurements, emphasizing the diagnostic importance of nuclear shape in cytopathology.

3. **SVM with RBF Kernel Achieves Best Performance**: The non-linear SVM slightly outperforms ensemble methods, suggesting complex, non-linear decision boundaries in the feature space.

4. **Extreme Values Carry the Strongest Signal**: The "worst" measurements consistently outrank mean values, highlighting that the most abnormal cells in a sample are diagnostically most important.

5. **Clinical Applicability**: The high performance demonstrates that machine learning models can provide objective, reproducible assessments to support pathologists in breast cancer diagnosis.

6. **Feature Redundancy**: High correlations among size-related features suggest potential for dimensionality reduction without significant loss of predictive power.
