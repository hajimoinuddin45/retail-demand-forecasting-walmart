# Retail Demand Forecasting using Walmart Store Sales Data

---

# Project Overview

This project presents a complete end-to-end Retail Demand Forecasting solution using the Walmart Store Sales Forecasting dataset from Kaggle. The primary objective is to forecast weekly sales across multiple Walmart stores and departments using advanced Machine Learning, Time Series Forecasting, and Explainable AI techniques.

The solution integrates:

* Data preprocessing and feature engineering
* Exploratory data analysis (EDA)
* Multiple forecasting models
* Time-series-aware validation
* Model explainability using SHAP and LIME
* Business interpretation and recommendations
* Production-ready project structure

The forecasting system is designed to support real-world retail business decisions such as:

* Inventory planning
* Demand forecasting
* Promotion optimization
* Workforce planning
* Supply chain management

---

# Problem Statement

Retail businesses experience highly dynamic demand fluctuations due to:

* Seasonal trends
* Holiday effects
* Promotional markdowns
* Economic indicators
* Store-level variations

Accurate sales forecasting is critical for:

* Reducing inventory costs
* Preventing stock shortages
* Improving customer satisfaction
* Enhancing operational efficiency
* Optimizing pricing and promotions

This project aims to build an intelligent forecasting pipeline capable of predicting Walmart weekly sales accurately and interpretably.

---

# Dataset Information

Dataset Source:
Walmart Store Sales Forecasting Dataset (Kaggle)

Dataset Link:
https://www.kaggle.com/c/walmart-recruiting-store-sales-forecasting/data

---

# Dataset Files

| File Name            | Description                               |
| -------------------- | ----------------------------------------- |
| train.csv            | Historical weekly sales data              |
| test.csv             | Test dataset used for prediction          |
| stores.csv           | Store metadata including type and size    |
| features.csv         | Economic indicators and markdown features |
| sampleSubmission.csv | Sample output format                      |

---

# Dataset Description

The dataset contains weekly sales information from 45 Walmart stores located across different regions.

Important external factors included:

* Temperature
* Fuel Price
* Consumer Price Index (CPI)
* Unemployment Rate
* Promotional Markdown Data
* Holiday Indicators

Major holidays are weighted heavily in evaluation:

* Super Bowl
* Labor Day
* Thanksgiving
* Christmas

---

# Project Objectives

The major objectives of this project are:

* Forecast weekly retail sales accurately
* Compare multiple forecasting models
* Analyze demand patterns and seasonality
* Engineer meaningful forecasting features
* Implement explainable AI methods
* Generate actionable business insights
* Build a scalable forecasting pipeline

---

# Technologies Used

## Programming Language

* Python 3.10

---

# Libraries Used

## Data Manipulation

* pandas
* numpy

## Data Visualization

* matplotlib
* seaborn

## Machine Learning

* scikit-learn
* xgboost
* lightgbm

## Time Series Forecasting

* statsmodels
* prophet

## Deep Learning

* tensorflow
* keras

## Explainable AI

* shap
* lime

## Notebook Environment

* jupyter notebook

---

# Project Workflow

The project follows a structured end-to-end machine learning workflow.

---

# 1. Data Collection & Integration

Data was collected from multiple CSV files:

* train.csv
* stores.csv
* features.csv

The datasets were merged using:

* Store
* Date
* IsHoliday

This created a unified forecasting dataset.

---

# 2. Data Preprocessing

The preprocessing pipeline included:

## Missing Value Handling

* MarkDown features filled with zeros
* CPI and Unemployment missing values filled using median values

## Date Conversion

Date columns converted into datetime format.

## Feature Encoding

Store type variables encoded using one-hot encoding.

## Data Cleaning

* Removed invalid records
* Ensured numeric compatibility for ML models and SHAP

---

# 3. Exploratory Data Analysis (EDA)

EDA was performed to understand:

* Weekly sales trends
* Holiday sales behavior
* Seasonal demand fluctuations
* Store-wise performance
* Correlation among features

---

# EDA Visualizations

The following visualizations were created:

* Weekly Sales Trend Plot
* Holiday vs Non-Holiday Sales Distribution
* Store-wise Sales Comparison
* Correlation Heatmap
* Residual Distribution Plot
* Residual Scatter Plot

