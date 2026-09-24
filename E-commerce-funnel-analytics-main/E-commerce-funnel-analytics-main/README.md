# 🛒 E-Commerce Funnel Analytics & Drop-off Analysis

An end-to-end **E-Commerce Funnel Analytics** project built to understand customer behavior across the purchase journey — from **Product View → Add to Cart → Checkout → Purchase**.

The project combines **Power BI, DAX, Python, SQL, SQLite, and Pandas** to transform event-level e-commerce data into an interactive business intelligence dashboard.

---

## 📊 Project Overview

E-commerce businesses generate large volumes of customer-event data, but raw events alone do not explain where customers are being lost.

This project analyzes the complete customer funnel to answer:

- How many users enter the purchase journey?
- Where do customers drop off?
- What percentage of users move from one funnel stage to the next?
- How much revenue is generated?
- How does customer behavior vary by device, traffic source, region, and product category?
- Which areas should be investigated to improve conversion?

---

## 🎯 Business Objective

The primary objective is to identify **conversion bottlenecks and customer behavior patterns** within an e-commerce purchase funnel.

### Funnel

```text
Product View
     ↓
Add to Cart
     ↓
Checkout Start
     ↓
Purchase
```

The analysis focuses on:

- Funnel conversion rates
- Drop-off between stages
- Revenue performance
- Average Order Value (AOV)
- Customer segmentation
- Device behavior
- Traffic-source performance
- Regional behavior
- Product-category performance

---

## 📌 Key Dashboard KPIs

Based on the current dataset and dashboard:

| KPI | Value |
|---|---:|
| Unique Users | 5,000 |
| Product Views | 5,000 |
| Add to Cart | 1,773 |
| Checkout Starts | 1,061 |
| Purchases | 500 |
| View → Cart | 35.46% |
| Cart → Checkout | 59.84% |
| Checkout → Purchase | 47.13% |
| Overall View → Purchase | 10.00% |
| Total Revenue | 79,248.85 |
| Average Order Value | 158.50 |

> Values displayed in the Power BI dashboard may be rounded for presentation, e.g. 5K users, 2K add-to-cart events, and 79.25K revenue.

---

## 📈 Dashboard Features

The Power BI dashboard provides an interactive view of the e-commerce funnel.

### 1. Executive KPI Overview

- Total Users
- Product Views
- Add to Cart
- Purchases
- Checkout-to-Purchase %
- Overall Conversion %

### 2. Funnel Analysis

Visualizes the customer journey:

**Product View → Add to Cart → Checkout → Purchase**

This makes it easier to identify the stages where the largest number of users are lost.

### 3. Conversion Analysis

The dashboard calculates:

- View-to-Cart Conversion
- Cart-to-Checkout Conversion
- Checkout-to-Purchase Conversion
- Overall Conversion

### 4. Revenue Analysis

Includes:

- Total Revenue
- Average Order Value (AOV)
- Revenue by Product Category

### 5. Customer Analysis

Customer behavior can be explored by:

- Device Type
- Traffic Source
- Region
- Product Category

### 6. Interactive Filters

The dashboard includes:

- Device Type dropdown
- Traffic Source dropdown
- Region dropdown
- Product Category dropdown
- Date Range filter

All visuals respond dynamically to these selections.

---

## 🧰 Tools & Technologies

### Business Intelligence
- **Microsoft Power BI**
- **DAX**
- Interactive dashboards
- Data modeling
- Slicers and filters

### Data Analysis
- **Python**
- **Pandas**
- **NumPy**

### Database & Querying
- **SQL**
- **SQLite**

### Visualization / Supporting Analysis
- Matplotlib
- Seaborn

---

## 🗂️ Dataset

The project uses a synthetic e-commerce event dataset created for analytical demonstration.

### Dataset size

- **8,334 event records**
- **5,000 unique users**
- **9 columns**

### Dataset columns

| Column | Description |
|---|---|
| `user_id` | Unique customer identifier |
| `session_id` | Customer session identifier |
| `event_time` | Timestamp of the customer event |
| `event_type` | Funnel event type |
| `device_type` | Mobile, Desktop, or Tablet |
| `traffic_source` | Acquisition source |
| `region` | Customer geographic region |
| `product_category` | Product category |
| `order_value` | Order/revenue value associated with the event |

### Event types

```text
product_view
add_to_cart
checkout_start
purchase
```

> The dataset is synthetic and is intended for learning, portfolio demonstration, and analytics practice rather than production decision-making.

---

## 🔄 Analytical Workflow

```text
Raw E-Commerce Event Data
          ↓
Data Generation / Collection
          ↓
Data Cleaning & Preparation
          ↓
SQLite Database
          ↓
SQL Funnel Analysis
          ↓
Python / Pandas Analysis
          ↓
DAX Measures & Power BI Data Model
          ↓
Interactive Dashboard
          ↓
Business Insights
```

---

## 🧮 Important DAX Measures

Examples of the measures used in the Power BI dashboard include:

```DAX
Total Users =
DISTINCTCOUNT(ecommerce_user_events[user_id])
```

```DAX
Add to Cart =
CALCULATE(
    DISTINCTCOUNT(ecommerce_user_events[user_id]),
    ecommerce_user_events[event_type] = "add_to_cart"
)
```

```DAX
Total Drop Off =
[Product Views] - [Purchases]
```

The project also uses DAX measures for:

