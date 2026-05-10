# 🏥 Hospital Operations Performance Analytics Using Advanced SQL

<div align="center">

![SQL](https://img.shields.io/badge/SQL-Advanced-blue?style=for-the-badge&logo=postgresql)
![Healthcare Analytics](https://img.shields.io/badge/Domain-Healthcare-success?style=for-the-badge)
![Business Intelligence](https://img.shields.io/badge/Analytics-Business%20Intelligence-orange?style=for-the-badge)
![Data Analysis](https://img.shields.io/badge/Project-Case%20Study-red?style=for-the-badge)

</div>

---

# 📌 Project Overview

Healthcare organizations generate huge volumes of operational data daily, but raw transactional data alone cannot support executive-level decision-making.

This project demonstrates how advanced SQL can transform raw hospital data into actionable operational intelligence by analyzing:
- doctor performance
- patient flow
- department efficiency
- revenue contribution
- operational growth trends
- resource utilization

The project focuses on solving real-world hospital management problems using advanced SQL analytics techniques.

---

# 🎯 Business Problem

Hospital management teams often struggle with:
- Uneven doctor workload
- Department bottlenecks
- Lack of operational visibility
- Resource allocation challenges
- Revenue tracking inefficiencies
- Monitoring operational growth

This project addresses these challenges through SQL-driven analytics and KPI reporting.

---

# 🛠️ Tools & Technologies

| Category | Tools Used |
|---|---|
| Database | SQL |
| SQL Concepts | CTEs, Window Functions |
| Functions | RANK, DENSE_RANK, NTILE, LAG |
| Domain | Healthcare Analytics |
| Reporting | Business Intelligence |
| Visualization | SQL Output Reporting |

---

# 📂 Dataset Information

The dataset contains simulated hospital operational data including:

- Patients
- Doctors
- Appointments
- Treatments
- Billing
- Departments
- Hospital visit records

The project works on large-scale operational healthcare records to simulate real business analytics scenarios.

---

# 🧠 Advanced SQL Concepts Used

## ✅ Common Table Expressions (CTEs)
Used for modular and layered analytical query design.

## ✅ Window Functions
Implemented:
- `RANK()`
- `DENSE_RANK()`
- `NTILE()`
- `LAG()`
- `FIRST_VALUE()`
- Running Totals

## ✅ Aggregate Functions
Used:
- `SUM()`
- `AVG()`
- `COUNT()`
- `MAX()`
- `MIN()`

## ✅ Business Analytics SQL
- Trend Analysis
- Segmentation
- KPI Analysis
- Performance Ranking
- Growth Analysis

---

# 📊 SQL Business Case Studies

---

# 1️⃣ Doctor Workload Ranking

## 📌 Business Question
Which doctors are handling the highest number of patient visits within each department?

## 🎯 Objective
Identify overloaded doctors and workload imbalance across departments.

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

## 📈 Output

![](https://miro.medium.com/v2/resize:fit:1400/1*8q1Q6v2b0i4hK0h0lM0xCg.png)

---

## 💡 Business Insight
- Identified departments with workload concentration
- Detected overloaded doctors
- Highlighted staffing imbalance
- Helped improve operational planning

---

# 2️⃣ Revenue Contribution Analysis

## 📌 Business Question
Which doctors contribute the most to hospital revenue?

## 🎯 Objective
Track financial contribution and identify high-performing doctors.

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
GROUP BY doctor_name, department;
```

---

## 📈 Output

![](https://miro.medium.com/v2/resize:fit:1400/1*wK4Wf5tB4Lx4j8sK7n7s5Q.png)

---

## 💡 Business Insight
- Identified top revenue-generating doctors
- Supported performance-based evaluation
- Improved financial visibility

---

# 3️⃣ Patient Visit Trend Analysis

## 📌 Business Question
How are patient visits changing over time?

## 🎯 Objective
Monitor operational growth and patient demand trends.

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

## 📈 Output

![](https://miro.medium.com/v2/resize:fit:1400/1*L9VY5f9eU8x5PjN5K8JvLQ.png)

---

## 💡 Business Insight
- Tracked operational growth
- Measured patient demand changes
- Helped forecast future hospital load

---

# 4️⃣ Department Performance Comparison

## 📌 Business Question
Which departments perform above or below hospital averages?

## 🎯 Objective
Benchmark departmental performance against hospital-wide metrics.

---

## 💻 SQL Query

```sql
SELECT 
    department,
    AVG(patient_count) AS avg_patients,
    
    CASE
        WHEN AVG(patient_count) >
            (SELECT AVG(patient_count)
             FROM department_summary)
        THEN 'Above Average'
        
        ELSE 'Below Average'
    END AS performance_status

FROM department_summary
GROUP BY department;
```

---

## 📈 Output

![](https://miro.medium.com/v2/resize:fit:1400/1*3K7h9uA4vB7mM8kP1sW7NQ.png)

---

## 💡 Business Insight
- Identified high-performing departments
- Detected underperforming operational units
- Supported strategic improvement initiatives

---

# 5️⃣ Operational Growth Momentum

## 📌 Business Question
Is hospital operational activity accelerating over time?

## 🎯 Objective
Measure operational momentum and growth consistency.

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

## 📈 Output

![](https://miro.medium.com/v2/resize:fit:1400/1*4V7f9mN0kP8xQ2zL1sT5Rg.png)

---

## 💡 Business Insight
- Monitored long-term operational growth
- Supported expansion planning
- Improved capacity forecasting

---

# 📈 Overall Business Impact

This project demonstrates how SQL analytics can help hospitals:

✅ Optimize doctor workload  
✅ Improve operational efficiency  
✅ Monitor department performance  
✅ Support executive decision-making  
✅ Improve resource allocation  
✅ Forecast hospital operational demand  
✅ Track business growth trends  

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

# 📁 Recommended Project Structure

```bash
Hospital-Operations-Analytics/
│
├── datasets/
├── sql_queries/
├── screenshots/
├── README.md
└── project_summary.pdf
```

---

# 🔗 Medium Blog

Read the complete detailed explanation here:

👉 https://medium.com/@patelkp021/hospital-operations-performance-analytics-using-advanced-sql-a9474f55a438

---

# 👨‍💻 Author

## Karan Patel

Aspiring Data Analyst | SQL | Power BI | Business Intelligence | Healthcare Analytics

<div align="center">

### ⭐ If you found this project useful, consider giving it a star!

</div>
