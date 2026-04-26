# Hierarchical Forecasting of Indian Air Traffic
Forecasting India's air traffic volume with reconciliation across the national, airport and route hierarchy using the Minimum Trace (MinTrace) method.

## Motivation
Air traffic volume forecasts are required at varying degree of granularity. At the national level, the total volume is required for macro planning. At the airport level, these forecasts are used for capacity planning. At the route level, the forecasts are used for scheduling airlines. Independent forecasts at each level are prone to inconsistency. Airport forecasts won't add up to the national forecast. This project aims to solve this problem by applying hierarchical reconciliation to the forecasts, ensuring they are coherent at all levels.

## Data
The monthly domestic city-pair passenger traffic data is sourced from Directorate General of Civil Aviation (DGCA), India via the [Vonter/india-aviation-traffic](https://github.com/Vonter/india-aviation-traffic) dataset (ODbL - 1.0)

- **Coverage:** April 2015 to February 2026
- **Granularity:** Monthly, directional (City 1 -> City 2)
- **Cities:** Approx. 134 airports
- **Routes:** Approx. 1855 unique city pairs

## Approach
1. **Hierarchy Design:** Three levels - Total (at national level), Origin Airport level, Origin - Destination route level
2. **Base Forecasts:** Naive, SeasonalNaive, AutoARIMA, ETS and gradient-boosted models (LightGBM) at each hierarchy level
3. **Reconciliation:** Minimum Trace Method aka MinTrace (Wickramasuriya, Athanasopoulos & Hyndman, 2019) to enforce coherence
4. **Evaluation:** Backtest on holdout window with MASE and RMSE

## Analytics Stack
`pandas`, `statsforecast`, `hierarchicalforecast`, `lightgbm`, `matplotlib`

##  Repo Structure
```
data/
    raw/ # source CSV from DGCA via Vonter dataset (gitignored)
    processed/ # cleaned, hierarchy-ready data
notebooks/ # EDA and modelling experiments
src/ # reusable modules: data preparation, forecasting and reconciliation
outputs/ # charts, tables, results (gitignored)
```
## Status
Active build - sprint April 2026

## Author
Rahul Mohan - Senior Consultant, EY-Parthenon | PG Diploma in Advanced Business Analytics, IIM Ahmedabad

## Attribution
Data: DGCA (https://www.dgca.gov.in/) via [Vonter/india-aviation-traffic](https://github.com/Vonter/india-aviation-traffic), ODbL-1.0.