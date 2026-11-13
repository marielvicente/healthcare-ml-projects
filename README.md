# Healthcare ML Projects

Projects from my MS in Data Analytics at Western Governors University. Most of them use healthcare data, which is also what I work with day to day.

Each folder is one project with its own README covering the question, the approach, and the results.

## Featured projects

| Project | What it does | Tools |
|---|---|---|
| [Predicting panic disorder (capstone)](capstone-panic-disorder-random-forest/) | Random forest classifier on 120,000 patient records to predict a panic disorder diagnosis | Python, scikit-learn |
| [Forecasting hospital revenue](time-series-revenue-forecasting/) | ARIMA model on two years of daily revenue, tested against held-out data | Python, statsmodels, pmdarima |
| [Sentiment analysis of customer reviews](sentiment-analysis-nlp/) | Neural network that classifies Amazon, IMDb, and Yelp reviews as positive or negative | Python, TensorFlow, NLTK |

## More coursework

- [Predicting hospital readmission with KNN](hospital-readmission-knn/) (R)
- [What's associated with readmission: logistic regression](readmission-logistic-regression/) (Python)
- [Grouping patients with k-means clustering](patient-clustering-kmeans/) (Python)
- [Which medications are prescribed together: market basket analysis](market-basket-prescriptions/) (Python)

## Skills covered

- **Languages:** Python, R
- **Modeling:** logistic regression, KNN, random forest, k-means, market basket analysis, ARIMA, neural networks
- **Data prep:** cleaning, outlier checks, encoding, scaling, text preprocessing
- **Libraries:** pandas, scikit-learn, statsmodels, TensorFlow/Keras, NLTK, mlxtend, seaborn, caret

## Running the code

The datasets aren't included. Most were provided by WGU and aren't mine to share, and the rest are public (linked in each project's README). Each notebook or script expects its data file in a `data/` folder next to it.

Python packages are listed in `requirements.txt`:

```
pip install -r requirements.txt
```

The R script uses readr, dplyr, ggplot2, corrr, caret, class, and pROC.
