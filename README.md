
# Index Balancing using S&P 500 Data

This project implements an end‑to‑end workflow for replicating and analyzing index balancing using S&P 500 constituents and their historical price data. The notebook automates data collection from public sources, constructs portfolio weights, and evaluates how index composition changes affect portfolio characteristics over time.[1]

## Project Overview

The objective of the notebook is to build a systematic framework that mimics an index provider’s rebalancing process for a broad equity index like the S&P 500.  The workflow covers downloading the current constituents, fetching historical daily prices for all tickers, computing index weights, and analyzing the impact of index changes on returns and exposures.[1]

## Data Collection

- The notebook installs and imports key libraries such as `yfinance`, `pandas`, `numpy`, and supporting packages for data handling and requests.[1]
- It first reads an S&P 500 constituents table that includes ticker symbol, company name, GICS sector, sub‑industry, headquarters location, date added, CIK, and founded year.[1]
- Using the ticker universe, the notebook downloads daily OHLCV data (open, high, low, close, volume) for each stock over the desired historical window through `yfinance`.[1]

## Data Preparation

- The code cleans and standardizes the constituents data, ensuring ticker symbols are consistent and aligned with price data returned by `yfinance`.[1]
- It structures the historical prices into panel‑like `DataFrame`s indexed by date and ticker, keeping key columns such as adjusted close and volume.[1]
- Basic sanity checks, such as inspecting head/tail of price tables and checking for missing values or delistings, are performed to ensure data quality before portfolio calculations.[1]

## Index Construction Logic

- The notebook builds index‑level weights from individual securities using either market‑cap approximations or equal‑weight logic, depending on what is available from the inputs.[1]
- For each rebalancing date, it calculates normalized portfolio weights that sum to one over the active constituent list.[1]
- It then combines security‑level returns with these weights to generate index‑level time series (e.g., daily index return).[1]

## Index Rebalancing and Turnover

- The workflow explicitly models index rebalancing by updating the constituent set and portfolio weights on rebalance dates (e.g., when new companies are added or removed).[1]
- It computes turnover metrics by comparing pre‑ and post‑rebalance weights, highlighting how much trading is required to move from the old to the new index composition.[1]
- The notebook can quantify the contribution of added and deleted names to overall index performance around rebalance events.[1]

## Performance and Exposure Analysis

- After constructing the synthetic index, the notebook calculates standard performance metrics such as cumulative return, average daily return, and volatility over the sample period.[1]
- It also breaks the index into sector or industry buckets using the GICS information from the constituents table, allowing analysis of sector weights and how they evolve through time and rebalances.[1]
- Visual and tabular summaries (e.g., head of constituents with their sectors and prices) help interpret how individual stocks and sectors drive index behavior.[1]

## Implementation Details

- The implementation is fully in Python, using `pandas` for time series manipulation and `yfinance` for market data access, making the workflow reproducible in environments like Google Colab.[1]
- The notebook is organized into logical sections: library setup, constituent data loading, price data download, index weight construction, rebalancing logic, and performance/exposure analysis.[1]
- This structure allows easy extension, for example changing the rebalancing frequency, trying alternative weighting schemes, or applying the same logic to other indices or custom universes.[1]

## How to Use

- Open the notebook in Google Colab or a local Jupyter environment and run all cells sequentially to reproduce the full index balancing pipeline.[1]
- Users can customize tickers, date ranges, and weighting rules to experiment with different index designs, or plug in alternative constituent files (e.g., other country indices or factor portfolios).[1]
https://github.com/ishhverma/S-P500-INDEX-BALANCING/blob/main/Index_balancing.ipynb
