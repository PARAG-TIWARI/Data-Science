# Seoul Bike Sharing — Exploratory Data Analysis

An exploratory analysis of hourly bike rentals in Seoul, examining how rental demand varies by time of day, season, and weather conditions.

**Author:** Parag Tiwari  
**Notebook:** [analysis.ipynb](analysis.ipynb)  
**Dataset:** [SeoulBikeData.csv](SeoulBikeData.csv)  
**Parent portfolio:** [Data Science repository](https://github.com/PARAG-TIWARI/Data-Science)

## 1. Project overview

The project investigates patterns in a year of hourly bike-rental observations and explores relationships between rental counts, temperature, rainfall, snowfall, and seasonal conditions.

The notebook includes descriptive statistics, data-quality checks, date feature extraction, grouped comparisons, correlation analysis, visual exploration, and an introductory Linear Regression workflow.

## 2. Dataset profile

The notebook reports **8,760 observations and 14 columns**, covering hourly records from **1 December 2017 to 30 November 2018**.

The fields include:
- Date and hour.
- Rented Bike Count.
- Temperature and dew-point temperature.
- Humidity, wind speed, and visibility.
- Solar radiation, rainfall, and snowfall.
- Season, holiday indicator, and functioning-day indicator.

The notebook's initial data-quality outputs show no missing values and no duplicate rows in this dataset.

## 3. Analysis workflow

~~~mermaid
flowchart TD
    A[Load hourly rental dataset] --> B[Inspect schema and summary statistics]
    B --> C[Check missing values and duplicates]
    C --> D[Parse dates and create calendar features]
    D --> E[Explore hourly and seasonal demand]
    E --> F[Compare weather variables and rentals]
    F --> G[Visualise patterns and correlations]
    G --> H[Explore a baseline regression workflow]
~~~

## 4. Findings recorded in the notebook

### Overall demand

| Measure | Recorded value |
|---|---:|
| Number of observations | 8,760 |
| Mean rentals per observation | 704.60 |
| Minimum rentals | 0 |
| Maximum rentals | 3,556 |
| Mean temperature | 12.88 °C |

### Hourly pattern

The notebook's hourly averages show the highest mean rental count at **18:00**, at approximately **1,502.9 rentals**. Other high-demand hours include 17:00 and 19:00, indicating a strong late-afternoon/evening pattern in this dataset.

### Seasonal pattern

| Season | Mean rented-bike count |
|---|---:|
| Summer | 1,034.07 |
| Autumn | 819.60 |
| Spring | 730.03 |
| Winter | 225.54 |

Summer has the highest average hourly rental count in the recorded analysis, while Winter has the lowest.

### Weather relationships

The notebook calculates Pearson correlations between rented-bike count and selected weather variables:

| Variable | Correlation with rented-bike count |
|---|---:|
| Temperature | +0.539 |
| Snowfall | -0.142 |
| Rainfall | -0.123 |

The temperature relationship is moderately positive in this dataset. The rainfall and snowfall relationships are weaker and negative in the recorded correlation matrix.

Correlation alone does not establish that a weather variable causes a change in rentals. Other factors—such as hour, season, day type, and service availability—may also contribute.

## 5. Visualisation approach

The notebook explores:
- Hourly rental averages.
- Descriptive distributions and summary statistics.
- Seasonal rental comparisons.
- Weather-variable correlations.
- Calendar features derived from the date column.

The code imports Matplotlib and Seaborn for plotting and uses Pandas for grouping and analysis.

## 6. Introductory modelling

The notebook begins a Linear Regression exercise using rental count and weather/time information. It imports train/test splitting and regression metrics such as R², MAE, and MSE.

The saved notebook does not provide a complete, reproducible held-out evaluation report. Therefore, no model accuracy or predictive-performance claim is made here.

A stronger modelling iteration should:
1. Define the prediction target and feature set explicitly.
2. Split data chronologically to avoid using future observations to predict the past.
3. Build a reproducible preprocessing and modelling pipeline.
4. Compare against a simple baseline.
5. Report MAE, RMSE, and R² on a held-out time period.

## 7. Technology stack

| Area | Tools |
|---|---|
| Language | Python |
| Data manipulation | Pandas, NumPy |
| Visualisation | Matplotlib, Seaborn |
| Modelling exploration | Scikit-learn |
| Environment | Jupyter Notebook |

## 8. Run locally

Install the dependencies:

~~~bash
python -m pip install numpy pandas matplotlib seaborn scikit-learn jupyter
~~~

Launch the notebook from this project folder:

~~~bash
jupyter notebook analysis.ipynb
~~~

The notebook expects **SeoulBikeData.csv** in the same working directory.

## 9. Limitations and interpretation notes

- The analysis is descriptive and does not establish causal effects.
- The holiday and functioning-day fields exist in the dataset, but the notebook does not retain a completed statistical comparison proving that rentals are lower on holidays or non-functioning days.
- The notebook contains an exploratory regression setup but no saved, complete held-out evaluation.
- One later notebook section reparses dates separately; date parsing should consistently use the dataset's day-first format.
- The results describe the included period and should not be assumed to represent current demand or every season/year.

## 10. Possible next steps

1. Add weekday/weekend and holiday comparisons with clearly defined denominators.
2. Visualise hourly demand separately by season.
3. Investigate the relationship between temperature and rentals after controlling for hour and season.
4. Build a chronological train/test evaluation for demand forecasting.
5. Export chart images and a compact metrics table for a reproducible report.

---

[Back to the Data Science portfolio](../../README.md) · [Open the analysis notebook](analysis.ipynb) · [Dataset](SeoulBikeData.csv)
