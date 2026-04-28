# Data Analysis on Market Timing vs Long-Term Investing


## Overview

This project is a data-driven analysis comparing two common stock investment strategies, **Buy & Hold** (long-term investing) and **Market Timing**, to provide clear, evidence-based guidance for first-time and casual investors.

Using 20+ years of historical ETF data retrieved from Yahoo Finance, we simulated **six portfolio scenarios** across three distribution types for both strategies. Results are communicated through an interactive Power BI dashboard, enabling non-expert users to explore and compare strategy outcomes without a financial background.

---

> *"When it comes to investing to make a profit, are casual investors better off with market timing or long-term investing?"*

Casual investors frequently face a knowledge gap that leads to speculation-driven decisions or confusion when entering the stock market. This project aims to close that gap by comparing two of the most commonly debated entry-level investment strategies using real historical data and reproducible analysis.

---

## Data Sources

Three ETFs were selected to represent different segments of the U.S. equity market:

| ETF | Index Tracked | Description |
|---|---|---|
| **SPY** | S&P 500 | Tracks 500 of the largest publicly traded U.S. companies |
| **QQQ** | Nasdaq-100 | Tracks 100 of the largest non-financial companies on the Nasdaq |
| **VTI** | Total U.S. Market | Provides exposure to the entire investable U.S. stock market |

- **Source:** Yahoo Finance via the `yfinance` Python library

---
## Getting Started

### Prerequisites

| Component | Requirement |
|---|---|
| Operating System | Windows 10/11, macOS 12+, or Ubuntu 20.04+ |
| Python | 3.9 or higher |
| Git | Any recent version |
| Power BI | Power BI Desktop (Windows) or Power BI Service (browser) |
| Storage | ~500 MB for all raw, processed, and simulation CSV files |

### Installation

**1. Clone the repository**

```bash
git clone https://github.com/AdaTaing/COMP3250-Project
cd COMP3250-Project
```

**2. Create and activate a virtual environment**

```bash
python -m venv venv

# Windows
venv\Scripts\activate

# macOS / Linux
source venv/bin/activate
```

**3. Install dependencies**

```bash
pip install -r requirements.txt
```

**4. Launch Jupyter**

```bash
jupyter notebook
```

### Running the Pipeline

Execute the notebooks **in order** from the `notebooks/` folder. Each notebook must complete without errors before the next is run.

| Order | Notebook | Expected Output |
|---|---|---|
| 1 | `data_retrieval.ipynb` | `data/raw/SPY_raw.csv`, `QQQ_raw.csv`, `VTI_raw.csv` |
| 2 | `data_cleaning.ipynb` | `data/processed/SPY_cleaned.csv`, `QQQ_cleaned.csv`, `VTI_cleaned.csv`, `combined_prices.csv` |
| 3 | `indicators.ipynb` | `data/processed/prices_with_indicators.csv` |
| 4 | `single_buy_hold.ipynb` | `data/simulations/single_buy_hold.csv` |
| 4 | `single_timing.ipynb` | `data/simulations/single_timing.csv` |
| 4 | `equal_buy_hold.ipynb` | `data/simulations/equal_buy_hold.csv` |
| 4 | `equal_timing.ipynb` | `data/simulations/equal_timing.csv` |
| 4 | `custom_buy_hold.ipynb` | `data/simulations/custom_buy_hold.csv` |
| 4 | `custom_timing.ipynb` | `data/simulations/custom_timing.csv` |
| 5 | `combine_simulations.ipynb` | `data/simulations/combined_simulations.csv` |
| 6 | `summary_metrics.ipynb` | `data/metrics/summary_metrics.csv` |

No manual steps are required between notebooks. Each notebook reads from and writes to consistent, predefined file paths.

**Load the dashboard**

Open `dashboard/Strategy_Analysis_Dashboard.pbix` in Power BI Desktop. If prompted to refresh the data source, point it to `data/simulations/combined_simulations.csv`.

---

## Project Structure

