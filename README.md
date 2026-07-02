# Food Delivery Time Prediction

A machine learning model that predicts food delivery response times using order details, weather, and live traffic data.

## What it does

- Pulls live weather (OpenWeatherMap) and traffic/route data (TomTom, OpenRouteService) for each delivery.
- Engineers features from restaurant/delivery coordinates, encodes categorical fields, and reduces dimensionality with PCA.
- Trains an XGBoost regressor to predict delivery response time.
- Evaluates with MAE, RMSE, and R².

## Tech stack

- pandas, scikit-learn, XGBoost, MySQL, matplotlib, seaborn

## Setup

This project calls external APIs and a local MySQL database. Set the following environment variables before running:

```bash
export OPENWEATHER_API_KEY=your_key
export TOMTOM_API_KEY=your_key
export ORS_API_KEY=your_key
export DB_USER=root
export DB_PASSWORD=your_password
```

```bash
pip install pandas numpy scikit-learn xgboost matplotlib seaborn mysql-connector-python requests ydata-profiling
python PROJECT.PY
```

## Project structure

| File | Purpose |
|---|---|
| `PROJECT.PY` | Main pipeline: EDA, feature engineering, model training/evaluation |
| `new_code_traffic_time.py` | Batch script to enrich a CSV with travel-time data via OpenRouteService |
| `Filled_missing_value.csv`, `Ordinal_encoded.csv`, `temp_csv.csv` | Intermediate processed datasets |
| `..._REPORT.pdf`, `..._PPT.pptx` | Project write-up and presentation |

## Note on API keys

Earlier versions of this project had API keys committed in source. They have been moved to environment variables — if you're reusing this code, generate your own keys rather than relying on any values from git history.
