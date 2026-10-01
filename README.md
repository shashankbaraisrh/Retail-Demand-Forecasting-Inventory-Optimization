# Retail Demand Forecasting & Inventory Optimization

## Project Overview

An end-to-end data science solution for retail demand forecasting and inventory replenishment. The project combines statistical forecasting, machine learning, inventory analytics, and constrained optimization to support data-driven ordering decisions.

## Business Problem

Retail demand varies by product, store, season, price, discount, and promotions. Poor demand estimation can lead to:

- Stockouts and lost sales
- Excess inventory and higher holding costs
- Inefficient replenishment decisions

The objective is to forecast future demand and convert those forecasts into practical inventory replenishment recommendations.

## Dataset

The project uses a synthetic daily retail dataset containing:

- 76,000 records
- 5 stores
- 20 products
- 5 categories
- 4 regions
- Daily observations from January 2022 to January 2024

Key variables include sales, demand, inventory levels, prices, discounts, promotions, competitor pricing, weather, and seasonality.

## Methodology

### 1. Data Preparation
- Data quality and completeness checks
- Date conversion and validation
- Duplicate and missing-value analysis
- Store-product data validation

### 2. Exploratory Data Analysis
- Demand distribution
- Category and store-level demand patterns
- Promotion and discount analysis
- Seasonal demand patterns
- Price and competitor pricing relationships

### 3. Feature Engineering

Created time-series features including:

- Lag 1, 7, 14 and 28 days
- Rolling mean demand over 7, 14 and 28 days
- Month, day of week and week of year
- Product, store, region, promotion and seasonality features

Rolling features were shifted to prevent data leakage.

### 4. Demand Forecasting

Three forecasting approaches were evaluated:

- 7-day seasonal naive baseline
- SARIMA statistical time-series model
- XGBoost machine learning model

A chronological train-test split was used to reflect a real forecasting scenario.

### 5. Model Evaluation

Models were evaluated using:

- MAE
- RMSE
- WMAPE

XGBoost achieved:

| Metric | XGBoost |
|---|---:|
| MAE | 18.38 |
| RMSE | 24.70 |
| WMAPE | 18.39% |

The XGBoost model improved substantially over the 7-day baseline on the test dataset.

### 6. Inventory Analytics

The forecasting results were combined with inventory concepts including:

- Lead-time demand
- Demand variability
- Safety stock
- Reorder point
- Target stock level

A 3-day supplier lead time and a 1.645 service-level z-score were used for the inventory demonstration.

### 7. Replenishment Optimization

SciPy optimization was used to determine replenishment quantities under a maximum supplier order capacity.

The optimization objective balances:

- Ordering cost
- Shortage cost
- Current inventory
- Target stock requirements
- Supplier capacity constraints

## Project Workflow

```text
Retail Data
    ↓
Data Cleaning
    ↓
Exploratory Data Analysis
    ↓
Feature Engineering
    ↓
Chronological Train/Test Split
    ↓
Baseline / SARIMA / XGBoost
    ↓
Model Evaluation
    ↓
Demand Forecast
    ↓
Lead-Time Demand
    ↓
Safety Stock
    ↓
Reorder Point
    ↓
Target Stock
    ↓
Replenishment Optimization
    ↓
Recommended Order Quantity