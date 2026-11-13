# Predicting Panic Disorder With Random Forest (Capstone)

My MS in Data Analytics capstone. The question: can a random forest model predict whether a person has a panic disorder diagnosis?

## Data

[Panic Disorder Detection Dataset](https://www.kaggle.com/datasets/muhammadshahidazeem/panic-disorder-detection-dataset/data) from Kaggle. 120,000 rows and 17 columns covering demographics, symptoms, severity, stressors, history, coping mechanisms, and lifestyle factors. About 4.3% of people in the data have a panic disorder diagnosis (5,120 after cleaning).

The data isn't included here. To run the notebook, download both CSVs from Kaggle and put them in a `data/` folder next to it.

## Approach

1. Combined the training and testing files, dropped the ID column and two history fields I couldn't interpret without a data dictionary, and removed 187 duplicates (119,813 rows left).
2. Explored each variable with a histogram or bar chart, then compared each predictor against the diagnosis using crosstabs.
3. Encoded ordinal variables as numbers and one-hot encoded the rest (32 columns total).
4. Split 80/20 and tuned a random forest with `RandomizedSearchCV` (16 combinations, 5-fold cross-validation).
5. Evaluated on the test set with accuracy, MSE, RMSE, MAE, and R-squared, plus a confusion matrix and classification report since the diagnosis is rare. Then plotted the most important features.

## What the data showed

People with a panic disorder diagnosis were more likely to have high current stressors, panic attacks as a symptom, a severity rating of severe, a significant impact on life, and low social support. They were less likely to use exercise as a coping mechanism.

## Results

On the test set (23,963 people, 1,017 with a diagnosis):

- Accuracy: 98.1%
- Recall: 86% (the model caught 871 of the 1,017 people with a diagnosis)
- Precision: 74% (about 1 in 4 people it flagged didn't have a diagnosis)
- MSE: 0.019, under the 0.25 threshold I set in my hypothesis

Accuracy alone is misleading here. Only about 4% of the data has a positive diagnosis, so a model that always predicted no diagnosis would still be about 96% accurate. That's why recall and precision matter more.

The most important features in the model were sleep quality as a lifestyle factor, current stressors, impact on life, and severity. That lines up with what the crosstabs showed.

## What I'd do next

Tune the model to cut down on false positives, for example by adjusting the classification threshold or using class weights. I think this would work best as a screening tool, where people flagged by the model get a follow-up assessment.

## Tools

Python, pandas, NumPy, scikit-learn, seaborn, matplotlib
