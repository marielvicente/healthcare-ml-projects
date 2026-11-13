# Predicting Hospital Readmission With KNN

Can k-nearest neighbors predict which patients will be readmitted to the hospital?

## Data

Hospital patient data (10,000 patients) provided by WGU. It isn't included here. To run the script, put `D209_medical_raw.csv` in a `data/` folder next to it.

## Approach

1. Checked for duplicates, nulls, and outliers.
2. Started with 12 numeric predictors (age, income, length of stay, charges, and others). Dropped total charge because it was highly correlated with initial days (over my 0.75 threshold).
3. Min-max normalized the predictors, since KNN is distance-based.
4. Split 80/20 and fit two models, k = 89 and k = 90 (the square root of the training set size was 89.4).
5. Evaluated with a confusion matrix, accuracy, and ROC/AUC.

## Results

- Accuracy: 0.90 for both models
- AUC: close to 1
- No false negatives in the confusion matrix, but there were false positives

Next I'd try including more of the variables to see if that cuts down the false positives.

## Tools

R, caret, class, pROC, dplyr, corrr, ggplot2
