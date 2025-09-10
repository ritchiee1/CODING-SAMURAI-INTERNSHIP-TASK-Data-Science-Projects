# 📈 Coding Samurai Internship Project - Task 5  
### Time Series Forecasting for Apple (AAPL) Stock Prices Using ARIMA

---


## Table of Contents
1. [Project Scope](#project-scope)  
2. [Project Objectives](#project-objectives)  
3. [Expected Outcome](#expected-outcome)  
4. [Document Purpose](#document-purpose)  
5. [Use Case](#use-case)  
6. [Data Source](#data-source)  
7. [Data Cleaning and Processing](#data-cleaning-and-processing)  
8. [Data Analysis](#data-analysis)  
9. [Data Visualization](#data-visualization)  
10. [Insights](#insights)  
11. [Recommendation](#recommendation)  
12. [Conclusion and Future](#conclusion-and-future)  
13. [Link](#link)

---

## Project Scope
This project focuses on forecasting **Apple Inc. (AAPL) stock prices** using the **ARIMA time series model**.  
It demonstrates the end-to-end pipeline of data acquisition, cleaning, modeling, evaluation, and prediction. 

---

## Project Objectives
- Acquire and preprocess Apple stock price data (2020–2025).  
- Test for stationarity.  
- Build and tune an ARIMA model for forecasting.  
- Evaluate the model using statistical metrics.  
- Generate forecasts for future stock prices.
- Insights and Future Recommendation 

---

## Expected Outcome
- A reliable ARIMA model for predicting Apple stock prices.
- Visualization of historical data and ARIMA forecasts. 
- Visualizations comparing **actual vs predicted values**.  
- Forecast for the next 60 business days (~3 months).   
- Evaluation metrics (RMSE, MAE) to measure performance and also accuracy check using average error.  

---

## Document Purpose
This document provides the methodology, workflow, and results of using ARIMA to forecast Apple stock prices. It highlights key findings and recommendations for market analysis.

---

## Use Case
- **Investors / Traders:** Use the ARIMA forecast as a statistical baseline to confirm or reject short-term trade ideas.  
- **Analysts:** Quick baseline forecasting and diagnostics of risk assessment.  
- **Data Scientists / Students:** Reference for building and evaluating classical time-series models and for comparing against advanced approaches.
- Recruiters and employers can assess **skills in Python, statistics, and modeling**.  

---

## Data Source
- Extracted from **Yahoo Finance** using the Python library **`yfinance`**. 
- Timeframe: 2020-05-05 to 2025-05-05
- Extraction is programmatic; no manual CSV downloads.
- Features extracted:
  - `Date`  
  - `Open`  
  - `High`  
  - `Low`  
  - `Close`  
  - `Adj Close`  
  - `Volume`  

---

## Data Cleaning and Processing
- Extracted using yfinace using `yf.Ticker("AAPL")`.
- Checked dataset info, datatypes, and missing values. 
- Explored the dataset, summary statistics and visualization.
- Split dataset into **80% training** and **20% testing**. 
- Focused the modeling on the `Close` price as the target series for ARIMA. 
- Stationarity Check using visualizations and standard statistical tests.
- Split the dataset into training and test sets for evaluation 

---

## Data Analysis
This analysis was performed using **VS Code**, leveraging libraries such as **pandas**, **seaborn**, **matplotlib**, and **statsmodels**.
- Model evaluation metrics on test set:  
  - **MAE:** 2.8149  
  - **RMSE:** 4.2445  
  - **MAPE:** 1.30%  
  - **Accuracy:** 98.70%

  ### Future Forecast (60 Business Days)  
**First 5 Predictions:**  
- 2025-05-06 204.88
- 2025-05-07 204.85
- 2025-05-08 204.93
- 2025-05-09 205.07
- 2025-05-12 205.16

**Last 5 Predictions:**  
- 2025-07-22 208.25
- 2025-07-23 208.23
- 2025-07-24 208.26
- 2025-07-25 208.24
- 2025-07-28 208.27


---

## Data Visualization
- ![Plotted historical closing prices](apple_closing_price.png)
**Apple Closing Prices**

- ![Compared Apple Stock Closing Price with Rolling Mean & Std Dev for Stationarity check](apple_closing_price_vs_mean_and_avg.png)
   **Apple Closing Price vs Mean & Std Dev**

- ![Compared predicted vs actual values](actual_vs_predited.png)
**Actual vs Predicted**

- ![Visualized future ARIMA’s forecasts](future_forecast.png) 
**Future Forecast**

---

## Insights
**Technical Insights**
- **Stationarity:** The raw closing price was non-stationary and required differencing. This supports using `d = 2` in ARIMA for the tested period.  
- **Model Behavior:** The ARIMA(3,2,3) model provided a **good fit** for the data.   
- **Metrics:** Evaluation metrics show **high accuracy (98.7%)**, which suggest small overfitting.   
- **Forecast Intervals:** Predictions indicate **gradual upward movement with fluctuations**.  
**Performance Observations**
- ARIMA provides a solid baseline for forecasts but typically underperforms in capturing sudden, news-driven moves or structural breaks.
- ⚠️ Forecasts are for **educational purposes only** and should not guide financial decisions.  

---

## Recommendation
- Explore **SARIMA / SARIMAX** for seasonality.  
- Consider **LSTM or advanced deep learning models** for nonlinear patterns.  
- Incorporate **external variables** (macroeconomic indicators, company news) for improved accuracy.  

---

## Conclusion and Future
This project successfully demonstrated the use of ARIMA for stock price forecasting, achieving strong accuracy and producing short-term forecasts.  
Future work can extend to **multi-model comparisons** and **ensemble forecasting**.  
 

---

## Link

- GitHub Repository: [[Github Repo Link](https://github.com/ritchiee1/CODING-SAMURAI-INTERNSHIP-TASK-Data-Science-Projects/tree/main/Task_2%20TimeSeries_StockForecast)](#)

