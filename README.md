# Predicting Average Property Prices in Bristol by Postcode Sectors

**MSc Data Science Project – University of the West of England (UWE Bristol)**

## Project Overview

This project develops a data-driven framework to analyse and predict residential property prices across Bristol at the **postcode-sector level**. It integrates UK Land Registry property transactions, Ordnance Survey geographic data, and ONS demographic data to investigate spatial and temporal patterns in the Bristol housing market.

## Key Objectives

- Clean and integrate property, geographic, and demographic datasets.
- Analyse house-price distributions, trends, and spatial patterns.
- Engineer postcode-level geographic and transaction features.
- Develop and compare regression and machine-learning models.
- Evaluate model performance using MAE, RMSE, and R².
- Visualise predicted prices and spatial clusters using an interactive Folium map.

## Data Sources

- **UK Land Registry Price Paid Data** – property transaction prices and characteristics.
- **Ordnance Survey Code-Point Open** – postcode geographic coordinates.
- **Office for National Statistics (ONS)** – population and demographic information.

## Key Findings

- Bristol property prices show a strong **right-skewed distribution**.
- Average prices generally increased between **2015 and 2024**, with a notable change around 2021.
- Property prices exhibit substantial **spatial variation**, with higher-priced areas concentrated around central Bristol.
- Population and demographic variables have relatively weak individual relationships with property prices.
- Transaction volume (`n_sales`) was the most influential feature in the final model.

## Machine Learning

Several models were evaluated, including Linear Regression, Ridge, Lasso, HistGradientBoosting, and Random Forest.

The final **RandomForest_fast** model achieved:

| Metric | Result |
|---|---:|
| MAE | £126,525 |
| RMSE | £376,403 |
| R² | -1.04 |

The results demonstrate the challenges of predicting postcode-sector property prices using a limited set of demographic, spatial, and transaction features.

## Interactive Map

A **Folium-based interactive map** was developed to visualise postcode-sector results across Bristol. The map includes:

- Postcode-sector locations
- Spatial cluster colours
- Transaction-volume-based marker sizes
- Median and predicted prices
- Number of transactions
- Interactive popups and tooltips

### Dynamic Map Layers:
* **Base Map Layer:** Centered directly over Bristol City Centre `[51.4545, -2.5879]`.
* **Postcode-Sector Markers:** Each postcode sector is represented by a coloured circle. Marker size reflects the number of property transactions (`n_sales`).
* **Cluster Colours:** Colours represent the **spatial cluster assigned to each postcode sector**, rather than fixed affordable or premium price categories:
  * 🔴 **Red:** Cluster 0
  * 🔵 **Blue:** Cluster 1
  * 🟢 **Green:** Cluster 2
  * 🟣 **Purple:** Cluster 3
  * 🟠 **Orange:** Cluster 4
  * 🩷 **Pink:** Cluster 5
  * 🔷 **Cadet Blue:** Cluster 6
  * 🔴 **Dark Red:** Cluster 7
  * 🔵 **Dark Blue:** Cluster 8
* **Custom Info Popups:** Clicking a marker displays the **Postcode Sector, Cluster, Median Property Price, Predicted Property Price,** and **Number of Sales**.
* **Interactive Tooltips:** Hovering over a marker displays the corresponding postcode sector.

The colour scheme is used to distinguish the different **spatial clusters identified during the analysis**. It should not be interpreted as a direct ranking of property affordability or market value; the predicted and median prices are provided separately in the interactive popups.

## Technologies

`Python` · `Pandas` · `NumPy` · `Scikit-learn` · `Matplotlib` · `Seaborn` · `Folium` · `Google Colab`

## Limitations & Future Work

The model is limited by the absence of detailed housing characteristics, income indicators, amenity data, and explicit spatial modelling. Future work could incorporate richer property and neighbourhood features, spatial machine-learning methods, and time-aware modelling approaches.

## Project

**GitHub:** https://github.com/s2-nandar/Predicting-Average-Property-Prices-in-Bristol-by-Postcode-Sectors.git
