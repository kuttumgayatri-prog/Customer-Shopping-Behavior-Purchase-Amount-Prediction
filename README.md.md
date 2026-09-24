# Customer Shopping Behavior & Purchase Amount Prediction

> **IBM SkillsBuild Data Analytics Internship Project**

---

## Project Overview

This project analyzes customer shopping behavior from the **shopping_trends.csv** dataset and builds machine learning models to predict the **Purchase Amount (USD)** a customer is likely to spend.

It delivers:
- Exploratory Data Analysis (EDA) with interactive charts
- Three regression models compared on real test data
- A Streamlit dashboard covering demographics, products, payments, seasons, and more
- A live prediction form where you enter customer details and get an instant predicted spend

---

## Dataset

| Property | Value |
|---|---|
| File | `shopping_trends.csv` |
| Rows | ~3,900 |
| Target | `Purchase Amount (USD)` |
| Features | Age, Gender, Category, Season, Payment Method, Discount, etc. |

---

## Technology Stack

| Layer | Tools |
|---|---|
| Language | Python 3.8+ |
| Data | Pandas, NumPy |
| Machine Learning | Scikit-learn, XGBoost |
| Frontend / Dashboard | Streamlit |
| Visualization | Plotly Express, Matplotlib, Seaborn |
| Model Persistence | Joblib |

---

## Project Files

```
Mainproject/
├── shopping_trends.csv          # Dataset
├── train_model.py               # Preprocessing + model training
├── app.py                       # Streamlit dashboard
├── requirements.txt             # Python dependencies
├── README.md                    # This file
└── models/                      # Auto-created by train_model.py
    ├── best_model.pkl
    ├── best_model_name.pkl
    ├── label_encoders.pkl
    ├── scaler.pkl
    ├── feature_names.pkl
    ├── categorical_cols.pkl
    ├── numerical_cols.pkl
    ├── linear_regression.pkl
    ├── random_forest.pkl
    ├── xgboost.pkl
    ├── model_results.csv
    └── cleaned_data.csv
```

---

## Setup & Installation

### Prerequisites

- Python 3.8 or higher
- pip

### Step 1 — Install dependencies

```bash
pip install -r requirements.txt
```

### Step 2 — Train the models

Run this **once** before launching the dashboard. It loads the CSV, preprocesses the data, trains all three models, and saves the artifacts to the `models/` folder.

```bash
python train_model.py
```

Expected console output:
```
============================================================
  Customer Shopping Behavior -- Model Training
============================================================

[INFO] Dataset loaded: 3900 rows x 18 columns
...
  Linear Regression      MAE=...  RMSE=...  R2=...
  Random Forest          MAE=...  RMSE=...  R2=...
  XGBoost                MAE=...  RMSE=...  R2=...

[INFO] Best model: Random Forest  (RMSE=...)
============================================================
  Training complete!  Now run:  streamlit run app.py
============================================================
```

### Step 3 — Launch the dashboard

```bash
streamlit run app.py
```

The app will open automatically in your browser at `http://localhost:8501`.

---

## Dashboard Sections

| Section | Description |
|---|---|
| 🏠 Project Overview | Goal, tech stack, quick metrics |
| 📋 Dataset Summary | Shape, columns, dtypes, statistics |
| 🧹 Data Cleaning | Missing values, duplicates, cleaning steps |
| 👥 Customer Demographics | Age, Gender, Location analysis |
| 🛒 Product & Category | Top items, category spend, size heatmap |
| 💰 Purchase Amount Analysis | Distribution, box plots, rating correlation |
| 💳 Payment & Shipping | Method usage and avg spend breakdown |
| 🎁 Subscription & Discounts | Subscription, discount, promo code impact |
| 📅 Seasonal Trends | Season and purchase frequency analysis |
| 🤖 ML Model Comparison | MAE, RMSE, R² bar charts for all 3 models |
| 📊 Feature Importance | RF and XGBoost top-15 feature charts |
| 🔮 Live Prediction | Enter customer details → get predicted spend |

---

## Machine Learning Models

| Model | Type | Library |
|---|---|---|
| Linear Regression | Baseline regression | scikit-learn |
| Random Forest Regressor | Ensemble (bagging) | scikit-learn |
| XGBoost Regressor | Ensemble (boosting) | xgboost |

### Evaluation Metrics

| Metric | Meaning |
|---|---|
| MAE | Mean Absolute Error — average USD error |
| RMSE | Root Mean Squared Error — penalizes large errors |
| R² | Proportion of variance explained (1.0 = perfect) |

Best model is selected automatically based on the **lowest RMSE** on the held-out test set.

---

## Notes

- The `models/` folder is created automatically when you run `train_model.py`.
- Do not skip the training step — `app.py` will show a warning if model files are missing.
- The prediction form uses the exact same preprocessing pipeline used during training.
- All charts are interactive (zoom, hover, export) via Plotly Express.

---

*IBM SkillsBuild Data Analytics Internship | Built with Python & Streamlit*
