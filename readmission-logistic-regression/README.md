# What Factors Are Associated With Readmission? (Logistic Regression)

Which factors are related to a patient being readmitted to the hospital within a month of release?

## Data

Hospital patient data (10,000 patients) provided by WGU. It isn't included here. To run the notebook, put `D208_medical_raw.csv` in a `data/` folder next to it.

## Approach

1. Checked for duplicates and nulls, and replaced outliers in three variables with the median.
2. Explored the target and all 12 predictors with univariate and bivariate plots.
3. Fit an initial logistic regression with all 12 predictors.
4. Reduced the model: removed predictors with a VIF over 10 one at a time, then used backward stepwise elimination until every p-value was under 0.05.
5. Evaluated the final model with a confusion matrix.

## Results

The final model kept two predictors: initial days in the hospital and additional charges.

- Pseudo R-squared: 0.926 (0.932 for the initial model)
- Accuracy: 97.8% (6,219 true negatives, 3,563 true positives, 112 false positives, 106 false negatives)

Each extra day of the initial stay raised the log odds of readmission by about 0.99.

## Tools

Python, pandas, statsmodels, seaborn, matplotlib
