# Store-Data-Analysis

# 📊 Store Performance Analysis Dashboard

This project provides an in-depth analysis of store performance using customer traffic, marketing spend, store size, staffing, and overhead data. The dashboard combines **interactive visualizations** (Altair) and **static plots** (Seaborn & Matplotlib) for a well-rounded view of operational efficiency, space utilization, staff productivity, and anomaly detection across retail stores.

---

## 🧠 Key Objectives

- Evaluate marketing spend effectiveness.
- Measure space utilization efficiency.
- Segment stores by customer volume.
- Identify top and bottom performing stores.
- Detect operational anomalies.
- Visualize seasonal trends.
- Provide actionable business insights.

---

## 📦 Data Sources

Data is dynamically loaded using a unique student ID:

```python
student_id = "001349369"
base_url = f"https://tinyurl.com/ChrisCoDV/{student_id}"
```

### Loaded Datasets:
| Dataset        | Description                                  |
|----------------|----------------------------------------------|
| StoreDailyCustomers.csv | Daily customer footfall per store      |
| StoreMarketing.csv       | Marketing spend per store             |
| StoreOverheads.csv       | Monthly overhead costs                |
| StoreSize.csv            | Physical size of each store (m²)     |
| StoreStaff.csv           | Number of staff in each store        |

---

## 🚀 How It Works

### 🔧 Data Preprocessing

- Converts `Date` to `datetime` for time-based analysis.
- Melts customer data into a long format for easier plotting.
- Merges store-specific data into a single summary DataFrame.

---

## 📐 Feature Engineering

We calculate key performance indicators for each store:

- **CustomersPer£**: Total customers per pound of marketing spend.
- **CustomersPerSqm**: Customers per square meter of store space.
- **CustomersPerStaff**: Staff efficiency measured by customer traffic.

We also classify stores based on:
- **Operational Status**: `Operational`, `Closed`, or `New`.
- **Customer Volume**: `Low`, `Medium`, or `High` (based on percentiles).

---

## 📈 Visualizations

### 1️⃣ Marketing Spend Effectiveness (Altair Interactive)

Shows how marketing investments influence customer visits.

- **X-axis**: Marketing Spend (£)
- **Y-axis**: Total Customers
- **Color**: Volume Segment
- **Tooltip**: Store, Marketing, Size

📌 _Use this to identify outliers and marketing ROI._

---

### 2️⃣ Space Utilization Efficiency (Altair Interactive)

Analyzes how store space is used.

- **X-axis**: Store Size (m²)
- **Y-axis**: Customers Per Sqm
- **Bubble Size**: Total Customers
- **Color**: Volume Segment

📌 _Spot high-density stores and optimize space allocation._

---

### 3️⃣ Customer Volume Distribution (Boxplot)

Compares customer traffic across volume segments.

📌 _Understand distribution and variation by segment._

---

### 4️⃣ Staff Productivity (Bar Chart)

Top 10 stores with highest customers per staff member.

📌 _Find which stores maximize their workforce best._

---

### 5️⃣ Overhead Cost Analysis (Scatter Plot)

Compares overheads against customer volume.

- **Hue**: Store Status
- **Style**: Volume Segment

📌 _High cost but low traffic? This graph highlights inefficiencies._

---

### 6️⃣ Correlation Matrix (Heatmap)

Shows correlations between numeric features:

- Marketing (£)
- Overheads (£)
- Size (m²)
- Staff
- Customers

📌 _Reveal linear relationships between business factors._

---

## 📉 Seasonal Trend Decomposition

Using `statsmodels`, we perform decomposition on customer time series for:

- **Top 3 Stores**
- **Bottom 3 Stores**

Each store's time series is broken into:
- **Trend**
- **Seasonality**
- **Residuals**

📌 _Discover periodic behavior and long-term trends._

---

## ⚠️ Anomaly Detection & Reporting

We flag anomalies based on:

| Criteria                          | Threshold                  |
|----------------------------------|----------------------------|
| Low Marketing Efficiency         | < 0.5 customers per £1     |
| High Overheads                   | > £100,000                 |
| Non-Operational Stores           | Status: `New` or `Closed` |

Anomalies are displayed in a readable markdown table format.

---

## 💾 Output & Export

- Static plots can be saved as `.png` using `plt.savefig()`.
- Interactive charts are displayed directly using Altair.

---

## 📚 Dependencies

Make sure the following Python libraries are installed:

```bash
pip install pandas numpy matplotlib seaborn altair statsmodels
```

---

## 📎 Usage

1. Clone or download this notebook/script.
2. Set your own `student_id` if applicable.
3. Run cells sequentially in a Jupyter Notebook environment.
4. Explore interactive charts and static graphs.
5. Analyze seasonal trends and investigate flagged anomalies.

---

## 🧩 Example Output: Anomaly Summary

```
=== Identified Anomalies ===
Marketing efficiency threshold: < 0.5 customers/£
Overhead threshold: > £100,000

| Store   | Status   |   Customers |   Marketing (£) |   Overheads (£) |   CustomersPer£ |
|:--------|:---------|------------:|----------------:|----------------:|----------------:|
| QUF     | New      |       11859 |            2000 |           83000 |          5.93   |
| RIK     | New      |        4538 |            1000 |           46000 |          4.54   |
| AIO     | Closed   |       16043 |            2000 |           91000 |          8.02   |
```

---

## 👤 Author

**Name:** Muhammad Amaz Majid  
**Project:** Store Operational Insights & Strategy