---

# 4. Feature Engineering

Feature engineering significantly improved forecasting performance.

## Date-Based Features

* Year
* Month
* Week
* Quarter
* Day

## Lag Features

Lag variables help models learn temporal dependencies.

* Lag_1
* Lag_4
* Lag_12

## Rolling Window Features

Rolling statistics capture short-term trends and volatility.

* Rolling_Mean_4
* Rolling_STD_4

## Holiday Features

* Holiday_Next_Week

## Store Features

* Store Size
* Store Type

---

# 5. Model Development

Multiple forecasting models were implemented and compared.

---

# Machine Learning Models

## Random Forest Regressor

Advantages:

* Handles non-linear relationships
* Robust against overfitting
* Good baseline forecasting model

---

## XGBoost Regressor

Advantages:

* High forecasting accuracy
* Excellent scalability
* Handles missing values effectively
* Strong feature importance capabilities

XGBoost achieved the best overall performance.

---

## LightGBM Regressor

Advantages:

* Fast training speed
* Memory efficient
* Good scalability for large datasets

---

# Time Series Forecasting Models

## Prophet

Facebook Prophet was implemented for:

* Trend decomposition
* Seasonality analysis
* Holiday-aware forecasting

---

# Hyperparameter Tuning

Hyperparameter tuning was performed using:

* RandomizedSearchCV

Optimized parameters included:

* Number of estimators
* Learning rate
* Tree depth

This improved model generalization and forecasting stability.

---

# Train-Test Split Strategy

A time-series-aware split strategy was implemented.

## Training Data

Before 2012

## Testing Data

2012 and later

Random train-test splitting was avoided to prevent temporal data leakage.

---

# Time Series Cross Validation

TimeSeriesSplit cross-validation was used to:

* Simulate real-world forecasting
* Evaluate model stability
* Prevent leakage
* Assess robustness over time

---

# Model Evaluation Metrics

The following evaluation metrics were used:

| Metric   | Description                    |
| -------- | ------------------------------ |
| MAE      | Mean Absolute Error            |
| RMSE     | Root Mean Squared Error        |
| WMAE     | Weighted Mean Absolute Error   |
| MAPE     | Mean Absolute Percentage Error |
| R² Score | Goodness of fit                |

---

# Why WMAE Matters

WMAE is particularly important in retail forecasting because holiday periods have significantly higher business impact.

Holiday weeks were weighted 5x as specified in the Kaggle competition.

---

# Model Comparison

| Model         | Performance |
| ------------- | ----------- |
| Random Forest | Good        |
| XGBoost       | Best        |
| LightGBM      | Very Good   |
| Prophet       | Moderate    |

---

# Best Model Selection

## Selected Model: XGBoost

XGBoost was selected as the final forecasting model because it demonstrated:

* Lowest RMSE
* Strong generalization
* High scalability
* Excellent handling of non-linear demand patterns
* Better robustness during holiday periods
* Strong explainability support

---

# Trade-off Analysis

| Model         | Accuracy | Interpretability | Training Speed | Scalability |
| ------------- | -------- | ---------------- | -------------- | ----------- |
| Random Forest | Medium   | Medium           | Medium         | Medium      |
| XGBoost       | High     | Medium           | Medium         | High        |
| LightGBM      | High     | Medium           | Fast           | High        |
| Prophet       | Medium   | High             | Fast           | Medium      |

---

# Residual Analysis

Residual analysis was conducted to validate forecasting quality.

The following checks were performed:

* Residual distribution analysis
* Residual scatter plots
* Error consistency analysis
* Randomness validation

Observations:

* Residuals were centered near zero
* No major systematic patterns observed
* Model demonstrated stable forecasting behavior

---

# Robustness Testing

The model was evaluated under different business conditions.

## Tests Performed

### Holiday vs Non-Holiday Performance

Measured forecasting stability during peak demand periods.

### Store-Type Analysis

Compared performance across different store categories.

### Markdown Sensitivity

Evaluated forecasting behavior under promotional conditions.

---

# Explainable AI (XAI)

Explainability was integrated to improve transparency and business trust.

---

# SHAP Explainability

SHAP (SHapley Additive exPlanations) was used for:

* Global feature importance
* Feature contribution analysis
* Dependence analysis

