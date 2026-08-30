# Sales & Demand Forecasting for Businesses

## Superstore Sales Forecasting using Machine Learning

## 📌 Project Overview

This project focuses on analyzing historical Superstore sales data and forecasting monthly sales for the year 2018 using Machine Learning.

A Random Forest Regression approach is used to learn patterns from historical monthly sales. Two Random Forest configurations are evaluated using MAE, RMSE, and MAPE, and the better-performing model is selected for the final forecast.

The forecast results are then visualized using an interactive Power BI dashboard.

---

## 🎯 Objectives

- Analyze historical Superstore sales data.
- Convert transaction-level sales data into a monthly time series.
- Identify yearly, monthly, and seasonal sales patterns.
- Engineer time-based and lag-based features.
- Train Random Forest Regression models.
- Compare two model configurations using MAE, RMSE, and MAPE.
- Select the better-performing model.
- Forecast monthly sales for all 12 months of 2018.
- Visualize historical and forecast sales using Power BI.
- Identify important features influencing the predictions.

---

## 📊 Dataset

The project uses the **Sample - Superstore** dataset.

The dataset contains sales transaction information including:

- Order Date
- Ship Date
- Customer information
- Segment
- Country
- City
- State
- Region
- Product information
- Category
- Sub-Category
- Sales
- Quantity
- Discount
- Profit

The original dataset is stored as:

`Sample - Superstore.csv`

---

## 🔄 Methodology

### 1. Data Loading

The Superstore CSV dataset is loaded using Pandas.

### 2. Data Preprocessing

The `Order Date` column is converted into datetime format.

The transaction-level sales data is aggregated into monthly sales values.

### 3. Exploratory Data Analysis

The project analyzes:

- Yearly sales
- Monthly sales patterns
- Seasonal sales behavior
- Monthly sales trends

### 4. Feature Engineering

The following features are created:

| Feature | Description |
|---|---|
| Year | Year of the observation |
| Month | Month number |
| Quarter | Quarter of the year |
| TimeIndex | Sequential time index |
| Lag_1 | Previous month's sales |
| Lag_12 | Sales from the same month in the previous year |

The lag features help the model capture historical sales behavior.

### 5. Train-Test Split

The monthly dataset is divided chronologically:

- **Training data:** 30 observations
- **Testing data:** 6 observations

A time-based split is used instead of random splitting because this is a time-series forecasting problem.

---

## 🤖 Machine Learning Models

Two Random Forest Regression models are evaluated.

### Random Forest Model 1

- Number of trees: 200
- Random state: 42

### Random Forest Model 2

- Number of trees: 500
- Maximum depth: 8
- Minimum samples per leaf: 2
- Random state: 42

---

## 📈 Model Evaluation

The models are evaluated using:

### MAE — Mean Absolute Error

Measures the average absolute difference between actual and predicted sales.

Lower values indicate better performance.

### RMSE — Root Mean Squared Error

Measures prediction error while giving greater weight to larger errors.

Lower values indicate better performance.

### MAPE — Mean Absolute Percentage Error

Measures the average percentage difference between actual and predicted sales.

Lower values indicate better performance.

### Results

| Model | MAE | RMSE | MAPE (%) |
|---|---:|---:|---:|
| Random Forest 1 | 14,329.20 | 17,806.18 | 16.997% |
| Random Forest 2 | 15,975.36 | 20,143.04 | 18.587% |

Based on MAE and RMSE, **Random Forest 1** provides the better overall performance and is selected as the final model.

---

## 🔮 2018 Sales Forecast

The selected Random Forest model is retrained using the available historical modeling data and used to generate monthly sales forecasts for all 12 months of 2018.

The forecast dataset is exported as:

`powerbi_sales_forecast.csv`

The forecast contains:

- Date
- Sales
- Type

where `Type` identifies observations as either:

- `Actual`
- `Forecast`

---

## 🔍 Feature Importance

The Random Forest model identifies the following features as important:

| Feature | Importance |
|---|---:|
| Lag_12 | 0.559835 |
| Month | 0.218051 |
| TimeIndex | 0.119434 |
| Lag_1 | 0.060171 |
| Quarter | 0.027121 |
| Year | 0.015388 |

`Lag_12` is the most important feature, indicating that sales from the same month in the previous year provide substantial information for forecasting.

---

## 📊 Power BI Dashboard

An interactive Power BI dashboard was created to visualize the analysis and forecast.

### Page 1 — Superstore Sales Analysis & Forecasting

Includes:

- Monthly Actual vs Forecast Sales
- Annual Sales: Historical vs 2018 Forecast
- Sales by Category
- Sales by Region
- 2018 Forecast Sales KPI

### Page 2 — 2018 Sales Forecast Dashboard

Includes:

- 2018 Monthly Sales Forecast
- Forecast Average Monthly Sales
- Highest Forecasted Monthly Sales
- Lowest Forecasted Monthly Sales
- MAE
- RMSE
- MAPE

### Page 3 — Machine Learning Model Insights

Includes:

- Feature Importance
- Model Comparison — MAE
- Model Comparison — MAPE
- Key Business Insights

---

## 💡 Key Insights

- Random Forest 1 provides the better overall performance based on MAE and RMSE.
- The model achieves a MAPE of approximately 17% for Random Forest 1.
- `Lag_12` is the most influential feature in the Random Forest model.
- The 2018 forecast shows substantial variation across months.
- Forecasted sales increase significantly during the later part of 2018, with the highest forecast occurring around September.
- The forecast can support inventory planning and sales decision-making.

---

## 🛠️ Technologies Used

- Python
- Pandas
- NumPy
- Scikit-learn
- Matplotlib
- Jupyter Notebook
- Microsoft Power BI

---

## 📁 Project Structure

```text
FUTURE_ML_01/
│
├── Superstore_Sales_Forecasting.ipynb
├── Superstore_Sales_Forecasting.pbix
├── Sample - Superstore.csv
└── powerbi_sales_forecast.csv

---

## 🚀 How to Run

### Python Notebook

1. Open `Superstore_Sales_Forecasting.ipynb` in Jupyter Notebook or JupyterLab.
2. Ensure the required Python libraries are installed.
3. Run the cells sequentially.
4. The notebook generates the 2018 sales forecast.
5. The forecast is exported to `powerbi_sales_forecast.csv`.

### Power BI

1. Open `Superstore_Sales_Forecasting.pbix`.
2. Refresh the data if required.
3. Explore the three dashboard pages.

---

## 👤 Project Summary

This project demonstrates an end-to-end Machine Learning workflow for sales forecasting, starting from raw transactional data and progressing through data preprocessing, exploratory analysis, feature engineering, model training, evaluation, forecasting, and business intelligence visualization.