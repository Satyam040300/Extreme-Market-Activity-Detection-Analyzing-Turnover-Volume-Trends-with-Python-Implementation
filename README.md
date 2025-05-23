# Extreme Market Activity Detection

## Overview
## Methodology 1 
This project analyzes daily trading activity from the CRSP (Center for Research in Security Prices) database to detect unusually high dollar volume spikes in U.S. stocks. By leveraging WRDS (Wharton Research Data Services), the script retrieves data from 2000 onward, calculates dollar volume, adjusts it for inflation (relative to a base CPI year, such as 2013), and applies filters to flag days where trading volume is:

Significantly higher than the stock’s recent 5-day average, and

Much larger than the next trading day's volume.

The result is a dataset of potential market anomalies, liquidity events, or news-driven spikes. This analysis is useful for researchers, analysts, and quantitative finance practitioners interested in market microstructure, event studies, or liquidity modeling.

## Methodology 2
This project analyzes stock market data since 2000 to detect extreme market activity by examining average turnover (volume per shares outstanding). The goal is to identify liquidity shocks and trading anomalies using Python and WRDS CRSP data.

## Data Sources
- **WRDS CRSP Daily Stock File (dsf)**: Includes daily stock prices and trading volume.
- **WRDS CRSP Daily Shares Outstanding (dse)**: Provides shares outstanding for each stock.

## Methodology 1

##  Objective

- Connect to WRDS and query CRSP daily stock data (from 2000 onward).
- Calculate daily **dollar volume** = price × volume.
- Adjust dollar volume using **inflation factors** (e.g., CPI base year = 2013).
- Identify stock-days where:
  - Inflation-adjusted dollar volume > $100M.
  - Volume is >10x the **5-day trailing average**.
  - Volume is >10x the **next day's volume**.

## Methodology 2

### Data Extraction
- Query daily stock price, volume, and shares outstanding from WRDS.

### Data Preprocessing
- Convert dates to datetime format.
- Adjust share outstanding values (stored in thousands in CRSP).
- Compute turnover ratio as `volume / shares outstanding`.

### Rolling Statistics & Outlier Detection
- Compute 60-day rolling mean and standard deviation for turnover per stock.
- Identify extreme turnover days where Z-score exceeds ±3 standard deviations.

### Visualization
- Histogram of abnormal turnover with a normal distribution overlay.
- Highlight extreme turnover days in the dataset.

## Installation & Usage

### Requirements
- Python 3.x
- WRDS Account
- Required Libraries: `wrds`, `pandas`, `numpy`, `matplotlib`, `scipy`

## Output

filtered_stock_days2000.csv : Contains stock-days flagged as extreme turnover events (from Methodology 1).

filtered_turnover_stock_days.csv: Contains stock-days flagged as extreme turnover events (from Methodology 2).

Visualization: Abnormal turnover histogram with ±3 standard deviation markers.

## Future Enhancements

Compute market-wide turnover Z-scores.
Integrate macroeconomic event overlays.
Test alternative anomaly detection methods (MAD, IQR-based filtering).


## Author
Satyam

MS in Business Analytics(Finance) from University at Buffalo School of Management
