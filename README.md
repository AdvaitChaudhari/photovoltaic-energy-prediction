# PV generation & surplus – HS Ansbach

Real measured data from a building at Hochschule Ansbach: hourly irradiance (horizontal and vertical),
outdoor temperature and humidity, PV generation, and household consumption.

**What's in the notebook**
1. **Cleaning** of a messy German export (multi-row header, `;` separators, decimal commas, units row)
2. **EDA**: daily and seasonal patterns, correlations, PV output against irradiance and hour of day
3. **Model**: predict hourly PV generation from weather and time features (linear model on irradiance only, random forest, gradient boosting), with a time-based train/test split
4. **Surplus**: monthly PV generation against building consumption, and how many hours have a PV surplus

**Results**

Time-based split (the last 20 % of Jan 2020 – Apr 2022 is the test set):

| Model | MAE [kWh] | RMSE [kWh] | R² |
|---|---|---|---|
| Linear, irradiance only | 1.54 | 3.11 | 0.785 |
| Random forest | **1.07** | 2.65 | 0.843 |
| Gradient boosting | 1.09 | **2.55** | **0.855** |

- PV output correlates at 0.92 with horizontal irradiance and at 0.53 with temperature. The temperature link is mostly "sunny = warm". Physically, heat lowers module efficiency.
- PV generation exceeds the building's measured consumption in 41.6 % of all hours.

Files: `pv_energy_prediction.ipynb`, `SesKiPvEletric.csv`, report: `Gr_E_PV_Surplus_Prediction.pdf`

*University group project (Group E), M.Sc. Smart Energy Systems.*
