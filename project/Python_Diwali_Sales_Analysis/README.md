# Diwali Sales Analysis

An exploratory data analysis project using a retail sales dataset to understand customer, geographic, occupation, and product-category patterns during a Diwali sales period.

**Author:** Parag Tiwari  
**Notebook:** [Diwali_Sales_Analysis.ipynb](Diwali_Sales_Analysis.ipynb)  
**Parent portfolio:** [Data Science repository](https://github.com/PARAG-TIWARI/Data-Science)

## 1. Project overview

The goal of this analysis is to explore the available sales records, identify which customer groups and regions contribute prominently to recorded orders and sales amount, and summarise observations that could inform further retail analysis.

The notebook uses descriptive statistics, grouped aggregations, and visualisations. It is an exploratory analysis rather than a predictive model or a causal study.

## 2. Dataset overview

The notebook loads **Diwali Sales Data.csv**.

| Item | Recorded value |
|---|---:|
| Original rows | 11,251 |
| Original columns | 15 |
| Rows with a missing Amount value | 12 |
| Rows remaining after dropping incomplete records | 11,239 |
| Columns removed as empty/uninformative | Status, unnamed1 |

Fields used in the analysis include customer ID, gender, age group, age, marital-status code, state, zone, occupation, product category, order count, and amount.

The notebook removes the two empty columns, checks null values, drops rows with missing values, and converts Amount to an integer for subsequent analysis.

## 3. Analytical workflow

~~~mermaid
flowchart TD
    A[Load retail sales CSV] --> B[Inspect schema and summary statistics]
    B --> C[Remove empty columns]
    C --> D[Check missing values]
    D --> E[Remove rows with missing Amount]
    E --> F[Convert Amount data type]
    F --> G[Group and aggregate customer and sales fields]
    G --> H[Visualise patterns]
    H --> I[Document observations and recommendations]
~~~

### Analysis dimensions

- **Gender:** record counts and aggregate Amount by gender.
- **Age:** buyer counts and aggregate Amount by age group.
- **Geography:** total orders and Amount by state.
- **Marital-status code:** distribution and aggregate Amount by gender and encoded status.
- **Occupation:** customer counts and aggregate Amount by occupation.
- **Product category:** category counts and aggregate Amount.
- **Products:** highest-order product IDs.

## 4. Findings recorded in the notebook

The notebook's charts and written observations highlight the following exploratory patterns:

1. Female-labelled records form a larger share of the analysed buyer records and contribute a higher aggregate Amount in the displayed gender comparison.
2. The 26–35 age band is prominent in the buyer and sales analysis, with female records particularly represented in the age-group comparison.
3. Uttar Pradesh, Maharashtra, and Karnataka are identified in the notebook commentary among the leading states for order and sales totals.
4. IT, Healthcare, and Aviation are highlighted in the occupation analysis.
5. Food, Clothing, and Electronics are highlighted among the product categories with notable sales.

These are qualitative observations from the notebook's exploratory charts and comments. The report does not assign exact percentages or monetary totals because those figures are not recorded as reproducible tables in the current notebook.

## 5. Business questions suggested by the analysis

The observed patterns can guide further investigation:

- Do age groups differ in average order value, not just total sales?
- Are state-level differences explained by customer counts, order frequency, or average transaction value?
- Do product-category patterns remain similar when sales are normalised per customer?
- Are occupational patterns stable across geography and age groups?
- Would a properly labelled marital-status field change the interpretation of the segment comparison?

These are follow-up questions, not proven causal recommendations.

## 6. Visualisation approach

The notebook uses:
- Count plots for buyer distribution.
- Bar charts for aggregate Amount by group.
- State-level comparisons for orders and sales.
- Product-category and product-ID rankings.

The charts are generated with Seaborn and Matplotlib.

## 7. Technology stack

| Area | Tools |
|---|---|
| Language | Python |
| Data manipulation | Pandas, NumPy |
| Visualisation | Matplotlib, Seaborn |
| Environment | Jupyter Notebook |

## 8. Run locally

Place the dataset file in this project folder, then install the dependencies:

~~~bash
python -m pip install numpy pandas matplotlib seaborn jupyter
~~~

Launch the notebook:

~~~bash
jupyter notebook Diwali_Sales_Analysis.ipynb
~~~

Run the cells from top to bottom. The notebook reads **Diwali Sales Data.csv** using a relative path, so the notebook's working directory should be this project folder.

## 9. Limitations and interpretation notes

- The notebook drops the 12 rows with missing Amount values; the effect of this exclusion is not analysed.
- Aggregate Amount is not the same as average spend per customer. A larger total may reflect a larger group rather than higher individual purchasing power.
- The marital-status field is stored as a numeric code. Its meaning should be confirmed from the dataset documentation before assigning labels such as married or unmarried.
- The notebook is descriptive. It does not perform significance testing, causal analysis, or a predictive evaluation.
- Some findings are written as comments beside charts rather than exported as summary tables. Exact values should be recalculated before being quoted in a formal report.
- Confirm the original dataset source and licence before redistributing the data.

## 10. Possible next steps

1. Add a reusable analysis script that exports group-level summary tables.
2. Compare total sales, unique customers, order count, and average amount separately.
3. Calculate percentages with clearly defined denominators.
4. Add segment-level cross-tabulations and normalised comparisons.
5. Improve chart titles, axis labels, and currency formatting.
6. Record dataset provenance and the exact cleaning decisions in a reproducible report.

---

[Back to the Data Science portfolio](../../README.md) · [Open the notebook](Diwali_Sales_Analysis.ipynb) · [GitHub profile](https://github.com/PARAG-TIWARI)
