# PortfolioOptimiser
# Portfolio Optimization Tool

A Python implementation of Modern Portfolio Theory that constructs efficient frontiers and identifies optimal portfolio allocations using real-time market data. Developed as part of my self-directed learning in quantitative finance, complementing Rice University's Portfolio Management Specialization.

## 🎯 Project Overview

This tool automates the portfolio optimization process, from data collection through final reporting, enabling rapid analysis of multiple asset combinations. It implements Markowitz's mean-variance optimization framework with practical enhancements for real-world application.

**Key Features:**
- Real-time market data integration via Yahoo Finance API
- Geometric mean returns calculation for accurate compound growth representation  
- Maximum Sharpe ratio optimization using convex optimization
- Comprehensive risk metrics including annualized volatility and correlation analysis
- Automated Excel report generation with multi-sheet analytics
- Dynamic risk categorization based on volatility thresholds

## 📊 Technical Implementation

### Core Methodology

The optimizer employs several key financial concepts:

- **Returns Calculation**: Utilizes geometric mean rather than arithmetic mean to account for compounding effects over the 252-trading-day year
- **Risk Assessment**: Calculates annualized volatility using daily returns standard deviation scaled by √252
- **Optimization Engine**: PyPortfolioOpt's efficient frontier implementation to solve the quadratic programming problem
- **Covariance Matrix**: Full historical correlation analysis to assess diversification benefits

### Architecture Components

```
Input Layer:
├── User-specified tickers (comma-separated)
├── 1-year historical data window (configurable)
└── Current risk-free rate from 10-year Treasury

Processing Layer:
├── Individual asset analysis (return, volatility, Sharpe)
├── Portfolio correlation matrix construction
├── Efficient frontier generation
└── Optimal weight calculation

Output Layer:
├── Optimized portfolio weights
├── Performance metrics (return, volatility, Sharpe)
├── Risk categorization
└── Excel report with complete analytics
```

## 🚀 Installation & Usage

### Prerequisites
```bash
pip install pandas numpy yfinance scipy matplotlib pypfopt xlsxwriter
```

### Basic Usage
```python
python portfolio_optimizer.py

# Example input when prompted:
# Enter tickers: VOO,BLV,VWO,IYR,VCEB,IVE
# Enter filename: optimization_results.xlsx
```

### Sample Portfolio Analysis

The tool can analyze various portfolio compositions:
- **Equity-focused**: SPY, QQQ, IWM, EFA, EEM
- **Balanced**: VOO, AGG, GLD, VNQ, VTEB  
- **Sector-specific**: XLK, XLF, XLV, XLE, XLI

## 📈 Performance Metrics

### Optimization Results (Sample Portfolio)
Based on backtesting with a diversified ETF portfolio:
- **Sharpe Ratio**: 1.17 (capstone project achievement)
- **Risk Reduction**: 23% volatility decrease vs. equal-weight
- **Processing Time**: <30 seconds for 6-asset optimization
- **Annual Rebalancing**: Consistent outperformance in backtests

### Risk Categorization Framework
- **Low Risk**: Annualized volatility < 5%
- **Moderate Risk**: Annualized volatility 5-15%  
- **High Risk**: Annualized volatility > 15%

## 💻 Code Structure

### Key Functions

```python
# Data Collection
yf.download(tickers, start=start_date, end=end_date)

# Returns Calculation  
geometric_mean = gmean(daily_returns + 1) - 1
annualized_return = (1 + geometric_mean)**252 - 1

# Risk Metrics
daily_volatility = returns.std()
annual_volatility = daily_volatility * np.sqrt(252)

# Optimization
ef = EfficientFrontier(mu, S, weight_bounds=(0, 1))
weights = ef.max_sharpe()
```

### Output Format

The Excel report contains four integrated sheets:
1. **Analysis**: Individual asset metrics and risk categorizatio