```
COMP3250-Project/
│
├── dashboard/
│   ├── COMP 3250 FINAL PROJECT.pptx   # Presentation slides
│   ├── Strategy_Analysis_Dashboard.pbix  # Power BI dashboard file
│   └── dashboard.txt
│
├── data/
│   ├── metrics/
│   │   └── summary_metrics.csv         # Aggregated performance metrics
│   ├── processed/
│   │   ├── QQQ_cleaned.csv
│   │   ├── SPY_cleaned.csv
│   │   ├── VTI_cleaned.csv
│   │   ├── combined_prices.csv         # Merged ETF prices
│   │   └── prices_with_indicators.csv  # Combined prices + MA50 columns
│   ├── raw/
│   │   ├── QQQ_raw.csv
│   │   ├── SPY_raw.csv
│   │   └── VTI_raw.csv
│   └── simulations/
│       ├── combined_simulations.csv    # All six simulations merged
│       ├── custom_buy_hold.csv
│       ├── custom_timing.csv
│       ├── equal_buy_hold.csv
│       ├── equal_timing.csv
│       ├── single_buy_hold.csv
│       └── single_timing.csv
│
├── docs/
│   ├── COMP 3250 FINAL PROJECT.pptx
│   ├── Dashboard_User_Guide.md
│   ├── Data Dictionary.md
│   ├── Final_Report.pdf
│   ├── Performance_Metrics.md
│   ├── Problem_Overview.md
│   └── Simulation_Approach.md
│
├── notebooks/
│   ├── data_retrieval.ipynb
│   ├── data_cleaning.ipynb
│   ├── indicators.ipynb
│   ├── single_buy_hold.ipynb
│   ├── single_timing.ipynb
│   ├── equal_buy_hold.ipynb
│   ├── equal_timing.ipynb
│   ├── custom_buy_hold.ipynb
│   ├── custom_timing.ipynb
│   ├── combine_simulations.ipynb
│   └── summary_metrics.ipynb
│
├── outputs/
├── .gitignore
├── README.md
└── requirements.txt
```

---

## Tech Stack

| Tool | Purpose |
|---|---|
| **Python 3.9+** | All data engineering tasks: retrieval, cleaning, indicator calculation, and simulation |
| **pandas** | Data manipulation and transformation |
| **yfinance** | Yahoo Finance API wrapper for ETF data retrieval |
| **NumPy** | Numerical computations |
| **Jupyter Notebook** | Interactive pipeline execution and documentation |
| **Microsoft Power BI** | Interactive dashboard and results visualization |
| **GitHub** | Version control, collaboration, and audit trail |

---

**Investment Parameters:**

- Initial investment: **$10,000**
- Biweekly contributions: **$500** (every 10 trading rows)

