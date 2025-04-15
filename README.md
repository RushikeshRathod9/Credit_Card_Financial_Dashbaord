# 💳 Credit Card Financial Dashboard

An interactive Power BI dashboard project designed to deliver actionable insights into credit card operations using real-time data.

## 📌 Project Objective

Develop a comprehensive **credit card weekly dashboard** to provide stakeholders with real-time visibility into key metrics and trends, enabling better monitoring and analysis of:

- Revenue generation
- Customer demographics
- Transaction patterns
- Product performance
- Regional contributions

---

## 🛠 Tools & Technologies

- **Power BI** – for interactive visualizations and DAX modeling  
- **PostgreSQL** – for data storage and management  
- **Microsoft Excel** – for data preparation  
- **DAX Queries** – for custom calculations and KPIs  
- **SQL Server Connection** – to connect Power BI directly to the database

---

## 📥 Data Source

> Public GitHub Repository:
  https://github.com/RushikeshRathod9/Credit_Card_Financial_Dashbaord

---

## 🗂 Data Import Workflow

1. Prepare the `.csv` data files.
2. Create and define tables in PostgreSQL.
3. Import the `.csv` files into the SQL database.
4. Connect Power BI to the SQL Server instance.

---

## 📊 Key DAX Calculations

```dax
-- Age Group
AgeGroup = SWITCH(
  TRUE(),
  'public cust_detail'[customer_age] < 30, "20-30",
  'public cust_detail'[customer_age] >= 30 && 'public cust_detail'[customer_age] < 40, "30-40",
  'public cust_detail'[customer_age] >= 40 && 'public cust_detail'[customer_age] < 50, "40-50",
  'public cust_detail'[customer_age] >= 50 && 'public cust_detail'[customer_age] < 60, "50-60",
  'public cust_detail'[customer_age] >= 60, "60+", "unknown"
)

-- Income Group
IncomeGroup = SWITCH(
  TRUE(),
  'public cust_detail'[income] < 35000, "Low",
  'public cust_detail'[income] >= 35000 && 'public cust_detail'[income] < 70000, "Medium",
  'public cust_detail'[income] >= 70000, "High", "unknown"
)

-- Revenue Calculation
Revenue = 'public cc_detail'[annual_fees] + 'public cc_detail'[total_trans_amt] + 'public cc_detail'[interest_earned]

-- Weekly Revenue
Current_week_Revenue = CALCULATE(
  SUM('public cc_detail'[Revenue]),
  FILTER(ALL('public cc_detail'), 'public cc_detail'[week_num2] = MAX('public cc_detail'[week_num2]))
)

Previous_week_Revenue = CALCULATE(
  SUM('public cc_detail'[Revenue]),
  FILTER(ALL('public cc_detail'), 'public cc_detail'[week_num2] = MAX('public cc_detail'[week_num2]) - 1)
)
```

---

## 📈 Key Insights (Week 53)

- 🔺 **Revenue increased by 28.8%** (WoW)
- 📈 Total transaction amount and count also rose significantly.
- 👥 **Customer count** increased.
- 💰 **YTD Revenue:** $57M  
- 🏦 **Interest Earned:** $8M  
- 🧾 **Total Transaction Amount:** $46M  
- 🧍‍♂️🧍‍♀️ Revenue split: Male - $31M, Female - $26M  
- 💳 **Blue & Silver cards** account for 93% of transactions  
- 🗺 **Top contributing states:** TX, NY, CA (68%)  
- ⚡ **Activation Rate:** 57.5%  
- ❌ **Delinquency Rate:** 6.06%

---

## 📄 Add to Resume

**Credit Card Financial Dashboard using Power BI, PostgreSQL, and Excel:**

- Designed and developed an interactive dashboard using transactional and customer data from a SQL database.
- Applied DAX and SQL for KPI tracking and insight generation.
- Shared key metrics and findings to enable data-driven decisions.
