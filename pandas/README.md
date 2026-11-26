# QVI Customer & Transaction Analysis

A customer and retail transaction analysis that combines customer-segment attributes with product-level transaction records to explore sales patterns across life-stage and premium-customer groups.

**Author:** Parag Tiwari  
**Analysis notebook:** [parag - G35 Python - Pandas Analysis.ipynb](parag%20-%20G35%20Python%20-%20Pandas%20Analysis.ipynb)  
**Parent portfolio:** [Data Science repository](https://github.com/PARAG-TIWARI/Data-Science)

## 1. Executive overview

This analysis joins a customer profile dataset with transaction-level product sales using the loyalty-card identifier. It then explores product sales totals, average recorded sales per product row by life stage, and aggregate sales across life-stage and premium-customer segments.

The notebook provides a useful starting point for retail/customer analytics because it moves beyond a customer-category table and connects customer attributes to observed transaction records.

## 2. Dataset overview

The notebook reads two source files:

| Dataset | Rows | Columns | Main fields |
|---|---:|---:|---|
| QVI purchase behaviour | 72,637 | 3 | Loyalty card, life stage, premium-customer tier |
| QVI transaction data | 264,836 | 8 | Date, store, loyalty card, transaction ID, product, quantity, total sales |

The customer profile contains:
- Loyalty card identifier.
- Life-stage segment.
- Premium-customer tier: Budget, Mainstream, or Premium.

The transaction data contains:
- Date and store number.
- Loyalty card identifier and transaction ID.
- Product number and product name.
- Product quantity and total sales.

## 3. Data preparation and join

The notebook performs the following steps:

1. Loads the customer profile CSV and transaction Excel workbook with Pandas.
2. Inspects samples, schema, summary statistics, and missing values.
3. Checks the customer profile for repeated rows.
4. Standardises the customer identifier column name.
5. Confirms that the customer identifiers overlap between both tables.
6. Joins transaction rows to customer attributes using the loyalty-card identifier.
7. Aggregates sales by product and customer segment.

The notebook records **72,637 common customer identifiers**. The resulting left join contains **264,836 transaction rows** with customer-segment attributes attached.

~~~mermaid
flowchart TD
    A[QVI purchase behaviour<br/>72,637 customer profiles] --> C[Standardise loyalty-card key]
    B[QVI transaction data<br/>264,836 transaction rows] --> C
    C --> D[Match on LYLTY_CARD_NBR]
    D --> E[Enriched transaction table]
    E --> F[Sales by product]
    E --> G[Average row-level sales by life stage]
    E --> H[Sales by life stage and premium tier]
    E --> I[Average product quantity by life stage]
~~~

## 4. Recorded analysis outputs

### 4.1 Data completeness

The notebook's initial info/null checks show no missing values in the loaded customer-profile columns or transaction columns.

| Check | Recorded result |
|---|---:|
| Customer profiles | 72,637 |
| Transaction records | 264,836 |
| Common loyalty-card identifiers | 72,637 |
| Rows after the left join | 264,836 |

The notebook does not provide a formal post-merge audit table for unmatched rows or transaction-key uniqueness. Those checks should be added before treating the join as a production-quality data pipeline.

### 4.2 Highest sales by product

The notebook groups total sales by product name and displays the ten largest product totals. The leading entries in the saved output are:

| Product | Recorded total sales |
|---|---:|
| Dorito Corn Chp Supreme 380g | 40,352.00 |
| Smiths Crnkle Chip Orgnl Big Bag 380g | 36,367.60 |
| Smiths Crinkle Chips Salt & Vinegar 330g | 34,804.20 |
| Kettle Mozzarella Basil & Pesto 175g | 34,457.40 |
| Smiths Crinkle Original 330g | 34,302.60 |

These are dataset-level sums of the TOT_SALES field, not profit or margin figures.

### 4.3 Average recorded sales by life stage

The notebook calculates the mean of TOT_SALES grouped by life stage:

| Life stage | Mean TOT_SALES per transaction-product row |
|---|---:|
| Older Singles/Couples | 7.3868 |
| Retirees | 7.3643 |
| Midage Singles/Couples | 7.3577 |
| New Families | 7.2891 |
| Older Families | 7.2798 |
| Young Families | 7.2527 |
| Young Singles/Couples | 7.1585 |

**Interpretation:** The recorded average value per transaction-product row is relatively close across the seven life-stage groups. This metric is not average customer lifetime spending or average spend per customer; it is the mean of the row-level TOT_SALES field after the transaction table is joined to customer segments.

### 4.4 Total sales by life stage and premium tier

The notebook creates a pivot table that sums TOT_SALES by life stage and premium-customer tier.

| Life stage | Budget | Mainstream | Premium |
|---|---:|---:|---:|
| Midage Singles/Couples | 35,514.80 | 90,803.85 | 58,432.65 |
| New Families | 21,928.45 | 17,013.90 | 11,491.10 |
| Older Families | 168,363.25 | 103,445.55 | 81,958.40 |
| Older Singles/Couples | 136,769.80 | 133,393.80 | 132,263.15 |
| Retirees | 113,147.80 | 155,677.05 | 97,646.05 |
| Young Families | 139,345.85 | 92,788.75 | 84,025.50 |
| Young Singles/Couples | 61,141.60 | 157,621.60 | 41,642.10 |

These are aggregate sales totals. They should be interpreted alongside each segment's customer count, number of transactions, and average basket size before drawing conclusions about customer value or preference.

## 5. Analytical questions this work can support

The merged dataset provides a basis for further questions:

- Which life-stage and premium-tier combinations account for the largest total sales?
- Are high aggregate sales driven by a larger customer base, more transactions, larger quantities, or higher sales per transaction?
- Which products contribute the largest sales totals?
- Do product quantities vary across life stages?
- How do sales patterns change over time or across stores?

The current notebook explores some of these with grouped summaries and pivot tables, but does not fully answer all of them.

## 6. Technology stack

| Area | Tools |
|---|---|
| Language | Python |
| Data manipulation | Pandas |
| Input formats | CSV, Excel |
| Analysis | Groupby aggregations, joins, pivot tables |
| Environment | Jupyter Notebook |

## 7. Run locally

From the pandas folder, install the dependencies:

~~~bash
python -m pip install pandas openpyxl jupyter
~~~

Open the notebook:

~~~bash
jupyter notebook "parag - G35 Python - Pandas Analysis.ipynb"
~~~

Keep these datasets in the same folder as the notebook:

- QVI_purchase_behaviour.csv
- QVI_transaction_data.xlsx

## 8. Limitations and improvements

The notebook is an exploratory analysis and has several opportunities for improvement:

- Some early cells contain general Pandas practice and intermediate column-renaming attempts. These can be moved to a separate learning notebook.
- Add explicit checks for duplicate customer identifiers and duplicate transaction IDs.
- Audit unmatched customer identifiers after the join instead of relying only on the count of common IDs.
- Confirm the date format and convert the DATE column into a proper datetime field before time-based analysis.
- Add customer counts, transaction counts, sales per customer, average basket value, and quantity metrics alongside aggregate sales.
- Distinguish line-item sales from transaction-level basket totals; aggregate product rows to the transaction ID before calculating basket-level metrics.
- Add charts and a short written interpretation for the pivot tables.
- Record the data source, licence, reporting currency, and period covered.
- Use statistical tests or a suitable experimental design before making claims about customer preferences or the impact of a marketing action.

## 9. Conclusion

This notebook demonstrates an end-to-end introductory customer and transaction analysis workflow: loading separate datasets, aligning a shared identifier, joining customer attributes to transaction rows, and analysing product and customer-segment sales.

Its most valuable next step is to deepen the descriptive analysis with transaction-level basket metrics and clearly labelled visualisations, supported by explicit join and data-quality checks.

---

[Back to the Data Science portfolio](../README.md) · [Open the analysis notebook](parag%20-%20G35%20Python%20-%20Pandas%20Analysis.ipynb)
