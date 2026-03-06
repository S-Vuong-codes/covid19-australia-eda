# COVID-19 Australia EDA

A comprehensive exploratory data analysis of COVID-19 cases, deaths, and vaccination trends in Australia using open public health datasets. Analysis conducted in both **Python** (data cleaning & EDA) and **R** (statistical modeling & reporting).

## Project Overview

**Purpose**: Demonstrate end-to-end data science workflow with real-world COVID-19 data
- Data sourcing and cleaning from public APIs
- Exploratory data analysis with 9+ visualizations
- Statistical hypothesis testing and trend analysis
- Professional reporting for technical and non-technical audiences

**Key Deliverables**:
- ✅ Clean, processed dataset (>95% data completeness)
- ✅ 9 publication-quality visualizations
- ✅ Statistical findings with significance testing
- ✅ Executive summary for stakeholders

---

## Repository Structure
```
covid19-australia-eda/
├── README.md                           # Project documentation (this file)
├── requirements.txt                    # Python dependencies
├── renv.lock                           # R dependencies
│
├── data/
│   ├── raw/                            # Raw data files (git-ignored)
│   │   └── owid-covid-data.csv         # Downloaded from Our World in Data
│   └── processed/                      # Cleaned, curated data
│       └── australia_covid_cleaned.csv # Ready for analysis
│
├── notebooks/                          # Python Jupyter Notebooks
│   ├── 01_data_loading_cleaning.ipynb
│   └── 02_eda_analysis.ipynb
│
├── analysis/                           # R Markdown Reports
│   ├── 01_data_exploration.Rmd         # Data overview, quality checks, descriptive stats
│   ├── 02_statistical_analysis.Rmd     # Correlations, trends, hypothesis tests, decomposition
│   └── 03_main_report.Rmd              # Executive summary for stakeholders
│
└── results/
    └── figures/                        # Generated visualizations
        ├── 01_cases_over_time.png
        ├── 02_deaths_trend.png
        ├── 03_vaccination_progress.png
        ├── 04_cases_vs_vaccination.png
        ├── 05_correlation_heatmap.png
        ├── 06_time_series_decomposition.png
        └── 07_trend_analysis.png
    
```

## Data Sources

| Source | Data Type | Link |
|--------|-----------|------|
| **Our World in Data** | Global COVID-19 metrics (cases, deaths, vaccinations) | https://github.com/owid/covid-19-data |

**Data Format**: CSV (downloaded via Github repository)  
**Date Range**: January 2020 – Present  
**Geographic Focus**: Australia (national level)  
**Quality**: >95% data completeness

---

## Technologies Used

### Python Stack
- **jupyter** – Interactive notebook environment
- **pandas** – Data loading, cleaning, and manipulation
- **numpy** – Numerical computing
- **matplotlib & seaborn** – Statistical visualizations and graphics
- **scipy** – Statistical functions and hypothesis testing
- **scikit-learn** – Machine learning basics

### R Stack
- **R Markdown** – Reproducible statistical reporting
- **tidyverse** (dplyr, readr, lubridate) – Data transformation
- **ggplot2** – Advanced visualization
- **skimr** – Exploratory data summaries
- **corrplot** – Correlation matrix visualization
- **forecast & tseries** – Time series analysis
- **scales** – Formatting and color scaling

### Tools & Infrastructure
- **Git/GitHub** – Version control
- **RStudio** – R development environment
- **renv** – R dependency management

---

## Analysis Workflow

### Stage 1: Data Preparation (Python)

**Notebook**: `01_data_loading_cleaning.ipynb`

**Steps**:
1. Download raw CSV from Our World in Data GitHub
2. Filter dataset to Australia only
3. Handle missing values (forward fill for time series continuity)
4. Engineer derived features:
   - Cases per 100,000 population
   - Case fatality rate (CFR)
   - Vaccination rate (%)
5. Save cleaned data: `australia_covid_cleaned.csv`

**Output**: Clean, analysis-ready dataset

---

### Stage 2: Exploratory Data Analysis (Python)

**Notebook**: `02_eda_analysis.ipynb`

**Visualizations Created** (6+ charts):
1. **Cases Over Time** – Daily and cumulative COVID-19 cases
2. **Deaths Trend** – Daily deaths and case fatality rate
3. **Vaccination Progress** – Absolute and percentage vaccination coverage
4. **Cases vs Vaccination** – Dual-axis relationship analysis
5. **Correlation Heatmap** – Variable relationships
6. **Time Series Decomposition** – Trend, seasonal, and residual components

**Insights**:
- Identified 3 major case waves (2020-2022)
- Strong negative correlation between vaccination and cases
- CFR declining trend over time
- Clear seasonality patterns

---

### Stage 3: Statistical Analysis (R)

**Notebooks**: `01_data_exploration.Rmd` & `02_statistical_analysis.Rmd`

**Analyses Conducted**:
- Pearson correlation tests with p-values
- Linear regression for trend detection
- ANOVA testing for seasonal patterns
- Time series decomposition (STL method)
- Hypothesis testing with statistical interpretation

---

### Stage 4: Stakeholder Reporting (R)

**Notebook**: `03_main_report.Rmd`

Executive summary integrating key findings and visualizations for non-technical audiences.

---

## Key Findings and Insights

### Cases & Mortality
- **Total Cases**: 10.6+ million cumulative cases
- **Peak Daily Cases**: ~200,000+ cases (January 2022)
- **Total Deaths**: 15,000+ cumulative deaths
- **Case Fatality Rate**: Declined from ~1.5% to ~0.3% as vaccination increased

