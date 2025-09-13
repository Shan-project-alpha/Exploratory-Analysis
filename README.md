# PortfolioOptimiser
# Portfolio Optimization Tool

A Python implementation of Modern Portfolio Theory that constructs efficient frontiers and identifies optimal portfolio allocations using real-time market data. Developed as part of my self-directed learning in quantitative finance, complementing Rice University's Portfolio Management Specialization.

## 🎯 Project Overview

This tool automates the portfolio optimization process, from data collection through final reporting, enabling rapid analysis of multiple asset combinations. It implements Markowitz's mean-variance optimization framework with practical enhancements for real-world application.

**Key Features:**
- Real-time market data integration via Yahoo Finance API
- Geometric mean returns calculation for accurate compound growth representation  
- Maximum Sharpe ratio optimization 
- Comprehensive risk metrics including annualized volatility and correlation analysis
- Automated Excel report generation with analytics
- Dynamic risk categorization based on volatility thresholds

## 📊 Technical Implementation

### Core Methodology

The optimizer employs several key financial concepts:

- **Returns Calculation**: Utilizes geometric mean rather than arithmetic mean to account for compounding effects over the 252-trading-day year
- **Risk Assessment**: Calculates annualized volatility using daily returns standard deviation scaled by √252
- **Optimization Engine**: PyPortfolioOpt's efficient frontier implementation to solve the quadratic programming problem
- **Covariance Matrix**: Full historical correlation analysis to assess diversification benefits

## Installation & Usage

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
- **Equity-focused**: SPY, QQQ, IWM
- **Sector-specific**: XLK, XLF, XLV, XLE, XLI

### Risk Categorization Framework
- **Low Risk**: Annualized volatility < 5%
- **Moderate Risk**: Annualized volatility 5-15%  
- **High Risk**: Annualized volatility > 15%