---

# SHAP Insights

Important forecasting features included:

* Lag_1
* Rolling_Mean_4
* Store Size
* MarkDown features
* Holiday indicators

---

# LIME Explainability

LIME (Local Interpretable Model-Agnostic Explanations) was used to explain individual predictions.

Benefits:

* Local prediction transparency
* Human-readable explanations
* Better stakeholder trust

---

# Business Insights

## Key Findings

### Holiday Effects

Holiday weeks significantly increased sales demand.

### Seasonal Patterns

Strong seasonal demand trends were observed during festive periods.

### Promotional Impact

Markdown campaigns directly influenced purchasing behavior.

### Store-Level Variability

Larger stores exhibited stronger seasonal volatility.

### Economic Indicators

Fuel prices and unemployment affected customer spending patterns.

---

# Business Recommendations

## Inventory Planning

Increase inventory before major holidays and promotional periods.

## Promotion Optimization

Use markdown forecasting to optimize campaign performance.

## Workforce Planning

Use demand forecasts for staffing optimization.

## Store-Level Forecasting

Develop region-specific and store-specific forecasting systems.

## Strategic Decision Making

Use explainable AI insights for transparent retail planning.

---

# Model Fairness Discussion

The forecasting model was evaluated across different store types and sizes.

## Observations

* Model performance remained relatively stable across store categories.
* Larger stores showed slightly higher demand volatility.
* Holiday-related errors increased during extreme demand spikes.

## Potential Biases

* Stores with limited historical data may receive lower forecasting accuracy.
* Extreme markdown periods may introduce forecasting instability.

## Future Improvements

* Store-specific ensemble forecasting
* Region-aware modeling
* Fairness-aware optimization techniques

---

# Production Readiness

The project was designed with deployment readiness in mind.

## Production Features

* Modular pipeline
* Reproducible workflow
* Organized project structure
* Explainability integration
* Scalable forecasting models
* Time-series validation

---

# Folder Structure

```bash
Retail_Demand_Forecasting/
│
├── data/
│   ├── train.csv
│   ├── test.csv
│   ├── features.csv
│   ├── stores.csv
│   └── sampleSubmission.csv
│
├── notebooks/
│   └── Retail_Demand_Forecasting.ipynb
│
├── outputs/
│   ├── plots/
│   ├── models/
│   └── reports/
│
├── README.md
├── requirements.txt
└── process_flow_document.pdf
```

---

# Installation Instructions

## Clone Repository

```bash
git clone <repository-link>
cd retail-demand-forecasting-walmart
```

---

# Create Virtual Environment

```bash
python -m venv venv
```

---

# Activate Environment

## Windows

```bash
venv\Scripts\activate
```

## Linux/Mac

```bash
source venv/bin/activate
```

---

# Install Dependencies

```bash
pip install -r requirements.txt
```

---

# Running the Project

Launch Jupyter Notebook:

```bash
jupyter notebook
```

Open:

```bash
Retail_Demand_Forecasting.ipynb
```

Run all notebook cells sequentially.

---

# Challenges Faced

## SHAP Compatibility Issues

Compatibility conflicts between SHAP and newer XGBoost versions were resolved through dependency management and preprocessing adjustments.

## Time-Series Validation

Ensuring proper temporal validation without data leakage required time-series-aware splitting strategies.

## Large-Scale Data Processing

Efficient sampling and optimized training workflows were implemented for scalable processing.

---

# Future Enhancements

Potential future improvements include:

* Real-time forecasting API deployment
* Streamlit dashboard integration
* MLflow experiment tracking
* Ensemble forecasting techniques
* Deep learning optimization
* Cloud deployment
* Automated retraining pipelines

---

# Conclusion

This project successfully developed a comprehensive retail demand forecasting system using Walmart sales data.

Multiple forecasting models were implemented and evaluated using robust time-series validation techniques. XGBoost achieved the best overall forecasting performance due to its strong predictive capability, scalability, and robustness.

The integration of SHAP and LIME improved model transparency and interpretability, making the solution suitable for real-world retail decision-making and production deployment.

The project demonstrates practical expertise in:

* Machine Learning
* Time Series Forecasting
* Explainable AI
* Retail Analytics
* AI Engineering
* Production-Oriented Data Science
