BBCA Stock Price Forecasting with Time-Series Models
A Data Science group project analyzing historical closing prices of Bank Central Asia (BBCA) and comparing time-series forecasting approaches to understand price trends and evaluate forecasting performance.
Project Overview
Stock prices change over time and can be affected by market conditions and unexpected events. This project explores historical BBCA stock data through exploratory data analysis (EDA), time-series decomposition, stationarity testing, forecasting, and model comparison.

Objectives
- Explore historical BBCA stock prices and trading volume.
- Examine daily returns, rolling averages, and time-series components.
- Test stationarity after removing the seasonal component.
- Compare statistical time-series methods with an XGBoost regression model.
- Evaluate forecasting results using Mean Squared Error (MSE) and Mean Absolute Percentage Error (MAPE).

Dataset
The project uses historical BBCA stock data provided as CSV files. The main BBCA dataset contains these columns:
- Date
- Close
- Open
- High
- Low
- Volume
- Percentage Change %
The notebook reports 3,200 observations and checks for missing values. Data preparation includes converting dates to datetime, sorting observations chronologically, converting OHLC values to integer price values, and cleaning volume values.
The repository also includes a historical Jakarta Stock Exchange Composite dataset. Refer to the notebooks and CSV files for the exact data used in each analysis.

Workflow
1. Data preparation — load the CSV data, inspect data types and missing values, parse dates, sort by date, and clean numeric fields.
2. Exploratory data analysis — visualize closing prices, the 20-day rolling mean, daily-return distribution, and trading volume.
3. Time-series analysis — decompose the closing-price series into trend, seasonal, and residual components, then run the Augmented Dickey–Fuller (ADF) test on the deseasonalized series.
4. Model development — fit and compare ARIMA, SARIMA, Simple Exponential Smoothing (SES), Holt Linear, Holt-Winters, and XGBoost.
5. Evaluation — compare model forecasts with test data using MSE and MAPE and visualize the forecast comparison.

Models Compared
Model	Purpose
ARIMA	Baseline statistical time-series forecasting
SARIMA	ARIMA with seasonal components
Simple Exponential Smoothing (SES)	Forecasting with different smoothing factors (alpha values)
Holt Linear	Exponential smoothing for trend-oriented series
Holt-Winters	Exponential smoothing with trend and seasonal components
XGBoost	Gradient-boosted tree regression for forecasting


Results
The notebook's final comparison reports the following MAPE values:
Model	MAPE reported
ARIMA	40.98%
SARIMA	40.99%
SES (α = 0.05)	38.28%
SES (α = 0.1)	40.34%
SES (α = 0.2)	47.71%
SES (α = 0.3)	57.96%
SES (α = 0.5)	80.48%
SES (α = 0.7)	100.08%
SES (α = 0.9)	115.81%
SES (α = 1.0)	122.61%
Holt Linear	13.18%
Holt-Winters	44.23%
XGBoost	1.80%


Based on the notebook's final comparison table, XGBoost has the lowest reported MAPE (approximately 1.80%) among the listed models.

The notebook also reports an ADF-test p-value of 0.2193 for the deseasonalized series, so the test does not provide sufficient evidence to classify that series as stationary at the 5% significance level.

Evaluation note: These values are reproduced from the project notebook. The notebook contains multiple modeling sections and preprocessing paths, so the reported metrics should be interpreted in the context of their respective evaluation steps rather than as a fully standardized benchmark. In particular, MSE values may not be directly comparable if models were evaluated on differently scaled targets or test series.
Tools & Libraries
- Python
- Pandas and NumPy
- Matplotlib and Seaborn
- Statsmodels
- pmdarima
- Scikit-learn
- XGBoost

How to Run
1. Clone or download this repository.
2. Install the required Python libraries listed above (and pmdarima if running the ARIMA/SARIMA sections).
3. Open the Jupyter Notebook in Jupyter Notebook, JupyterLab, or Google Colab.
4. Update the CSV file paths in the notebook to match your local environment.
5. Run the notebook cells in order.

Example installation command:
pip install pandas numpy matplotlib seaborn statsmodels pmdarima scikit-learn xgboost jupyter

Limitations
- Historical price patterns do not guarantee future performance.
- Results depend on the selected data period, preprocessing steps, and model configuration.
- The notebook uses local file paths that must be updated before running in another environment.
- This is an academic forecasting project, not financial advice or a recommendation to buy or sell securities.
