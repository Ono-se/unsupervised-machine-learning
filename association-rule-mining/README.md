# Market Basket Analysis with Apriori

## Overview
A market basket analysis project using the Apriori algorithm to identify grocery items that are frequently purchased together, based on real member-level transaction data.

## Objective
The goal is to discover meaningful purchasing patterns and generate association rules that could support:

* Product recommendations
* Cross-selling
* Store product placement

## Dataset
The project uses the [Groceries Dataset](https://www.kaggle.com/datasets/heeraldedhia/groceries-dataset) from Kaggle, containing 38,765 purchase records with `Member_number`, `Date`, and `itemDescription` columns.

Grouping purchases by member and date produces **14,963 individual shopping baskets**, which form the transactions used for the analysis. Basket size ranges from 2 to 11 items, averaging about 2.6 items per trip.

## Approach

1. **Data preparation** — group raw purchase records by `Member_number` and `Date` to reconstruct individual shopping baskets, and derive basket size / unique item counts.
2. **Exploratory data analysis** — examine basket size distribution, average basket size and shopping frequency per member, and the top-selling items (whole milk, other vegetables, and rolls/buns lead the list).
3. **Transaction encoding** — convert baskets into a one-hot encoded item matrix suitable for Apriori.
4. **Frequent itemset mining** — apply the Apriori algorithm (via `mlxtend`) with a minimum support of 0.001.
5. **Association rule generation** — derive rules from the frequent itemsets using lift as the evaluation metric (minimum threshold of 1.0), then rank by lift to surface the strongest associations.

Rules are evaluated using:
* **Support** — how frequently an itemset occurs
* **Confidence** — how often the consequent occurs when the antecedent is present
* **Lift** — the strength of the association between items, relative to chance

## Tools
Python · Pandas · NumPy · Matplotlib · Seaborn · mlxtend · Jupyter Notebook

## Key Results
The mining process produced 240 association rules (lift ≥ 1.0). The strongest patterns identified include:

* Customers who buy **sausage** are ~2.2x more likely to also buy **whole milk and yogurt**.
* Customers who buy **whole milk and yogurt** are ~2.2x more likely to also buy **sausage**.
* Customers who buy **whole milk and sausage** are ~1.9x more likely to also buy **yogurt**.
* A notable association also appears between **citrus fruit** and **specialty chocolate**.

These patterns highlight strong cross-category purchasing behavior around staple items (milk, yogurt, sausage) that could inform recommendation systems, bundle promotions, or shelf placement decisions.
