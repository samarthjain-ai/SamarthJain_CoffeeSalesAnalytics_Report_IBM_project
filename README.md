# ☕ Coffee Sales Analytics & Business Intelligence

> **A complete, portfolio-quality Data Science + Machine Learning + Node.js project**
> Built on a real 13-month coffee sales transaction dataset.

**Student:** Samarth Jain &nbsp;|&nbsp; **University:** Sage University Indore &nbsp;|&nbsp; **Program:** B.Tech Artificial Intelligence &nbsp;|&nbsp; **Year:** 2024–25

---

## 📋 Table of Contents

1. [What This Project Does](#-what-this-project-does)
2. [Requirements](#-requirements)
3. [How to Run — Step by Step](#-how-to-run--step-by-step)
4. [How to Run the Single Python File](#-how-to-run-the-single-python-file)
5. [Project Structure](#-project-structure)
6. [API Reference](#-api-reference)
7. [Dataset](#-dataset)
8. [Key Findings](#-key-findings)
9. [Machine Learning](#-machine-learning)
10. [Architecture](#-architecture)
11. [Limitations & Future Scope](#-limitations--future-scope)

---

## 🎯 What This Project Does

This project analyses a real coffee shop's 13-month sales data and builds:

| What | Technology |
|------|-----------|
| Data Cleaning & EDA | Python, Pandas, Matplotlib, Seaborn |
| Statistical Hypothesis Testing | SciPy (Kruskal-Wallis) |
| Machine Learning (Revenue Forecasting) | Scikit-learn — Random Forest + 4 more models |
| Analytics REST API | Python FastAPI |
| Web Server / Backend | Node.js + Express |
| Interactive Dashboard | HTML + CSS + JavaScript + Chart.js |
| Jupyter Notebook (24 sections) | Full academic report-style notebook |
| Single Python file for college | `Coffee_Sales_Analytics.py` |

---

## ✅ Requirements

Before you start, make sure these are installed on your computer.

### Python (version 3.10 or higher)
Check: open a terminal and type:
```bash
python --version
```
Download from: https://www.python.org/downloads/

### Node.js (version 18 or higher)
Check:
```bash
node --version
```
Download from: https://nodejs.org/

### Git (optional — only needed if cloning)
Download from: https://git-scm.com/

---

## 🚀 How to Run — Step by Step

> The dashboard needs **two terminals open at the same time** — one for Python, one for Node.js.

---

### STEP 1 — Get the project folder

If you cloned from GitHub:
```bash
git clone <your-repo-url>
cd coffee-sales-analytics
```

If you already have the folder on your computer, just open a terminal and navigate to it:
```bash
cd "C:\Users\ASUS\OneDrive\Desktop\IBM_project\coffee-sales-analytics"
```

---

### STEP 2 — Install Python packages (do this once)

Make sure you are inside the `coffee-sales-analytics` folder, then run:
```bash
pip install -r requirements.txt
```

This installs: `pandas`, `numpy`, `matplotlib`, `seaborn`, `scipy`, `scikit-learn`, `joblib`, `fastapi`, `uvicorn`

> **If you get a "pip not found" error**, try `pip3 install -r requirements.txt`

---

### STEP 3 — Install Node.js packages (do this once)

```bash
cd backend
npm install
cd ..
```

> This creates a `node_modules` folder inside `backend/`. It only needs to be done once.

---

### STEP 4 — Create the .env file (do this once)

In the `coffee-sales-analytics` folder, create a file called `.env`:

**On Windows:**
```bash
copy .env.example .env
```

**On Mac/Linux:**
```bash
cp .env.example .env
```

The `.env` file should contain:
```
PORT=3000
PYTHON_API_URL=http://localhost:8000
```

---

### STEP 5 — Run the ML pipeline & train models (do this once)

From inside the `coffee-sales-analytics` folder:
```bash
python -m ml.data_cleaning
python -m ml.eda
python -m ml.statistics
python -m ml.train
python -m ml.visualizations
```

> This creates the cleaned dataset, trains 5 models, and saves all charts.
> The `models/` and `outputs/` folders will be populated.
> **Skip this step if `models/daily_revenue_rf.joblib` already exists** — it was pre-trained.

---

### STEP 6 — Open Terminal 1 and start the Python API

Open a terminal, go to the `coffee-sales-analytics` folder, and run:

```bash
uvicorn ml.api:app --host 0.0.0.0 --port 8000 --reload
```

**You should see output like this:**
```
INFO:     Uvicorn running on http://0.0.0.0:8000
[startup] Loaded 3539 rows
[startup] Models loaded
INFO:     Application startup complete.
```

> **Leave this terminal open and running.** Do not close it.

To verify it is working, open your browser and go to:
```
http://localhost:8000/health
```
You should see: `{"status":"ok","rows_loaded":3539}`

---

### STEP 7 — Open Terminal 2 and start the Node.js server

Open a **second** terminal, go to the `backend` folder, and run:

```bash
cd "C:\Users\ASUS\OneDrive\Desktop\IBM_project\coffee-sales-analytics\backend"
node server.js
```

**You should see:**
```
╔══════════════════════════════════════════════════════╗
║   Coffee Sales Analytics — Node.js Server           ║
║   Listening on http://localhost:3000                ║
║   Python API  -> http://localhost:8000              ║
╚══════════════════════════════════════════════════════╝
```

> **Leave this terminal open and running too.** Do not close it.

---

### STEP 8 — Open the Dashboard

Open your browser and go to:

```
http://localhost:3000
```

**That's it! The dashboard is now live.**

---

### What the Dashboard Looks Like

| Tab | What You See |
|-----|-------------|
| 📊 **Overview** | 8 live KPI cards (total revenue, transactions, top coffee, peak hour, etc.) + 5 business insight cards |
| ☕ **Products** | Doughnut chart of coffee product share + revenue bar chart + payment method chart |
| ⏰ **Time Analysis** | Hourly sales pattern (dual-axis) + weekday distribution + morning/afternoon/night breakdown |
| 📈 **Trends** | 13-month revenue and transaction trend line chart |
| 🤖 **Predictive ML** | Revenue predictor form + 5-model comparison table + feature importance chart |
| 🗃 **Data** | Full paginated transaction table (3,539 rows) with filters |

**Using the filters at the top** — select a coffee product, time of day, weekday, month, or date range and click **Apply Filters**. All KPIs and charts update instantly.

**Making a prediction** — go to the 🤖 Predictive ML tab, pick any date, and click **Predict Revenue**.

---

### How to Stop the Servers

- In **Terminal 1** (Python): press `Ctrl + C`
- In **Terminal 2** (Node.js): press `Ctrl + C`

---

### Troubleshooting

| Problem | Solution |
|---------|---------|
| `uvicorn: command not found` | Run `pip install uvicorn` first |
| `node: command not found` | Install Node.js from https://nodejs.org/ |
| `ModuleNotFoundError` | Run `pip install -r requirements.txt` |
| `Cannot find module 'express'` | Run `npm install` inside the `backend/` folder |
| Dashboard shows "Failed to load KPIs" | Python API (Terminal 1) must be running first |
| Port 8000 already in use | Change `--port 8001` and update `.env` → `PYTHON_API_URL=http://localhost:8001` |
| Port 3000 already in use | Edit `.env` → `PORT=3001`, then open `http://localhost:3001` |
| `ENOENT: .env not found` | Run `copy .env.example .env` (Windows) or `cp .env.example .env` (Mac/Linux) |

---

## 📄 How to Run the Single Python File

For college submission, a single self-contained Python file is also included.
It runs the complete data science pipeline (EDA + stats + ML) **without** needing Node.js or the web server.

```bash
cd "C:\Users\ASUS\OneDrive\Desktop\IBM_project\coffee-sales-analytics"
python Coffee_Sales_Analytics.py
```

This will:
- Load and inspect `data/Coffe_sales.csv`
- Clean the data
- Run full EDA
- Generate and save 5 charts to `outputs/figures/`
- Run 3 Kruskal-Wallis hypothesis tests
- Train and compare 5 ML models
- Print all results, metrics, observations, insights, and recommendations
- Save prediction results to `outputs/figures/predictions_sample.csv`

> No browser or Node.js needed for this file.

---

## 📓 How to Run the Jupyter Notebook

```bash
pip install jupyter
cd "C:\Users\ASUS\OneDrive\Desktop\IBM_project\coffee-sales-analytics"
jupyter notebook notebooks/SamarthJain_CoffeeSalesAnalytics.ipynb
```

Then in your browser, click **Kernel → Restart & Run All**.

---

## 📁 Project Structure

```
coffee-sales-analytics/
│
├── data/
│   └── Coffe_sales.csv                   <- Raw dataset (3,547 rows)
│
├── frontend/                             <- Dashboard UI (served by Node.js)
│   ├── index.html
│   ├── css/style.css
│   └── js/
│       ├── app.js                        <- KPIs, charts, prediction form
│       ├── charts.js                     <- Chart.js chart builders
│       ├── filters.js                    <- Filter state management
│       └── table.js                      <- Paginated transaction table
│
├── backend/                              <- Node.js Express server (port 3000)
│   ├── server.js
│   ├── routes/api.js
│   ├── controllers/
│   │   ├── analyticsController.js
│   │   └── predictController.js
│   ├── services/pythonClient.js          <- Axios proxy to Python API
│   └── package.json
│
├── ml/                                   <- Python ML pipeline
│   ├── __init__.py
│   ├── data_cleaning.py                  <- Cleaning pipeline
│   ├── eda.py                            <- Analytics aggregations
│   ├── statistics.py                     <- 3 hypothesis tests
│   ├── features.py                       <- Feature engineering
│   ├── models.py                         <- Model registry
│   ├── train.py                          <- Training pipeline
│   ├── visualizations.py                 <- 5 EDA charts
│   ├── predict.py                        <- Prediction functions
│   └── api.py                            <- FastAPI service (port 8000)
│
├── models/                               <- Pre-trained model files
│   ├── daily_revenue_rf.joblib           <- Random Forest regression model
│   ├── coffee_classifier_rf.joblib       <- Coffee product classifier
│   ├── label_encoder.joblib
│   ├── regression_metadata.json          <- MAE / RMSE / R2 / feature importance
│   └── classification_metadata.json
│
├── notebooks/
│   └── SamarthJain_CoffeeSalesAnalytics.ipynb  <- 24-section Jupyter notebook
│
├── outputs/
│   ├── figures/                          <- Generated charts (PNG files)
│   ├── tables/                           <- Analytics JSON files
│   └── cleaned_data/
│       └── coffee_sales_clean.csv        <- 3,539 cleaned rows
│
├── screenshots/                          <- Dashboard screenshots
│
├── Coffee_Sales_Analytics.py             <- Single-file Python submission
├── requirements.txt                      <- Python dependencies
├── .env.example                          <- Environment variable template
├── .gitignore
└── README.md
```

---

## 📡 API Reference

All endpoints available at `http://localhost:3000/api/` (via Node.js) or `http://localhost:8000/` (Python direct).

| Method | Endpoint | Description |
|--------|---------|-------------|
| GET | `/api/summary` | KPI summary — supports all filters |
| GET | `/api/filter-options` | Dropdown values for filter controls |
| GET | `/api/transactions` | Paginated transaction records |
| GET | `/api/analytics/products` | Revenue and count by coffee product |
| GET | `/api/analytics/hourly` | Transactions and revenue by hour |
| GET | `/api/analytics/weekday` | Transactions by day of week |
| GET | `/api/analytics/monthly` | Revenue and count by month |
| GET | `/api/analytics/daily` | Daily revenue time series |
| GET | `/api/analytics/time-of-day` | Morning / Afternoon / Night breakdown |
| GET | `/api/analytics/payment-types` | Payment method distribution |
| GET | `/api/analytics/statistics` | Hypothesis test results |
| GET | `/api/model-metrics` | Model metrics and feature importance |
| POST | `/api/predict` | `{"date":"YYYY-MM-DD"}` → predicted revenue |

**Example with filters:**
```
http://localhost:3000/api/summary?coffee_name=Latte&weekday=Mon&month_name=Mar
```

---

## 📊 Dataset

| Property | Value |
|----------|-------|
| File | `data/Coffe_sales.csv` |
| Raw Rows | 3,547 |
| Clean Rows | 3,539 (8 removed — bad time parse) |
| Columns | 11 |
| Date Range | 2024-03-01 to 2025-03-23 (13 months) |
| Coffee Products | 8 unique items |
| Payment Types | Card only (100% — zero cash) |
| Hour Range | 07:00 to 22:00 |
| Total Revenue | 111,988.90 CZK |
| Missing Values | 0 |
| Duplicate Rows | 0 |

**Coffee Products:** Latte, Americano, Americano with Milk, Cappuccino, Cortado, Hot Chocolate, Cocoa, Espresso

### Dataset Columns

| Column | Type | Description |
|--------|------|-------------|
| `hour_of_day` | int | Hour of transaction (7–22) |
| `cash_type` | str | Payment method (card only in this dataset) |
| `money` | float | Transaction amount in CZK |
| `coffee_name` | str | Coffee product name (8 unique values) |
| `Time_of_Day` | str | Period category: Morning / Afternoon / Night |
| `Weekday` | str | 3-letter day abbreviation (Mon–Sun) |
| `Month_name` | str | 3-letter month abbreviation (Jan–Dec) |
| `Weekdaysort` | int | Sort key for weekday (1=Mon to 7=Sun) |
| `Monthsort` | int | Sort key for month (1=Jan to 12=Dec) |
| `Date` | str | Transaction date (YYYY-MM-DD) |
| `Time` | str | Transaction time (HH:MM:SS.ffffff) |

## 🔗 Dataset Source

| Field | Details |
|-------|---------|
| **Platform** | Kaggle |
| **Dataset Name** | Coffee Sales Dataset |
| **Author** | Navjot Kaushal |
| **URL** | https://www.kaggle.com/datasets/navjotkaushal/coffee-sales-dataset |
| **Downloaded File** | `Coffe_sales.csv` (original spelling from source) |
| **Licence** | Public — Kaggle Dataset |

> **Direct Link:** [https://www.kaggle.com/datasets/navjotkaushal/coffee-sales-dataset](https://www.kaggle.com/datasets/navjotkaushal/coffee-sales-dataset)

---

## 🔍 Key Findings

### 5 Observations (from actual data)
1. **Product Concentration** — Top 2 products (Americano with Milk + Latte) account for 44.2% of all 3,539 transactions.
2. **Peak Hour** — Hour 10:00 has the highest volume with 328 transactions (9.3% of all sales).
3. **Time of Day** — Afternoon leads with 1,203 transactions vs Morning 1,179 vs Night 1,157.
4. **Price-Volume Trade-off** — Americano with Milk leads in transactions (808) but Latte generates more total revenue (26,810 CZK).
5. **Payment Exclusivity** — 100% of transactions are card payments across the entire 13-month window.

### 5 Insights
1. **Inventory Priority** — Top-2 products carry disproportionate stockout risk and need highest safety stock.
2. **Staffing Windows** — Peak demand at 10:00 supports targeted shift scheduling for that window.
3. **Seasonal Revenue** — Monthly revenue varies 2.8x (5,720 to 15,892 CZK) — justifies pre-planned promotions.
4. **Pricing Strategy** — Volume vs revenue leader divergence suggests a traffic-driver vs margin-maximiser product split.
5. **CRM Opportunity** — 100% card payments make every sale traceable — ideal foundation for a loyalty programme.

### 3 Hypotheses (Kruskal-Wallis, alpha = 0.05)

| ID | Hypothesis | p-value | Decision |
|----|-----------|---------|---------|
| H1 | Transaction counts differ across Time-of-Day | 0.2029 | Fail to Reject H0 |
| H2 | Transaction amounts differ across coffee products | < 0.001 | **Reject H0** |
| H3 | Daily transaction volume differs across weekdays | 0.1749 | Fail to Reject H0 |

### 3 Recommendations
1. **Tiered Inventory** — Set safety-stock 40-50% higher for Americano with Milk and Latte.
2. **Peak-Hour Staffing** — Maximum barista capacity at 10:00–12:00 daily.
3. **Seasonal Promotions** — Pre-plan campaigns for April, January, and July (historically lowest revenue months).

---

## 🤖 Machine Learning

### Task — Daily Revenue Forecasting (Regression)

Per-transaction price is nearly deterministic (coffee × price tier), so predicting `money` per transaction adds no ML value. Instead, the project aggregates to daily revenue and forecasts using lag + rolling + calendar features.

### 22 Features Used

| Category | Features |
|----------|---------|
| Calendar | `day_of_week`, `day_of_month`, `week_of_year`, `month`, `quarter`, `is_weekend` |
| Revenue Lags | `revenue_lag_1`, `revenue_lag_2`, `revenue_lag_3`, `revenue_lag_7`, `revenue_lag_14` |
| Count Lags | `count_lag_1`, `count_lag_2`, `count_lag_3`, `count_lag_7`, `count_lag_14` |
| Rolling Averages | `revenue_rolling_7/14/30`, `count_rolling_7/14/30` |

All lag/rolling features use `shift(1)` — zero future data leakage.

### Train/Test Split
```
Train -> Earliest 80% of dates (2024-03-15 to 2025-01-06) = 293 days
Test  -> Latest 20% of dates  (2025-01-07 to 2025-03-23) = 74 days
NO random shuffling — strictly chronological
```

### Model Results

| Model | MAE | RMSE | R2 | MAPE% |
|-------|-----|------|----|-------|
| Ridge Regression | 166.74 | 208.06 | -0.2221 | 48.75% |
| Decision Tree | 179.12 | 228.06 | -0.4684 | 45.49% |
| **Random Forest** ✓ | **136.06** | **170.14** | **0.1828** | **41.62%** |
| Gradient Boosting | 168.67 | 212.85 | -0.2790 | 45.14% |
| HistGradientBoosting | 155.26 | 192.45 | -0.0456 | 45.27% |

Random Forest selected as primary model (best MAE and R2).

---

## 🏗 Architecture

```
Browser  (http://localhost:3000)
    |
    |  GET/POST /api/*
    v
Node.js + Express          (port 3000)
backend/server.js
    |
    |  axios proxy
    v
Python FastAPI             (port 8000)
ml/api.py
    |
    +---> ml/eda.py          (analytics aggregations)
    +---> ml/statistics.py   (hypothesis tests)
    +---> ml/predict.py      (revenue forecasting)
    +---> models/*.joblib    (pre-trained models)
    +---> outputs/cleaned_data/coffee_sales_clean.csv
    +---> data/Coffe_sales.csv
```

---

## ⚠️ Limitations & Future Scope

### Limitations
- **Single outlet** — findings may not generalise to multi-location operations
- **Card-only payments** — payment-method analysis is limited; no cash data exists
- **Price tier changes** — revenue comparisons across months must account for 3 price regimes
- **No customer IDs** — repeat-visit and loyalty analysis is not possible with this data
- **One-step forecasting** — multi-day-ahead predictions accumulate error

### Future Scope
- Add customer identifiers for cohort and loyalty analysis
- Expand to multi-outlet with location-level comparison
- Evaluate LSTM or Facebook Prophet for longer-horizon forecasting
- Add real-time POS streaming via WebSocket
- Build a mobile-responsive PWA version of the dashboard

*All statistics, observations, insights, and model metrics are computed directly from the actual `Coffe_sales.csv` dataset. No values are fabricated.*