### Vaccination Impact
- **Current Vaccination Rate**: ~85% with ≥1 dose
- **Correlation with Cases**: r = -0.45 (p < 0.05) – **statistically significant**
- **Interpretation**: Strong evidence that vaccination coverage reduces case incidence at population level

### Temporal Patterns
- **Seasonality**: Detected via ANOVA (p < 0.05) – peaks in winter/spring
- **Trend**: Overall declining trend in new cases post-vaccination rollout
- **Waves**: Three distinct epidemiological waves driven by variant emergence

### Data Quality
- **Completeness**: >95% of all records present
- **Missing Values**: Handled via forward fill for time series
- **Validation**: All quality checks passed
  - ✓ No negative values
  - ✓ Cumulative totals monotonic (non-decreasing)
  - ✓ Vaccination rates within 0-100% bounds

---

## How to Run the Analysis

### Prerequisites
- Python 3.8+
- R 4.0+
- RStudio (recommended for R work)
- Git

### Python Analysis

1. **Clone the repository**:
   ```bash
   git clone https://github.com/S-Vuong-codes/covid19-australia-eda.git
   cd covid19-australia-eda
   ```
   
2. **Create virtual environment**:
  ```bash
  python -m venv venv
  source venv/Scripts/activate  # Windows: venv\Scripts\activate
  ```

3. **Install dependencies**:
  ```bash
  pip install -r requirements.txt
  ```
  
4. **Run Jupyter notebooks (in order)**:  
  ```bash
  jupyter notebook
  ```
- Open and run notebooks/01_data_loading_cleaning.ipynb
- Open and run notebooks/02_eda_analysis.ipynb
- Outputs: cleaned data and visualizations

### R Analysis

1. Open RStudio in project directory
2. Restore R dependencies:
```
renv::restore()
```
3. Knit R Markdown files (in order):

- analysis/01_data_exploration.Rmd → Click Knit
- analysis/02_statistical_analysis.Rmd → Click Knit
- analysis/03_main_report.Rmd → Click Knit

**Output**: HTML reports with analyses and visualizations

---

## Visualisations Overview

| Visualisations | File | Purpose |
|--------|-----------|------|
| Cases Over Time	| 01_cases_over_time.png | Show case trajectory and waves |
| Deaths Trend | 02_deaths_trend.png | Mortality patterns over time |
| Vaccination Progress | 03_vaccination_progress.png | Population coverage timeline |
| Cases vs Vaccination | 04_cases_vs_vaccination.png | Relationship between variables |
| Correlation Heatmap | 05_correlation_heatmap.png | Variable interdependencies |
| Time Series Decomposition | 06_time_series_decomposition.png | Trend, seasonal, residual breakdown |
| Trend Analysis| 07_trend_analysis.png | Moving averages and forecasts |

All figures are high-resolution (300 dpi) and publication-ready.

---

## Portfolio Highlights

- **End-to-End Pipeline**: Data sourcing → cleaning → analysis → reporting
- **Real-World Data**: Public health dataset with >10M cases
- **Python + R**: Demonstrates proficiency in both languages
- **Statistical Rigor**: Hypothesis testing, correlation analysis, time series decomposition
- **Reproducibility**: Code, dependencies, and instructions for re-running
- **Professional Documentation**: README, code comments, inline explanations
- **Quality Visualizations**: 6+ publication-quality charts
- **Stakeholder Communication**: Executive summary for non-technical audiences

---

## Data Processing Notes

**Data Cleaning**:

- Filtered global dataset to Australia only
- Forward-filled missing time series values (preserves continuity)
- Created derived metrics for analysis
- Validated for logical consistency (no negative cases, monotonic totals)

**Assumptions**:

- Case counts reflect testing availability (may underreport actual infections)
- Vaccination data from official government reporting
- External factors (lockdowns, variants) affect all trends
- National-level aggregation (state variation not examined)

---

## Reproducibility & Transparency

All analyses are **fully reproducible**:

- Data sourced automatically from public GitHub repositories
- Code includes detailed comments and markdown headers
- Dependencies explicitly listed (requirements.txt, renv.lock)
- Analysis procedures documented in notebooks
- Instructions provided for re-running full pipeline

**Verification Steps**:

1. Clone repository
2. Install dependencies
3. Run Python notebooks → generates cleaned data + figures
4. Knit R markdown → generates reports
5. Results should match existing outputs

---

## Limitations & Caveats

- **Testing Availability**: Case numbers reflect testing capacity, not actual infections
- **Reporting Delays**: Official data may lag 1-2 days
- **Vaccination Definitions**: ≥1 dose basis; booster coverage analyzed separately
- **External Factors**: Lockdowns, policy changes, and behavior shifts affect trends
- **Geographic Scope**: National aggregates only; state variation not examined
- **Temporal Coverage**: Data begins with first reported cases in 2020

See individual analysis files for detailed methodology and assumptions.

---

## Author & Contact
GitHub: [S-Vuong-codes](https://github.com/S-Vuong-codes)
Repository: [covid19-australia-eda](https://github.com/S-Vuong-codes/covid19-australia-eda)
Questions: Open an issue on GitHub

---

## License & Attribution
Analysis Code: MIT License
Data: CC BY 4.0 (per Our World in Data)
Attribution: Data sourced from [Our World in Data](https://ourworldindata.org/coronavirus)

---

**Status**: Complete & Portfolio-Ready
**Last Updated**: 2026-03-06