# Customer Churn Analysis (IBM Telco)

Exploratory data analysis on IBM Telco customer data to identify the key drivers of churn and surface actionable retention insights.

---

## Dataset

| | |
|---|---|
| **Source** | IBM Telco Customer Churn (`Telco-Customer-Churn.csv`) |
| **Records** | 7,043 customers |
| **Features** | 21 (demographics, services, contract, billing, churn label) |
| **Target** | `Churn` — Yes / No |

---

## Project Structure

```
├── Customer_Churn_EDA.ipynb   # Main notebook
├── Telco-Customer-Churn.csv   # Dataset
└── README.md
```

---

## Libraries Used

```python
pandas
numpy
matplotlib
seaborn
```

---

## Workflow

### 1. Data Loading & Cleaning
- Loaded the CSV and coerced `TotalCharges` to numeric (handling blank strings)
- Mapped `SeniorCitizen` from `0/1` to `No/Yes`
- Created binary `ChurnFlag` column for numeric aggregations

### 2. Feature Engineering
Four new features were engineered to improve segmentation:

| Feature | Description |
|---|---|
| `TenureBand` | Tenure grouped into 5 bands: 0–3 mo, 4–12 mo, 13–24 mo, 25–48 mo, 49–72 mo |
| `ChargeBucket` | Monthly charges bucketed: \$0–35, \$35–55, \$55–75, \$75–95, \$95+ |
| `ContractBucket` | Contract type mapped to Short-Term, Mid-Term, Long-Term |
| `ServiceCount` | Count of add-on services subscribed (out of 6) |

### 3. Churn Statistics
Computed overall churn rate and breakdowns by:
- Contract type
- Internet service type
- Senior citizen status

### 4. Exploratory Data Analysis
10 visualizations across the following themes:

| # | Chart | Key Variable |
|---|---|---|
| 1–2 | Tenure histograms (churned vs retained) | `tenure` |
| 3 | Monthly charges histogram overlay | `MonthlyCharges` |
| 4 | Box plot — tenure by contract type & churn | `Contract`, `tenure` |
| 5 | Box plot — monthly charges by internet service & churn | `InternetService`, `MonthlyCharges` |
| 6 | Correlation heatmap (numerical features) | `tenure`, `MonthlyCharges`, `TotalCharges`, `ServiceCount`, `ChurnFlag` |
| 7 | Bar chart — churn rate by contract type | `Contract` |
| 8 | Bar chart — churn rate by tenure band | `TenureBand` |
| 9 | Dual-axis chart — churn rate & customer count by service count | `ServiceCount` |
| 10 | Heatmap — churn rate by feature subscription status | 7 service features |

---

## Key Findings

- **50%** of churners left within the first **12 months** — new customers are the highest-risk group
- **Month-to-month** customers churn at a far higher rate than one-year or two-year contract holders
- Churned customers pay **higher average monthly charges** than retained customers
- **Fiber optic** users pay the highest charges yet have the highest churn rate — a value-perception gap
- Customers with **0 add-on services** churn at nearly **2× the rate** of those with 4+ services
- **OnlineSecurity** and **TechSupport** subscribers churn far less than non-subscribers
- **Tenure** has a negative correlation with churn — longer-tenured customers rarely leave

---

## How to Run

1. Clone the repository and ensure the dataset CSV is in the same directory as the notebook.
2. Install dependencies:
   ```bash
   pip install pandas numpy matplotlib seaborn
   ```
3. Open and run the notebook:
   ```bash
   jupyter notebook Customer_Churn_EDA.ipynb
   ```

---

## Author
Proteek Chatterjee
Data analysis project using Python for exploratory data analysis and visualization.





