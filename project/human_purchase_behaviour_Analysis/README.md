# Human Purchase Behaviour Analysis

An exploratory customer-segmentation analysis using life-stage and premium-customer categories.

**Author:** Parag Tiwari  
**Notebook:** [work1.ipynb](work1.ipynb)  
**Detailed report:** [Human Purchase Behaviour Analysis Report](Human%20Purchase%20Behaviour%20Analysis%20Repor.md)  
**Transaction-linked follow-up analysis:** [QVI Customer & Transaction Analysis](../../pandas/README.md)  
**Parent portfolio:** [Data Science repository](https://github.com/PARAG-TIWARI/Data-Science)

## 1. Project overview

This project examines how customer records are distributed across two categorical dimensions:

- **LIFESTAGE:** the customer's life-stage segment.
- **PREMIUM_CUSTOMER:** Budget, Mainstream, or Premium.

The analysis focuses on data inspection, basic cleaning, category counts, and visual comparison of customer segments. This particular customer-profile CSV has no transaction amount, product, or purchase-date fields. A separate notebook in the parent repository joins customer profiles to transaction data for a broader sales analysis.

## 2. Dataset profile

The notebook reports the following dataset shape and schema:

| Measure | Value |
|---|---:|
| Rows | 72,637 |
| Columns | 3 |
| Missing values shown by info() | 0 |
| Memory usage shown by info() | Approximately 1.7 MB |

| Column | Description |
|---|---|
| LYLTY_CARD_NBR | Customer/loyalty card identifier |
| LIFESTAGE | Customer life-stage category |
| PREMIUM_CUSTOMER | Budget, Mainstream, or Premium segment |

The notebook renames LYLTY_CARD_NBR to Loyalty_card_id and converts LIFESTAGE labels to lowercase for consistency.

## 3. Analytical workflow

~~~mermaid
flowchart TD
    A[Load customer segment CSV] --> B[Inspect shape, types and nulls]
    B --> C[Rename identifier column]
    C --> D[Standardise life-stage labels]
    D --> E[Count records by life stage]
    E --> F[Compare life stage and premium tier]
    F --> G[Create distribution charts]
    G --> H[Document insights and follow-up questions]
~~~

## 4. Life-stage distribution

The notebook's recorded value counts show:

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

The largest groups in this dataset are Retirees, Older Singles/Couples, and Young Singles/Couples. New Families is the smallest of the listed groups.

## 5. Premium-customer comparison

The notebook includes a cross-tabulation of LIFESTAGE against PREMIUM_CUSTOMER and plots the result as a grouped chart. This is the appropriate starting point for examining how premium tiers vary across life stages.

The current notebook does not preserve a numeric cross-tabulation or row-normalised percentage table in its saved outputs. For that reason, this README does not repeat the approximate premium-tier percentages or claim that one life stage has the strongest premium preference.

A stronger next step is to calculate:
- The record count for each life-stage and premium-tier combination.
- The percentage distribution within each life-stage group.
- The percentage distribution within each premium tier.

This would distinguish segment size from the relative mix inside each segment.

## 6. Visualisation approach

The notebook explores:
- Life-stage frequency counts.
- Premium-tier distribution.
- A life-stage versus premium-tier cross-tabulation.
- Bar, pie, histogram, and exploratory scatter/line plots.

The most interpretable comparisons for categorical data are frequency bars and a grouped or stacked bar chart. Numeric category codes should not be treated as continuous measurements.

## 7. Technology stack

| Area | Tools |
|---|---|
| Language | Python |
| Data manipulation | Pandas, NumPy |
| Visualisation | Matplotlib |
| Environment | Jupyter Notebook |

## 8. Run locally

Install the notebook dependencies:

~~~bash
python -m pip install numpy pandas matplotlib jupyter
~~~

Launch the notebook from this folder:

~~~bash
jupyter notebook work1.ipynb
~~~

The notebook expects **human_purchase_behaviour.csv** in the same working directory.

## 9. Interpretation limits

- The dataset has only an identifier, life-stage label, and premium-customer label.
- It contains no purchase amount, product, quantity, or date column.
- It therefore cannot establish spending, profitability, purchase frequency, customer lifetime value, or the monetary value of a premium segment.
- The current notebook visualises the life-stage/premium-tier relationship but should add a numeric cross-tab and normalised percentages before making strong segment comparisons.
- Recommendations should be treated as hypotheses until tested against transaction or campaign data.

## 10. Suggested next steps

1. Export the life-stage by premium-tier cross-tab as a table.
2. Add row-wise percentages to compare tier mix within each life stage.
3. Use a clearly labelled 100% stacked bar chart.
4. Check for duplicate loyalty identifiers and document the result.
5. Join customer segments to transaction data only where the data source, join key, and usage permissions are understood.

---

[Back to the Data Science portfolio](../../README.md) · [Detailed report](Human%20Purchase%20Behaviour%20Analysis%20Repor.md) · [Open the notebook](work1.ipynb)
