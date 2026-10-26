
# 📈 DSMarket: Forecasting & Stock Optimization

> **Master's Capstone Project - Nuclio Digital School**

This repository contains the complete development of an end-to-end Data Science solution for **DSMarket**, a retail company. The primary objective is to optimize stock logistics and strategic decision-making through predictive sales modeling and advanced product segmentation.

## 📋 Business Context

DSMarket is a fictional retail chain operating across the East Coast of the United States. To maintain competitiveness, the company is modernizing its inventory management, shifting from reactive methods to a data-driven, predictive approach.

* **Scope:** 10 Physical Stores.
* **Locations:** 3 Cities (New York, Boston, Philadelphia).
* **Catalog:** Thousands of SKUs divided into 3 main categories:
  * 💍 *Accessories*
  * 🏠 *Home & Garden*
  * 🛒 *Supermarket*
* **Challenge:** Predict future sales at the *store-item* level to minimize "out-of-stock" scenarios and reduce overstock costs.

## 🔄 Methodology & Workflow

The project is structured across several notebooks covering the entire data lifecycle, from ingestion to final prediction:

### 1. Exploratory Data Analysis & Cleaning (`first_steps`)

* **Data Ingestion:** Consolidation of three main data sources: historical daily sales (time series), event/holiday calendars, and price evolution.
* **Data Wrangling:** Transformation of the data structure from "wide" format (days as columns) to "long" format (transactional) to facilitate modeling.
* **Analysis:** Study of sales distributions by department, store, and region.

### 2. Advanced Segmentation: Clustering (`tarea_2_clustering`)

Instead of treating all products equally, we performed intelligent segmentation based on **sales behavior** rather than just category.

* **Feature Engineering for Clustering:** Creation of specific KPIs per item, including:
  * *Price Elasticity* (Demand sensitivity to price changes).
  * *Seasonality & Trend Slope* (Cyclical patterns and growth trends).
  * *Sociability* (Impact of social events on sales).
* **Outcome:** Grouping of products into homogeneous clusters (e.g., "High Elasticity," "Stable Sellers") to apply differentiated modeling strategies.

### 3. Feature Engineering

To feed the Machine Learning models, we enriched the dataset with complex variables:

* **Time-Lags:** Sales from 1, 4, 26, and 52 weeks ago to capture weekly, monthly, and annual cycles.
* **Rolling Windows:** Moving averages to smooth noise and capture recent trends.
* **Cyclical Calendar:** Transformation of dates (Month, Day) using Sine and Cosine functions to preserve the cyclical nature of time.
* **Events & "Heat" Features:** Specific flags and proximity counters (e.g., "Weeks until Christmas," "Days since Superbowl") to measure the impact of major holidays.
* **External Data:** Integration of weather data (Temperature, Precipitation) via the `meteostat` library to assess environmental impact on retail footfall.

### 4. Time Series Forecasting (`tarea_3_time_series`)

The core of the project is a robust forecasting system.

* **Validation Strategy:** Chronological **train / validation / test split** (train weeks 53–253, validation 255–268, test 270–278), with one-step-ahead evaluation and a naive last-week baseline for comparison. Hyperparameters are tuned with Optuna on the validation weeks; the test weeks are only used for the final evaluation.
* **Modeling Approach:** Evaluation of various algorithms, prioritizing **Tree-based Machine Learning models** (e.g., XGBoost/LightGBM) for their ability to handle non-linear patterns and complex exogenous variables.
* **Target:** Prediction of unit sales (`sale`) and revenue impact (`daily_revenue`), utilizing Log transformations to stabilize variance where necessary.

## 🛠️ Tech Stack

The project was developed entirely in **Python** using the following key libraries:

* **Data Processing:** `Pandas`, `NumPy`
* **Visualization:** `Matplotlib`, `Seaborn`
* **Machine Learning:** `Scikit-learn`, `XGBoost`
* **External APIs:** `Meteostat` (Weather data)
* **Environment:** Jupyter Notebooks / Google Colab

## 🚀 Results & Business Impact

The proposed solution empowers DSMarket to:

1. **Automate Forecasting:** Generate demand predictions for thousands of references simultaneously without manual intervention.
2. **Product Intelligence:** Deeply understand product behavior through clustering (e.g., identifying which items are "loss leaders" vs. profit drivers).
3. **Optimize Stock:** Reduce storage costs for low-rotation products and ensure availability for best-sellers, directly improving the operating margin.


## 👥 The team

[](https://github.com/asansal/ML-data-cleaning-and-classification-projects#-equipo)

**Alejandro Sanchez** / [@asansal](https://github.com/asansal)

**Emanuel Alassia** / [@EAlassia-ghub](https://github.com/EAlassia-ghub)

**Ignacio Salafranca** / [@NakioSE](https://github.com/NakioSE)

**Leonardo Aguado** / [@leoaguado](https://github.com/leoaguado)

---

*Project realized as a Master's Thesis (TFM) in Data Science.*
