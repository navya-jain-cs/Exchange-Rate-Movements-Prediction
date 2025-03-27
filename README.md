# Predictive Model for Exchange Rate Movements

## Project Overview

This project aims to predict short-term exchange rate movements using historical financial data and economic indicators. The approach includes data acquisition, preprocessing, feature engineering, model training, and evaluation. The models used include Ridge Regression, Random Forest, XGBoost, and LSTM.

## Dataset Sources

The data for this project was sourced from a combination of real-time APIs and local CSV files:

### APIs Used:
- Alpha Vantage
- FRED (Federal Reserve Economic Data)
- API Ninjas
- Open Exchange Rates

### CSV Files:
- `currency_exchange_rate.csv` (Daily USD/INR exchange rates)
- `interest_rates.csv` (Monthly interest rates for the USA & India)
- `inflation_rates.csv` (Monthly inflation rates for the USA & India)
- `gdp_growth_rates.csv` (Quarterly GDP growth data for the USA & India)
- `stock_price_data.csv` (Daily stock market indices - NIFTY & S&P 500)
- `trade_balance.csv` (Monthly trade balance data for both countries)
- `unemployment_rate.csv` (Monthly unemployment rates for the USA & India)
- `us_dollar_index.csv` (Monthly US Dollar Index values)

## Methodology

### 1. Data Collection
- Extracted exchange rate and economic indicator data from APIs and CSV files.
- Automated real-time data fetching where possible.

### 2. Data Preprocessing
- Cleaned missing values and handled outliers.
- Normalized and standardized data using MinMaxScaler and StandardScaler.
- Engineered new features, including:
  - Lag features (previous day’s exchange rates and key economic indicators).
  - Moving averages and volatility calculations.
  - Percentage changes in exchange rates and stock indices.

### 3. Model Building
- Implemented and trained multiple models:
  - Ridge Regression
  - Random Forest
  - XGBoost
  - LSTM (Long Short-Term Memory)
- Used chronological train-validation-test splitting to avoid data leakage.
- Optimized hyperparameters using GridSearchCV, RandomizedSearchCV and manually.

### 4. Model Evaluation
- Used Root Mean Squared Error (RMSE) and Mean Absolute Error (MAE) for performance evaluation.
- Compared model performances and selected the best-performing model for predictions.

### 5. ETL Pipeline
- Processed data from CSV files and APIs, ensuring consistency in formatting.
- Merged datasets and stored processed data in structured CSV files (`merged_data.csv`, `processed_data.csv`).
- Automated fetching and updating of new data when available.

## Results

| Model         | RMSE  | MAE  |
|--------------|------|------|
| Ridge        | 0.0055 | 0.0027 |
| Random Forest | 1.4762 | 0.0107 |
| XGBoost      | 1.5384 | 0.0116 |
| LSTM         | 0.0251 | 0.0156 |


## Instructions to Run the Code

### 1. Setup
Ensure you have Python installed along with the required dependencies. Install dependencies using:

```bash
pip install -r requirements.txt
```

### 2. Directory Structure
```plaintext
project-directory/
│── currency_exchange_rate.csv
│── gdp_growth_rates.csv
│── inflation_rates.csv
│── interest_rates.csv
│── stock_price_data.csv
│── trade_balance.csv
│── unemployment_rate.csv
│── us_dollar_index.csv
│── Data_Collection.ipynb
│── Data_Merge.ipynb
│── Data_Preprocessing.ipynb
│── ETL.ipynb
│── Model_Training.ipynb
│── best_random_forest_model.pkl
│── best_ridge_model.pkl
│── best_xgb_model.pkl
│── lstm_exchange_rate_model.h5
│── minmax_X.pkl
│── minmax_y.pkl
│── standard_X.pkl
│── standard_y.pkl
│── processed_data.csv
│── datasets/
```

### 3. Running the Project

#### Data Collection
Run `Data_Collection.ipynb` to fetch and store raw data.

#### Data Preprocessing
Execute `Data_Preprocessing.ipynb` to clean and process the data.

#### Model Training
Open `Model_Training.ipynb` to train models and generate predictions.

#### ETL and Predictions
Open 'ETL.ipynb' to generate predictions from the trained model.

### 4. Visualization
Run the visualization scripts in `Model_Training.ipynb` to generate graphs comparing actual vs. predicted values.
Run the visualization scripts in `data_Preprocessing.ipynb` to generate histograms and boxplots.

#### Key plots:
- Scatter plot (Actual vs. Predicted exchange rates)
- Time series plot (Exchange rate trends over time)

## Future Improvements
- Incorporate SQL for better structured data storage and retrieval.
- Expand dataset with additional macroeconomic indicators.
- Improve deep learning models (e.g., experimenting with different LSTM architectures).
- Deploy as a web API for real-time predictions.

---