- Product Views
- Checkout Starts
- Purchases
- Total Revenue
- Average Order Value
- Overall Conversion
- View-to-Cart Conversion
- Cart-to-Checkout Conversion
- Checkout-to-Purchase Conversion

A calculated `Funnel Stages` table is used to control the funnel order:

```text
Product Views
Add to Cart
Checkout
Purchases
```

---

## 🧪 SQL Analysis

SQL is used to transform event-level records into user-level funnel flags and calculate stage conversion rates.

Example analytical flow:

```sql
Product View
    ↓
Add to Cart
    ↓
Checkout Start
    ↓
Purchase
```

The SQL analysis calculates:

- Funnel stage counts
- View-to-cart rate
- Cart-to-checkout rate
- Checkout-to-purchase rate
- Overall purchase conversion
- Segment-level funnel performance

---

## 🐍 Python Analysis

Python scripts are included for supporting analytical workflows such as:

- Funnel analysis
- Segment analysis
- Metric exports
- Conversion confidence intervals
- Data generation

Main analysis files:

```text
analysis/
├── funnel_analysis.py
├── segment_analysis.py
├── export_metrics.py
└── conversion_confidence_interval.py
```

---

## 🔍 Key Analytical Observations

Based on the current dataset:

### Funnel

Only **35.46%** of product viewers proceed to add a product to their cart.

The funnel then continues through:

```text
Product View → Add to Cart     35.46%
Add to Cart → Checkout         59.84%
Checkout → Purchase            47.13%
Overall View → Purchase        10.00%
```

This indicates that the largest proportional conversion loss occurs at the **Product View → Add to Cart** stage.

### Revenue

The dataset generates approximately:

**79,248.85 total revenue**

with an average order value of approximately:

**158.50**

### Segmentation

The dashboard allows the funnel and revenue metrics to be explored interactively across:

- Desktop
- Mobile
- Tablet
- Organic Search
- Paid Search
- Direct
- Social
- Email
- Referral
- Regional segments
- Product categories

These segments can be filtered directly from the Power BI dashboard.

---

## 📁 Project Structure

```text
ecommerce-funnel-dropoff-analysis/
│
├── analysis/
│   ├── conversion_confidence_interval.py
│   ├── export_metrics.py
│   ├── funnel_analysis.py
│   └── segment_analysis.py
│
├── dashboard/
│   └── E-Commerce Dashboard.pbix
│
├── data/
│   ├── ecommerce_user_events.csv
│   ├── funnel_summary_metrics.csv
│   └── segment_funnel_metrics.csv
│
├── images/
│   └── dashboard_preview.png
│
├── sql/
│   ├── funnel_conversion_analysis.sql
│   └── segment_funnel_analysis.sql
│
├── ecommerce_funnel.db
├── generate_funnel_data.py
├── load_to_sqlite.py
├── requirements.txt
└── README.md
```

---

## ▶️ How to Run the Python / SQL Analysis

### 1. Clone the repository

```bash
git clone <YOUR_GITHUB_REPOSITORY_URL>
cd ecommerce-funnel-dropoff-analysis
```

### 2. Install dependencies

```bash
pip install -r requirements.txt
```

### 3. Generate the dataset

```bash
python generate_funnel_data.py
```

### 4. Load data into SQLite

```bash
python load_to_sqlite.py
```

### 5. Run funnel analysis

```bash
python analysis/funnel_analysis.py
```

### 6. Run segment analysis

```bash
python analysis/segment_analysis.py
```

### 7. Open the Power BI dashboard

Open:

```text
dashboard/E-Commerce Dashboard.pbix
```

using **Microsoft Power BI Desktop**.

---

## 🖥️ Dashboard Preview

### E-Commerce Funnel Analytics Dashboard

![E-Commerce Funnel Analytics Dashboard]<img width="1326" height="748" alt="dashboard _preview" src="https://github.com/user-attachments/assets/60307406-759c-4de3-a5e1-b91525dcaab3" />


> Interactive Power BI dashboard showing the complete customer journey from product views to purchases, with KPI cards, funnel conversion analysis, revenue insights, customer segmentation, and interactive filters.


---

## 💡 Business Use Cases

This type of funnel analysis can support:

- Conversion-rate optimization
- Product-page optimization
- Checkout experience analysis
- Customer segmentation
- Marketing-channel evaluation
- Revenue analysis
- Product-category performance monitoring
- Device-specific customer experience analysis

---

## 🚀 Future Improvements

Potential extensions for the project include:

- Customer cohort analysis
- Repeat-purchase analysis
- Customer Lifetime Value (CLV)
- Retention analysis
- Time-based conversion trends
- Product-level funnel analysis
- Automated Power BI refresh
- Cloud deployment
- Predictive conversion modeling
- Anomaly detection
- A/B testing analysis

---

## 📚 Skills Demonstrated

```text
Power BI
DAX
SQL
Python
Pandas
SQLite
Data Cleaning
Data Modeling
Funnel Analysis
Conversion Analysis
Customer Segmentation
Revenue Analysis
Business Intelligence
Data Visualization
Dashboard Design
Business Storytelling
```

---

## 👨‍💻 Author

**Pritam Maha Man Singh**

Data Analyst | Power BI | SQL | Python | Data Analytics

---

## ⭐ Project

If you find this project useful for learning or portfolio inspiration, consider giving the repository a ⭐.

<img width="1326" height="748" alt="dashboard _preview" src="https://github.com/user-attachments/assets/3cf09f0a-3749-4604-a136-8d3cd20b6fea" />
