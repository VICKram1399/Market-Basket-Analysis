
# Market Basket Analysis of Online Retail Transactions
This project applies Market Basket Analysis (MBA) to uncover associations between products purchased together in an online retail store. The goal is to identify patterns that can inform product recommendations, store layout optimization, and marketing strategies.

## Dataset:
The analysis is based on the "Online Retail" dataset from Kaggle, which contains transactional data for a UK-based online retail store from December 1st, 2010 to December 9th, 2011. The dataset includes information on invoice numbers, stock codes, item descriptions, quantities, invoice dates, unit prices, customer IDs, and countries.
### Dataset Link:- https://www.kaggle.com/datasets/carrie1/ecommerce-data

## Project Overview
### Data Collection and Preparation:

* Loaded and cleaned the dataset (removing missing values, cancellations, etc.).
* Filtered for transactions from France.
* Transformed the data into a format suitable for MBA, representing each transaction as a binary vector of item presence (1) or absence (0).

### Frequent Itemset Mining (Apriori):

* Used the Apriori algorithm to identify frequent itemsets (sets of products purchased together) that meet a minimum support threshold of 7%.
  
### Association Rule Generation:

* Generated association rules (of the form "If A, then B") from the frequent itemsets, using the "lift" metric to measure the strength of association (minimum threshold of 1).

### Rule Evaluation and Filtering:

* Sorted rules by confidence (descending order) and filtered by a minimum confidence of 0.5 and lift of 1 to retain the most relevant rules.
### Cross-Validation:

* Performed 5-fold cross-validation to assess the model's generalization performance and ensure the discovered rules are not due to overfitting.

## Key Outcomes:-

| Metric                  | Average Value | Interpretation                                                                                                                        |
|-------------------------|---------------|---------------------------------------------------------------------------------------------------------------------------|
| Average Support         | 0.1045        | Itemsets in the discovered rules appear together in roughly 10.45% of transactions, indicating they are not rare but not overly common either. |
| Average Confidence      | 0.7416        | When the antecedent itemset is present, there's a 74.16% chance of also finding the consequent itemset, suggesting good predictive power. |
| Average Lift            | 3.4430        | Items in the rules are 3.44 times more likely to be purchased together than by random chance, indicating strong associations.            |
| Average Number of Rules | 26.00         | The model finds an average of 26 rules per fold, suggesting a good number of potentially interesting relationships in the data.        |

## Insights and Recommendations
* High-Confidence Rules: The analysis revealed several high-confidence association rules, indicating strong relationships between certain product combinations. These rules can be used to:

  * Recommend Products: Suggest items from the consequent set when a customer adds an item from the antecedent set to their cart.
  * Store Layout: Place associated items near each other to encourage impulse purchases.
  * Promotional Bundles: Offer discounts or special deals on product combinations identified by the rules.
  
* Moderately Frequent Patterns: The average support of 10.45% suggests that the discovered patterns are not overly niche, but frequent enough to be relevant for a significant portion of customers.
* Strong Lift: The high average lift value of 3.44 reinforces the idea that the associations are meaningful and not just due to chance.

## Conclusion
* This market basket analysis provides valuable insights into the purchasing behavior of French customers in this online retail store. The discovered association rules can be leveraged to enhance customer experience, increase sales, and optimize various aspects of the business.

## Code:
* The code for this analysis is available in the market_basket_analysis.ipynb Jupyter Notebook in this repository. Feel free to explore the code and visualizations to dive deeper into the findings.

## Future Directions:

* Analyze customer segments separately to tailor recommendations more precisely.
* Explore time-based patterns to identify seasonal or event-driven associations.
* Experiment with different algorithms or support/confidence thresholds.
  



