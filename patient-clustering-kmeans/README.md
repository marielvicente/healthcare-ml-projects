# Grouping Patients With K-Means Clustering

Can patients with similar characteristics be grouped together using k-means?

## Data

Hospital patient data (10,000 patients) provided by WGU. It isn't included here. To run the notebook, put `D212_medical_raw.csv` in a `data/` folder next to it.

## Approach

1. Picked two continuous variables: income and total charge.
2. Checked for duplicates, nulls, and outliers. Kept the 274 incomes over $110,000, since they're valid values and income is one of the two clustering variables.
3. Standardized both variables with `StandardScaler`.
4. Fit k-means with k = 3, then checked that choice with an elbow plot (WCSS) and silhouette scores for k = 2 through 10.
5. Compared gender, age, income, and charges across the clusters.

## Results

The silhouette plot pointed to k = 3, with a silhouette score of 0.52.

| Cluster | Patients | Median income | Median total charge |
|---|---|---|---|
| 0: lower income, lower charges | 4,219 | $28,692 | $3,172 |
| 1: lower income, higher charges | 4,240 | $29,178 | $7,507 |
| 2: higher income | 1,541 | $85,141 | $4,487 |

Age and gender looked about the same in every cluster.

This only uses two of the dataset's variables, so there may be better groupings with others.

## Tools

Python, pandas, scikit-learn, seaborn, matplotlib
