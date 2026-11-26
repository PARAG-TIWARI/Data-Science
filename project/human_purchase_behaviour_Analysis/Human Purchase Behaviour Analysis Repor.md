# Human Purchase Behaviour Analysis — Report

**Author:** Parag Tiwari  
**Analysis notebook:** work1.ipynb  
**Dataset:** human_purchase_behaviour.csv

## 1. Executive summary

This exploratory analysis reviews **72,637 customer records** across two categorical attributes: life stage and premium-customer tier. It inspects the data structure, checks completeness, standardises the life-stage labels, counts customer records by segment, and visualises the relationship between life stage and premium tier.

The strongest directly recorded result is the distribution of customer records across seven life-stage categories. The notebook also creates a life-stage versus premium-tier cross-tabulation, but the saved output does not contain the underlying numeric table or normalised percentages. Those values should be calculated before making precise claims about which life stage is more likely to belong to a particular premium tier.

## 2. Objective and questions

The analysis explores:

1. How are the customer records distributed across life-stage categories?
2. What premium-customer tiers are represented?
3. How can the relationship between life stage and premium tier be visualised?
4. What additional information would be needed to support stronger business recommendations?

## 3. Dataset overview

The notebook loads a dataset with 72,637 rows and three columns.

| Field | Meaning |
|---|---|
| LYLTY_CARD_NBR | Customer or loyalty-card identifier |
| LIFESTAGE | Customer life-stage segment |
| PREMIUM_CUSTOMER | Budget, Mainstream, or Premium classification |

The notebook's info() output shows all 72,637 values present in each of the three fields. The identifier is an integer, while the two segment fields are categorical text.

## 4. Data preparation

The notebook performs the following steps:

1. Loads the CSV into a Pandas DataFrame.
2. Inspects sample records, shape, column names, data types, and descriptive statistics.
3. Checks for null values.
4. Renames LYLTY_CARD_NBR to Loyalty_card_id.
5. Sorts records by life stage and premium tier.
6. Converts life-stage labels to lowercase for consistent display.
7. Counts records by life-stage category.
8. Creates a cross-tabulation of life stage and premium tier.

The notebook calls a duplicate check, but it does not save a final duplicate-count result in the report. A reproducible duplicate-count output should be added before reporting a duplicate total.

## 5. Life-stage distribution

The recorded notebook output contains the following counts:

| Life-stage segment | Records |
|---|---:|
| Retirees | 14,805 |
| Older Singles/Couples | 14,609 |
| Young Singles/Couples | 14,441 |
| Older Families | 9,780 |
| Young Families | 9,178 |
| Midage Singles/Couples | 7,275 |
| New Families | 2,549 |
| **Total** | **72,637** |

Retirees are the largest group in the observed data, followed by Older Singles/Couples and Young Singles/Couples. New Families is the smallest group.

These counts describe the composition of this dataset. They should not automatically be interpreted as the population share of a wider customer base unless the sampling method supports that inference.

## 6. Premium-tier analysis

The dataset contains three premium-customer labels:

- Budget
- Mainstream
- Premium

The notebook uses a cross-tabulation to compare premium tier across life-stage groups and visualises the result.

The saved notebook does not contain a numeric cross-tab output or a normalised percentage table. The earlier approximate tier percentages and claims about premium preference should therefore be treated as unverified and are intentionally not repeated as findings here.

For a defensible comparison, calculate both:

- **Within-life-stage mix:** each premium tier as a percentage of its life-stage total.
- **Within-tier mix:** each life stage as a percentage of the premium-tier total.

The first answers, "What is the premium-tier mix inside each life stage?" The second answers, "What life stages make up each premium tier?"

## 7. Key observations

Based on the outputs currently retained in the notebook:

- The dataset contains seven life-stage categories.
- Retirees, Older Singles/Couples, and Young Singles/Couples are the three largest categories by record count.
- The premium-customer field has three categories: Budget, Mainstream, and Premium.
- A relationship between life stage and premium tier is explored visually, but the underlying numeric comparison needs to be exported before stronger segment conclusions are made.

## 8. Visualisations

The notebook creates:
- A life-stage frequency chart.
- A premium-tier distribution chart.
- A life-stage by premium-tier cross-tabulation chart.
- Additional exploratory plots of categorical fields.

For categorical comparisons, count plots and grouped/stacked bars are generally more informative than line or scatter plots of category labels. If category labels are encoded as numbers, those numbers should not be treated as continuous values.

## 9. Business interpretation and recommendations

The current data supports an initial customer-segmentation view, not a full purchasing or profitability analysis.

Possible next analyses include:

1. Compare premium-tier composition within each life stage using row-normalised percentages.
2. Investigate whether segment composition differs meaningfully from the overall customer distribution.
3. Join the segment table to authorised transaction data to study order frequency, average basket value, product mix, and retention.
4. Test targeted campaigns against a control group before claiming that a segment-specific offer improves conversion or revenue.

These are recommended next steps, not proven effects from the current three-column dataset.

## 10. Limitations

- The dataset does not include transaction amounts or revenue.
- It does not include product, quantity, or transaction-date fields.
- It cannot establish spending power, customer lifetime value, premium profitability, or purchase frequency.
- Exact premium-tier cross-tabulation values are not preserved in the notebook output.
- The duplicate check should be rerun and its numeric result recorded.
- The sample design and original data provenance should be documented before generalising beyond the dataset.

## 11. Reproducibility

Install the dependencies:

~~~bash
python -m pip install numpy pandas matplotlib jupyter
~~~

Run the notebook from the project folder:

~~~bash
jupyter notebook work1.ipynb
~~~

The notebook expects **human_purchase_behaviour.csv** to be available in the same working directory.

## 12. Conclusion

The project demonstrates a basic customer-segmentation workflow using Pandas and visualisation libraries. It records a clear distribution across seven life-stage categories and establishes a starting point for examining premium-tier composition.

The next improvement should be to export exact cross-tabulation counts and within-segment percentages. Transaction-level data would be required before making claims about spending, purchasing power, or commercial value.

---

[Project README](README.md) · [Notebook](work1.ipynb) · [Data Science portfolio](../../README.md)
