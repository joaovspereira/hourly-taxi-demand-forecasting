# Hourly Taxi Demand Forecasting

Time-series forecasting project for airport taxi demand.

## Business problem
Sweet Lift Taxi wants to attract more drivers during peak periods by predicting the number of orders for the next hour.

## Objective
Achieve **test RMSE ≤ 48**.

## Executed results
| Model | Test RMSE |
|---|---:|
| **LightGBM** | **41.01** |
| Random Forest | 44.05 |
| Linear Regression | 45.81 |

The selected LightGBM configuration saved in the notebook is:
`n_estimators=200`, `learning_rate=0.05`, `max_depth=7`.

## Methodology
Hourly resampling, trend/seasonality analysis, calendar features, 24 lag features, 24-hour rolling mean, leakage prevention and `TimeSeriesSplit`.

## Technologies
Python · pandas · NumPy · statsmodels · scikit-learn · LightGBM · Matplotlib

## Repository structure
- [notebooks/hourly_taxi_demand_forecasting.ipynb](notebooks/hourly_taxi_demand_forecasting.ipynb)
- [data/README.md](data/README.md)
- [requirements.txt](requirements.txt)

## Next steps
Rolling-origin backtesting, prediction intervals and monitoring performance by hour and peak-demand period.

## Run locally

Clone the repository, enter its directory and create an environment:

```bash
git clone https://github.com/joaovspereira/hourly-taxi-demand-forecasting.git
cd hourly-taxi-demand-forecasting
python -m venv .venv
```

Activate it with `source .venv/bin/activate` on macOS/Linux or `.\.venv\Scripts\Activate.ps1` in Windows PowerShell. Then run:

```bash
python -m pip install -r requirements.txt
python -m notebook notebooks/hourly_taxi_demand_forecasting.ipynb
```

Place the original datasets listed in [data/README.md](data/README.md) inside `data/` before executing cells. Dataset files are excluded from version control.

## Evaluation scope

These are saved results from the original execution. The last 10% of observations form the test set. Forecasts are one hour ahead and use previously observed demand, including observations that become available during the test period. This is not a recursive forecast of the entire test horizon. Exploratory plots cover the full series; future evaluation should include an untouched period and a seasonal-naive baseline.

The publication review checked notebook structure and code syntax, but did not rerun the full training process or establish exact environment reproducibility.

## Learning

This project was developed during the TripleTen Data Science bootcamp. It demonstrates a documented analytical workflow, explicit evaluation criteria and interpretation of model limitations.