Each simulation produces a CSV with **21 columns** as defined in the [Data Dictionary](#data-dictionary).

## Portfolio Scenarios

Six simulations are run across two strategies and three distribution types:

| # | Strategy | Distribution | Description |
|---|---|---|---|
| 1 | Buy & Hold | Single | 100% invested in SPY |
| 2 | Market Timing | Single | 100% invested in SPY |
| 3 | Buy & Hold | Equal | Equal split across SPY, QQQ, VTI |
| 4 | Market Timing | Equal | Equal split across SPY, QQQ, VTI |
| 5 | Buy & Hold | Custom | User-defined allocation across SPY, QQQ, VTI |
| 6 | Market Timing | Custom | User-defined allocation across SPY, QQQ, VTI |

---

## Performance Metrics

Each simulation is evaluated on five metrics:

| Metric | Description | What to Look For |
|---|---|---|
| **CAGR (%)** | Compound Annual Growth Rate — the steady annual rate at which the portfolio would have grown | Higher is better |
| **Sharpe Ratio** | Risk-adjusted return — how much return earned per unit of risk (volatility) taken | Above 1.0 is considered good; higher is better |
| **Volatility (%)** | Day-to-day fluctuation in portfolio value | Lower means a smoother, more predictable ride |
| **Max Drawdown (%)** | The single worst peak-to-trough loss experienced by the portfolio | Closer to 0% is better |
| **Total Profit ($)** | Raw dollar profit above total amount invested | Higher is better; negative means a net loss |

---

## 📈Key Findings📈

- **Buy & Hold** produced the highest total profit, final portfolio value, and CAGR across all portfolio types — it is the stronger strategy for maximizing long-term returns.
- **Market Timing** produced lower volatility, a smaller maximum drawdown, and a more efficient Sharpe Ratio — it is the safer strategy for investors primarily concerned with limiting large losses.
- The best overall portfolio value, best total profit, and best CAGR all belonged to **Buy & Hold – Equal**.
- The lowest max drawdown and lowest volatility belonged to **Timing – Single**.
- **Conclusion:** Buy & Hold is better for growing wealth over time. Market Timing is better for investors who prioritize capital preservation and cannot tolerate large swings.

| Portfolio_Type | Strategy | Final_Portfolio_Value | Total_Profit | 
|---|---|---|---|
| Custom | Buy & Hold | 2210672.43 | 1890172.43 | 
| Custom | Timing | 1141998.94 | 821498.94 | 
| Equal | Buy & Hold | 2262663.55 | 1942163.55 | 
| Equal | Timing | 1150538.82 | 830038.82 | 
| Single | Buy & Hold | 1729330.94 | 1408830.94 | 
| Single | Timing | 725083.84 | 404583.84 | 

---

## Dashboard

The results are presented through an interactive Power BI dashboard (`dashboard/Strategy_Analysis_Dashboard.pbix`).

> **Requirements:** Microsoft Power BI Desktop (Windows) or Power BI Service via browser (Mac). Free download at [powerbi.microsoft.com](https://powerbi.microsoft.com).

---

## Data Dictionary

Key columns produced by the simulation notebooks:

| Column | Type | Description |
|---|---|---|
| `Date` | `YYYY-MM-DD` | Trading session date |
| `SPY_Price` / `QQQ_Price` / `VTI_Price` | Float | Adjusted closing price for each ETF |
| `SPY_MA50` / `QQQ_MA50` / `VTI_MA50` | Float | 50-day moving average. `NaN` for first 49 rows. Blank in Buy & Hold simulations |
| `Position_SPY` / `Position_QQQ` / `Position_VTI` | Integer (0 or 1) | `1` = hold/buy signal; `0` = sell signal. Always `1` in Buy & Hold |
| `Contribution` | Float | `$500` every 10 rows; `$0` otherwise. Excludes initial investment |
| `Cash` | Float | Uninvested cash. Always `0` in Buy & Hold. Non-zero in Timing when `Position = 0` |
| `Shares_SPY` / `Shares_QQQ` / `Shares_VTI` | Float | Shares held that day. Only increases in Buy & Hold. Can drop to `0` in Timing |
| `Total_Invested` | Float | Cumulative capital deployed = `$10,000` + all contributions to date |
| `Portfolio_Value` | Float | Current total value of all holdings |
| `Earnings` | Float | `Portfolio_Value - Total_Invested`. Positive = profit; Negative = loss |
| `Daily_Return` | Percent | Day-over-day % change in `Portfolio_Value`. `NaN` on first row |
| `Strategy` | String | `'Buy & Hold'` or `'Timing'` |
| `Portfolio_Type` | String | `'Single'`, `'Equal'`, or `'Custom'` |

> For the full data dictionary, see [`docs/Data Dictionary.md`](docs/Data%20Dictionary.md).

---

## Documentation

All project documentation is available in the `docs/` folder:

| Document | Description |
|---|---|
| [`Final_Report.pdf`](docs/Final_Report.pdf) | Full project report including methodology, findings, and appendices |
| [`Problem_Overview.md`](docs/Problem_Overview.md) | Research question, scope, and project objectives |
| [`Data Dictionary.md`](docs/Data%20Dictionary.md) | Complete column definitions for all pipeline outputs |
| [`Simulation_Approach.md`](docs/Simulation_Approach.md) | Detailed explanation of Buy & Hold and Market Timing simulation logic |
| [`Performance_Metrics.md`](docs/Performance_Metrics.md) | Definitions and interpretation guidance for all five performance metrics |
| [`Dashboard_User_Guide.md`](docs/Dashboard_User_Guide.md) | Step-by-step guide to navigating and interpreting the Power BI dashboard |

---
