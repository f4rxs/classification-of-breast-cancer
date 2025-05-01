## Table of Contents
1. [Introduction](#introduction)
2. [Data Preparation](#data-preparation)
3. [Exploratory Data Analysis (EDA)](#exploratory-data-analysis-eda)
4. [Data Preprocessing](#data-preprocessing)
5. [Data Regularization](#data-regularization)
6. [Model Selection](#model-selection)
7. [Model Evaluation](#model-evaluation)
8. [Hyperparameter Tuning](#hyperparameter-tuning)
9. [Model Evaluation (Post-tuning)](#model-evaluation-post-tuning)
10. [Conclusion](#conclusion)

## Introduction
This study focuses on the classification of breast cancer tumors as malignant or benign using machine learning models. Breast cancer is one of the most prevalent cancers worldwide, and early and accurate diagnosis is crucial for effective treatment and improved patient outcomes.

The dataset used is the Breast Cancer Wisconsin dataset containing 569 samples (357 Benign, 212 Malignant), each with 30 numerical features describing characteristics of the cell nuclei. The target variable classifies tumors as Benign (B) or Malignant (M).

Dataset source: [UCI Machine Learning Repository](https://github.com/pkmklong/Breast-Cancer-Wisconsin-Diagnostic-DataSet/tree/master)

## Data Preparation
- Loaded from CSV file
- Checked for null values
- Dropped unnecessary columns (unnamed 32 and id)

## Exploratory Data Analysis (EDA)
The dataset contains 31 columns (1 target, 30 features). Key findings:
- No null values in any columns
- Features include various measurements of cell nuclei characteristics
- Target variable distribution: 357 Benign (0), 212 Malignant (1)

Statistical summary revealed distributions and correlations between features and target:

![Correlation Matrix](https://github.com/user-attachments/assets/a8cba770-fd04-4891-b0cf-3a976d88b884)


![Top Correlated Features](https://github.com/user-attachments/assets/92969118-5019-4971-b3bb-26c505a94175)
)

## Data Preprocessing
1. Declared target (diagnosis) and features
2. Selected top correlated features
3. Split data: 80% training, 20% testing
4. Applied Standard Scaling (mean=0, std=1)

## Data Regularization
Techniques used to prevent overfitting:
- **L1 (Lasso)**: Encourages sparsity by shrinking some coefficients to zero
- **L2 (Ridge)**: Penalizes large coefficients, reducing overfitting risk

## Model Selection
Trained and evaluated 5 classification models:
1. Lasso (L1)
2. Ridge (L2)
3. KNN
4. SVC
5. Random Forest

## Model Evaluation
| Model          | Accuracy | Precision | Recall | F1 Score |
|----------------|----------|-----------|--------|----------|
| Lasso (L1)     | 0.973684 | 0.973958  | 0.973684 | 0.973742 |
| Ridge (L2)     | 0.973684 | 0.973958  | 0.973684 | 0.973742 |
| KNN            | 0.973684 | 0.973958  | 0.973684 | 0.973742 |
| SVC            | 0.982456 | 0.982456  | 0.982456 | 0.982456 |
| Random Forest  | 0.956140 | 0.956088  | 0.956140 | 0.956036 |

**SVC emerged as the best performing model** with highest scores across all metrics (98.25% accuracy/precision/recall/F1).

## Hyperparameter Tuning
Used GridSearchCV and RandomizedSearchCV to optimize model performance. However, tuning negatively impacted performance:

| Model          | Before Tuning | After Tuning |
|----------------|---------------|--------------|
| Lasso (L1)     | 0.973684      | 0.641435     |
| Ridge (L2)     | 0.973684      | 0.702446     |
| KNN            | 0.973684      | 0.931868     |
| SVC            | 0.982456      | 0.936263     |
| Random Forest  | 0.956140      | 0.956043     |

## Conclusion
The **SVC model without tuning** is the best choice, providing the highest accuracy of 98.25%. 

