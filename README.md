# Using Time Series Analysis for Sales & Demand forecasting
The objective of this project was to identify sales patterns that demonstrate seasonal trends or any other traits, providing insights to inform reordering, restocking, and reprinting decisions for books based on their ISBN. Forecasting book sales and modelling demand was achieved by applying a range of time series analysis techniques - ARIMA, Deep Learning, and Hybrid Methods.


## 🟡 Data
The project utilised two datasets from Nielsen's BookScan repository:
* ISBN list containing industry-standard metadata about each book
* UK weekly trended timeline containing sales data

The data was filtered on books with sales beyond 01-07-2024, producing a list of 61 unique ISBNs, from which two were chosen for in-depth analysis: <ins>The Alchemist & The very hungry Caterpillar</ins>.

## 🟡 Methodology
* Imported both datasets, resampled weekly sales data to ensure missing weeks are filled with zeros, and converted ISBNs to strings and dates to datetime objects.
* Filtered out ISBNs with sales data beyond 01-07-2024, displayed these ISBNs, and plotted their sales.
* Investigated the general sales patterns across different time periods (1-12 years vs. 12-24 years) and analysed possible reasons for any noticeable changes.
* Selected two specific books and filtered their data from 2012 onwards for further forecasting.
* Performed time series decomposition, **ACF/PACF analysis**, and **stationarity checks** for both books. Used **Auto ARIMA** to identify the best model and forecasted the final 32 weeks of data.
* Prepared the data for ML models, created an **XGBoost pipeline** using sktime, tuned parameters using **GridSearch and RandomSearch**, and forecasted the final 32 weeks for both books.
* Built and tuned **LSTM models** using **KerasTuner**, forecasted the final 32 weeks, and evaluated the performance using **MAE and MAPE**.
* Applied both **sequential and parallel hybrid models** combining **SARIMA and LSTM**, tuned the models, and evaluated their performance using various metrics.
  * Sequential - SARIMA residuals modelled with LSTM
  * Parallel - weighted average of SARIMA and LSTM predictions
* Aggregated weekly to monthly data, trained XGBoost and SARIMA models to forecast 8 months, and compared results with weekly predictions.

## 🟡 Tools
* Pandas, NumPy, Datetime, SciPy, Matplotlib, Seaborn
* Statsmodels, pmdarima, sktime, Scikit-learn, XGBoost
* Keras/TensorFlow, KerasTuner, Hyperopt

## 🟡 Results and Findings
* Both the weekly and monthly predictions for the XGBoost and SARIMA models were able to capture the patterns of the data, but struggled in accurately modelling the variance experienced at the peaks of the time series.
* The evaluation scores confirmed the superiority of the Hybrid models in modelling and predicting sales volumes. (to insert table)
* The weekly predictions showed a more granular breakdown and a more accurate modelling of the paterns than the monthly, but the overall trend remained the same.
