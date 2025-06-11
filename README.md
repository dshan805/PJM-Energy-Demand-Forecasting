# PJM-Energy-Demand-Forecasting

## Overview

This project attempts to forecast hourly power demand (MW) in the PJM East region. The goal is to improve grid operations and reduce losses from over- or under-forecasting. Accurate demand forecasts help with resource allocation, market decisions, and scheduling.

## Data

- Source: [PJM Hourly Energy Consumption Data](https://www.kaggle.com/datasets/robikscube/hourly-energy-consumption) from Kaggle.
- Data: Historical hourly power consumption (MW) from PJM Interconnection LLC. This covers parts of 13 states and Washington, D.C.

## Methodology

1. **Data Preprocessing**
   - Load the data
   - Clean missing values

2. **Feature Engineering**
   - Time-based features: hour, day of week, month, year, etc.
   - Lag features: previous hour (`lag_1`), previous day (`lag_24`), previous week (`lag_168`).

3. **Modeling**
   - Prophet (trend/seasonality model)
   - XGBoost (tree-based regression using all features)

4. **Evaluation**
   - Metrics: Mean Absolute Error (MAE), Root Mean Squared Error (RMSE)

## Results

- **XGBoost**: MAE ≈ 349 MW (~1.1% of average demand), RMSE ≈ 463 MW
- **Prophet**: MAE ≈ 609 MW, RMSE ≈ 792 MW
- Average demand: 32,080 MW
- Standard deviation: 6,464 MW

Both models predict well below the natural variability of the system. XGBoost performs better than Prophet.

## Limitations and Next Steps

- The models do not use weather, holidays, or event data. Errors are larger during demand spikes or unusual periods.
- Next steps: Add weather and event features. Set up continuous model monitoring. Track business-relevant error thresholds.

## How to Run

1. Clone the repository:
    ```
    git clone <your-repo-url>
    cd <your-repo-name>
    ```

2. Install dependencies (use a virtual environment if possible):
    ```
    pip install pandas numpy scikit-learn xgboost matplotlib seaborn prophet kaggle
    ```

3. Download the data from Kaggle and place it in the correct folder.

4. Start Jupyter Notebook:
    ```
    jupyter notebook energy_projection.ipynb
    ```
    Run all cells to reproduce results.

---

