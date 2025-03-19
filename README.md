# Credit Risk Analysis

## Overview
This project focuses on predicting loan default risk using the LendingClub dataset. The dataset is highly imbalanced (98% defaults, 2% fully paid). I used a Random Forest model with SMOTE for handling class imbalance and achieved an F1-score of 0.89 for the minority class (fully paid loans).

## Dataset
- Source: LendingClub Loan Data from Kaggle.
- Features Used: `loan_amnt`, `int_rate`, `annual_inc`, `dti`, `delinq_2yrs`, `revol_bal`, `mort_acc`, etc.
- Target: `loan_status` (0 for Fully Paid, 1 for Default)

## Methodology
1. **Data Preprocessing:**
   - Handled missing values and outliers (e.g., removed top 1% of `annual_inc`).
   - Encoded categorical features like `grade`, `emp_length`, `home_ownership`.
2. **Class Imbalance Handling:**
   - Used SMOTE with `sampling_strategy=0.3` (3:1 majority:minority ratio).
   - Applied `class_weight='balanced'` in Random Forest.
3. **Model:**
   - Random Forest Classifier (`n_estimators=100`, `max_depth=5`).
4. **Evaluation:**
   - Accuracy: 99%
   - F1-score (minority class): 0.89
   - Precision (minority class): 0.80
   - Recall (minority class): 0.99

## Results
- **Confusion Matrix:**
  - True Negatives (0 predicted as 0): 203
  - False Positives (1 predicted as 0): 50
  - False Negatives (0 predicted as 1): 2
  - True Positives (1 predicted as 1): 8723
- **Classification Report:**
-                 precision    recall  f1-score   support
          0          0.80      0.99      0.89       205
          1          1.00      0.99      1.00      8773
      accuracy                           0.99      8978
      macro avg        0.90      0.99    0.94      8978
      weighted avg     1.00      0.99    0.99      8978
