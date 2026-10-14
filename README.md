# Global Development Explorer

Interactive Tableau project exploring how **wealth, health and demographics** connect across 230+ countries.

![Overview dashboard](images/01_overview.png)

## Live dashboard
[View on Tableau Public](PUT-YOUR-TABLEAU-PUBLIC-LINK-HERE)

## Overview
This project turns a country-level dataset (economy, population, health, energy and communications indicators) into a small analytical product: three linked dashboards and a five-page Tableau Story that ends with three recommendations. It was built as a course project (Advanced Tableau Storytelling & Interactive Analytics) and designed as a portfolio piece.

## What's inside
| Page | What it shows |
|---|---|
| **Overview** | KPI cards (life expectancy, GDP per capita, number of countries), a world map driven by an indicator selector, and a Top N bar chart |
| **Wealth vs Health** | GDP per capita vs life expectancy (log axis, trend line, median reference lines, auto-detected outliers) and a bubble chart of HIV/AIDS prevalence vs life expectancy |
| **Demographics** | Infant mortality histogram, population treemap and a top-10 fertility chart |
| **Key Takeaways** | Three recommendations drawn from the analysis |
| **Story** | 5-page Tableau Story: overview, income vs life expectancy, exceptions, demographics, recommendations |

## Visualization types (6)
Filled map, scatter plot with trend line, bar chart, histogram, treemap, bubble chart.

## Interactivity
- **Parameters:** `Select Indicator` (GDP per Capita / Life Expectancy / Infant Mortality) and `Top N` (5 to 20)
- **Dashboard actions (3):**
  - `Map to KPIs`: selecting a country on the map filters the KPI cards
  - `Income Highlight`: selecting a point highlights its income group across charts
  - `Histogram to Treemap`: selecting a histogram bar filters the treemap
- **Navigation buttons** between dashboards

## Calculated fields
- `Income Group`: buckets countries by GDP per capita into four groups
- `Selected Indicator Value`: switches the measure based on the parameter
- `Anomaly Flag`: uses a `FIXED` LOD expression to flag countries with above-median income but life expectancy more than 10 years below the median
- `Avg Life Expectancy`, `Avg GDP per Capita`, `Countries Count`: KPI measures

## Key findings
- GDP per capita and life expectancy are strongly related (about 0.73 correlation after a log transform of GDP).
- Life expectancy and infant mortality are strongly and negatively related (about -0.89).
- **South Africa, Botswana and Gabon** break the income pattern: higher income but much shorter life expectancy, driven largely by HIV/AIDS.
- Infant mortality and fertility are highest in the lowest-income countries.

## Screenshots
![Wealth vs Health](images/02_wealth_vs_health.png)
![Demographics](images/03_demographics.png)
![Key Takeaways](images/04_key_takeaways.png)
![Story](images/05_story.png)

## Repository structure
```
global-development-explorer/
├── README.md
├── Global_Development_Explorer.twbx   # Tableau packaged workbook (open with Tableau Desktop or Tableau Public)
├── data/
│   └── Country_Data_Clean.csv         # cleaned dataset used in the workbook
└── images/                            # screenshots used in this README
```

## How to open
1. Download `Global_Development_Explorer.twbx`.
2. Open it with [Tableau Public](https://public.tableau.com/app/discover) (free) or Tableau Desktop. The data is packaged inside the workbook.

## Data notes
- One row per country/territory; it is a **snapshot with no time dimension**, so the "trend" shown is the relationship between two indicators, not a time series.
- The dataset appears to predate the early 2010s (for example it still lists *Serbia and Montenegro* and *Netherlands Antilles*), so figures should be read as historical, not current.
- Non-country rows (for example the European Union aggregate) are excluded with a data source filter.
- A few names were mapped manually in Tableau (Congo, Serbia and Montenegro to Serbia).

## Tools
Tableau Public

## Author
Fatima Awad
