# 🏥 Hospital Operations Performance Analytics Using Advanced SQL

<div align="center">

![SQL](https://img.shields.io/badge/SQL-Advanced-blue?style=for-the-badge&logo=postgresql)
![Healthcare Analytics](https://img.shields.io/badge/Domain-Healthcare-success?style=for-the-badge)
![Business Intelligence](https://img.shields.io/badge/Analytics-Business%20Intelligence-orange?style=for-the-badge)
![Case Study](https://img.shields.io/badge/Project-SQL%20Case%20Study-red?style=for-the-badge)

</div>

---

# 📌 Project Overview

Healthcare organizations generate massive amounts of operational data daily, but raw transactional data alone cannot support strategic decision-making.

This project demonstrates how advanced SQL can transform hospital operational data into actionable business intelligence by analyzing:

- Doctor workload distribution
- Department performance
- Revenue contribution
- Patient visit trends
- Operational growth
- Resource utilization

The project focuses on solving real-world healthcare analytics problems using advanced SQL techniques and business-focused reporting.

---

# 🎯 Business Problem

Hospital management teams often face challenges such as:

- Uneven doctor workload
- Department bottlenecks
- Lack of operational visibility
- Resource allocation inefficiencies
- Revenue tracking limitations
- Difficulty monitoring operational growth

This project addresses these problems through SQL-driven KPI analysis and operational intelligence reporting.

---

# 🛠️ Tools & Technologies

| Category | Tools Used |
|---|---|
| Database | SQL |
| SQL Concepts | CTEs, Window Functions |
| Functions | RANK, DENSE_RANK, NTILE, LAG |
| Domain | Healthcare Analytics |
| Reporting | Business Intelligence |
| Analysis Type | Operational Analytics |

---

# 📂 Dataset Information

The dataset contains simulated hospital operational records including:

- Patients
- Doctors
- Appointments
- Departments
- Billing
- Treatments
- Visit records

The project uses large-scale healthcare transactional data to simulate real-world analytical reporting scenarios.

---

# 🧠 Advanced SQL Concepts Used

## ✅ Common Table Expressions (CTEs)

Used for modular and layered analytical query building.

---

## ✅ Window Functions

Implemented:
- `RANK()`
- `DENSE_RANK()`
- `NTILE()`
- `LAG()`
- `FIRST_VALUE()`
- Running Totals

---

## ✅ Aggregate Functions

Used:
- `SUM()`
- `AVG()`
- `COUNT()`
- `MAX()`
- `MIN()`

---

## ✅ Business Analytics SQL

- Trend Analysis
- KPI Reporting
- Segmentation
- Ranking Analysis
- Operational Intelligence

---

# 📊 SQL Business Case Studies

---

# 1️⃣ Doctor Workload Ranking

## 📌 Business Question

Which doctors are handling the highest number of patient visits within each department?

---

## 💻 SQL Query

```sql
WITH doctor_visits AS (
    SELECT 
        d.department,
        d.doctor_id,
        d.doctor_name,
        COUNT(a.visit_id) AS total_visits
    FROM doctors d
    JOIN appointments a
        ON d.doctor_id = a.doctor_id
    GROUP BY 
        d.department,
        d.doctor_id,
        d.doctor_name
)

SELECT 
    department,
    doctor_name,
    total_visits,
    
    DENSE_RANK() OVER (
        PARTITION BY department
        ORDER BY total_visits DESC
    ) AS department_rank

FROM doctor_visits;
```

---

## 💡 Business Insight

- Identified overloaded doctors
- Detected workload imbalance
- Improved staffing visibility
- Supported operational planning

---

# 2️⃣ Revenue Contribution Analysis

## 📌 Business Question

Which doctors contribute the most to hospital revenue?

---

## 💻 SQL Query

```sql
SELECT 
    doctor_name,
    department,

    SUM(billing_amount) AS total_revenue,

    RANK() OVER (
        ORDER BY SUM(billing_amount) DESC
    ) AS revenue_rank

FROM hospital_records

GROUP BY 
    doctor_name,
    department;
```

---

## 💡 Business Insight

- Identified top revenue-generating doctors
- Improved revenue visibility
- Supported financial performance tracking
- Enabled contribution analysis

---

# 3️⃣ Patient Visit Trend Analysis

## 📌 Business Question

How are patient visits changing over time?

---

## 💻 SQL Query

```sql
SELECT 
    visit_month,
    total_visits,

    LAG(total_visits) OVER (
        ORDER BY visit_month
    ) AS previous_month_visits,

    total_visits -
    LAG(total_visits) OVER (
        ORDER BY visit_month
    ) AS growth_difference

FROM monthly_hospital_visits;
```

---

## 💡 Business Insight

- Tracked patient demand growth
- Measured operational momentum
- Supported forecasting analysis
- Improved planning visibility

---

# 4️⃣ Department Performance Comparison

## 📌 Business Question

Which departments perform above hospital averages?

---

## 💻 SQL Query

```sql
SELECT 
    department,

    AVG(patient_count) AS avg_patients,

    CASE
        WHEN AVG(patient_count) >
            (
                SELECT AVG(patient_count)
                FROM department_summary
            )
        THEN 'Above Average'

        ELSE 'Below Average'
    END AS performance_status

FROM department_summary

GROUP BY department;
```

---

## 💡 Business Insight

- Identified high-performing departments
- Detected underperforming units
- Improved strategic planning
- Enhanced operational benchmarking

---

# 5️⃣ Operational Growth Momentum

## 📌 Business Question

Is hospital operational activity increasing consistently?

---

## 💻 SQL Query

```sql
SELECT 
    report_month,
    total_operations,

    SUM(total_operations) OVER (
        ORDER BY report_month
    ) AS cumulative_operations

FROM hospital_operations;
```

---

## 💡 Business Insight

- Monitored long-term operational growth
- Supported infrastructure planning
- Improved resource forecasting
- Enabled capacity analysis

---

# 📈 Overall Business Impact

This project demonstrates how SQL analytics can help hospitals:

✅ Optimize doctor workload  
✅ Improve operational efficiency  
✅ Monitor department performance  
✅ Support executive decision-making  
✅ Improve resource allocation  
✅ Forecast operational demand  
✅ Track long-term growth trends  

---

# 🚀 Key Project Highlights

✔ Real-world healthcare analytics use case  
✔ Advanced SQL implementation  
✔ Business-focused KPI analysis  
✔ Executive-level reporting approach  
✔ Window function optimization  
✔ Operational intelligence reporting  
✔ Recruiter-friendly SQL case study project  

---

# 📁 Project Structure

```bash
Hospital-Operations-Analytics/
│
├── datasets/
├── sql_queries/
├── README.md
└── project_summary.pdf
```

---

# 🔗 Medium Blog

Detailed project explanation:

👉 https://medium.com/@patelkp021/hospital-operations-performance-analytics-using-advanced-sql-a9474f55a438

---

# 👨‍💻 Author

## Karan Patel

Aspiring Data Analyst | SQL | Power BI | Business Intelligence | Healthcare Analytics

<div align="center">

### ⭐ If you found this project useful, consider giving it a star!

</div>
