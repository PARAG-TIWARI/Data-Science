# Data Science & Analytics Portfolio

A collection of Python-based data analysis projects, exploratory notebooks, visualisation exercises, and applied analytics applications by **Parag Tiwari**.

This repository documents work across the data-analysis workflow: loading datasets, checking data quality, cleaning and transforming records, exploring patterns, visualising results, and translating observations into questions or recommendations.

## Project index

| Project | Focus | Tools | Documentation |
|---|---|---|---|
| QVI Customer & Transaction Analysis | Customer segmentation joined to 264K+ transaction rows; product and segment sales analysis | Python, Pandas, CSV, Excel | [Analysis report](pandas/README.md) · [Notebook](pandas/parag%20-%20G35%20Python%20-%20Pandas%20Analysis.ipynb) |
| Diwali Sales Analysis | Retail/customer EDA and business observations | Python, Pandas, NumPy, Matplotlib, Seaborn | [Project report](project/Python_Diwali_Sales_Analysis/README.md) · [Notebook](project/Python_Diwali_Sales_Analysis/Diwali_Sales_Analysis.ipynb) |
| Human Purchase Behaviour Analysis | Customer life-stage and premium-tier segmentation | Python, Pandas, NumPy, Matplotlib | [Project report](project/human_purchase_behaviour_Analysis/README.md) · [Analysis report](project/human_purchase_behaviour_Analysis/Human%20Purchase%20Behaviour%20Analysis%20Repor.md) · [Notebook](project/human_purchase_behaviour_Analysis/work1.ipynb) |
| Seoul Bike Data Analysis | Hourly rental patterns and weather/season exploration | Python, Pandas, NumPy, Matplotlib, Seaborn, Scikit-learn | [Project report](project/SeoulBikeData_Analysis/README.md) · [Notebook](project/SeoulBikeData_Analysis/analysis.ipynb) |
| Olympic Data Analysis Web App | Interactive exploration of Olympic history | Python, Pandas, Streamlit, Plotly, Seaborn, Matplotlib | [Standalone application repository](https://github.com/PARAG-TIWARI/olympic-data-analysis-web-app) · [Live application](https://olympic-data-analysis-web-app-am3jfyvy4gxsad7yi4xbug.streamlit.app/) |

## What this repository demonstrates

### Data analysis
- Inspecting tabular datasets with Pandas.
- Checking schema, data types, missing values, duplicates, and summary statistics.
- Cleaning columns, normalising categories, and preparing data for analysis.
- Joining datasets and comparing groups with aggregations and pivot tables.
- Exploring time, demographic, geographic, product, and customer-segment patterns.

### Visualisation and communication
- Creating charts with Matplotlib and Seaborn.
- Building interactive views with Plotly and Streamlit.
- Writing notebook observations and documenting limitations.
- Turning exploratory findings into testable business questions and possible next steps.

### Introductory modelling
- Exploring a baseline regression workflow in the Seoul bike-rental notebook.
- Reviewing model-related outputs carefully and avoiding performance claims when an evaluation result is not recorded.

## Repository structure

~~~text
Data-Science/
├── data visualisation/
│   ├── mateplotlib/
│   └── seaborn/
├── numpy/
├── pandas/
│   ├── README.md
│   └── analysis and learning notebooks
└── project/
    ├── Python_Diwali_Sales_Analysis/
    ├── SeoulBikeData_Analysis/
    ├── human_purchase_behaviour_Analysis/
    └── Olympic Data Analysis web app/
~~~

The Matplotlib, Seaborn, NumPy, and Pandas folders also contain learning notebooks and smaller practice exercises. The project folders contain the more complete analysis work.

## Getting started

### 1. Clone the repository

~~~bash
git clone https://github.com/PARAG-TIWARI/Data-Science.git
cd Data-Science
~~~

### 2. Create a Python environment

~~~bash
python -m venv .venv

# Windows PowerShell
.venv\Scripts\Activate.ps1

# macOS / Linux
source .venv/bin/activate
~~~

### 3. Install the common analysis tools

~~~bash
python -m pip install --upgrade pip
pip install numpy pandas matplotlib seaborn jupyter notebook
~~~

Some projects use additional packages. Check the project-specific README before running an application or notebook.

### 4. Open the notebooks

~~~bash
jupyter notebook
~~~

Open the relevant project folder and run the notebook from that folder so its relative dataset paths resolve correctly.

## Working with the findings

The project reports distinguish between:
- **Observed results:** values or patterns directly recorded in a notebook or calculated from the included dataset.
- **Interpretations:** explanations that may be consistent with the charts but need further analysis.
- **Recommendations:** ideas to investigate, not proof of a causal relationship.

Where a notebook does not include a reproducible metric, the documentation says so rather than inventing one. Dataset provenance and redistribution conditions should be checked at the original source before reusing data outside learning or portfolio work.

## Author

**Parag Tiwari**  
[GitHub profile](https://github.com/PARAG-TIWARI)

---

This repository is a learning and project portfolio. Individual notebooks may represent exploratory work at different stages of completeness; consult each project report for its scope and limitations.
