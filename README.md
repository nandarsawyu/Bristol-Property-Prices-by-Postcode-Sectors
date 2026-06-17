# Predicting Average Property Prices in Bristol by Postcode Sectors

**Student ID:** 24071045 | **Supervisor:** Dalila Khettaf  
**MSc Data Science Project** – University of the West of England (UWE)  
**Interactive Artifact:** `bristol_property_market_map.html`

---

## Project Overview
This project establishes an end-to-end data science framework to analyze, model, and predict average property prices across Bristol at the **Postcode Sector** level (e.g., `BS1 6`, `BS16 7`). By engineering a pipeline that fuses transaction records, spatial grids, and municipal crime data, this study uncovers localized neighborhood dynamics and deploys predictive machine learning models.

### Key Objectives:
* **Integrate & Clean:** Aggregate open-access datasets spanning property transactions, coordinates, and crime indexes.
* **Geospatial Feature Engineering:** Transform British National Grid coordinates (`easting`/`northing`) into standard GPS Latitude/Longitude.
* **Predictive Modeling:** Train and optimize machine learning regressors to forecast property values.
* **Geospatial Deployment:** Build a responsive, interactive HTML map featuring transaction heatmaps and collapsible data clusters.

---

## Data Sources & Pipeline Architecture
The analytical pipeline blends three primary open-government data streams:
1. **UK Land Registry (`bristol_properties_monthly.csv`):** Historical sales data tracking purchase price, property type, and transaction dates.
2. **Ordnance Survey Code-Point Open (`bs_cleaned.csv`):** Master lookup mapping alphanumeric postcodes to spatial grid coordinates.
3. **UK Open Crime Data (`bristol_master_crimes.csv`):** Monthly municipal offense records used to evaluate neighborhood safety impacts.

---

## Core Insights (EDA)
* **Price Skewness:** Bristol property valuations display a prominent right-skewed distribution, driven by high-value outliers.
* **Market Seasonality:** A positive correlation ($r = 0.314$) exists between sales volumes and crime occurrences, peaking systematically during summer cycles.
* **Safety & Valuation Link:** An inverse correlation ($r = -0.385$) confirms that macro property valuations adjust downwards in sectors experiencing high localized crime densities.

---

## Machine Learning & Performance
The dataset was split into an **80% Training / 20% Testing** framework. Missing structures were resolved inside an isolated pipeline using median imputation and standard scaling to prevent data leakage. 

An optimized **Random Forest Regressor** ensemble was deployed to map complex geographic and spatial-temporal interactions, outperforming traditional linear models.

### Test Performance Matrix:
| Metric | Model Score |
| :--- | :--- |
| **Mean Absolute Error (MAE)** | £42,150.20 |
| **Root Mean Squared Error (RMSE)** | £61,845.50 |
| **Coefficient of Determination ($R^2$)** | **0.7845** |

*Interpretation: The model successfully accounts for **78.45% of the total variance** in Bristol's property valuations based on spatial-temporal inputs.*

---

## Interactive Geospatial Dashboard
The project concludes with an interactive deployment built via **Folium**. It renders directly inside any standard web browser by opening `bristol_property_market_map.html`.

### Dynamic Map Layers:
* **Base Map Layer:** Centered directly over Bristol City Centre `[51.4545, -2.5879]`.
* **Sales Volume Heatmap:** Visualizes live real estate activity density gradients across the city.
* **Collapsible Marker Clusters:** Interactive map pins color-coded by market tier:
  * 🟣 **Purple:** Premium sectors ($>£450,000$)
  * 🔵/🟢 **Blue & Green:** Mid-market sectors ($£200,000 - £450,000$)
  * 🟠 **Orange:** Entry-level affordable sectors ($<£200,000$)
* **Custom Info Popups:** Clicking a marker renders a clean HTML card breaking down the area's **Sector ID, Average Property Price, Total Transactions,** and **Total Crime Count**.

---
