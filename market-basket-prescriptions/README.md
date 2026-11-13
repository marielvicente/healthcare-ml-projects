# Which Medications Are Prescribed Together? (Market Basket Analysis)

Market basket analysis is usually used on shopping carts. Here it's applied to prescriptions, to find medications that are prescribed together more often than you'd expect.

## Data

Patient prescription data provided by WGU: 7,501 patients and 119 different medications, with up to 20 prescriptions per patient. It isn't included here. To run the notebook, put `D212_MBA_med_raw.csv` in a `data/` folder next to it.

## Approach

1. Removed the empty rows and converted each patient's prescriptions into a list.
2. One-hot encoded the lists with `TransactionEncoder` (one column per medication).
3. Ran the Apriori algorithm with a minimum support of 0.02.
4. Built the association rules table and ranked the rules by lift, support, and confidence.

## Results

Top three rules by lift:

| If prescribed | Also prescribed | Lift | Support |
|---|---|---|---|
| Carvedilol | Lisinopril | 2.29 | 3.9% |
| Lisinopril | Carvedilol | 2.29 | 3.9% |
| Glipizide | Carvedilol | 2.00 | 2.3% |

Patients prescribed carvedilol were 2.29 times more likely to also be prescribed lisinopril. Pairings like these could point to conditions that tend to show up together.

## Tools

Python, pandas, mlxtend, matplotlib
