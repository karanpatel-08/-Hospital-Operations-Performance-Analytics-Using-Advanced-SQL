# 🏥 Hospital Operations Performance Analytics Using Advanced SQL

<div align="center">

![SQL](https://img.shields.io/badge/SQL-Advanced-blue?style=for-the-badge&logo=postgresql)
![Healthcare Analytics](https://img.shields.io/badge/Domain-Healthcare-success?style=for-the-badge)
![Business Intelligence](https://img.shields.io/badge/Analytics-Business%20Intelligence-orange?style=for-the-badge)
![Data Analysis](https://img.shields.io/badge/Project-Portfolio-red?style=for-the-badge)

</div>

---

# 📌 Project Overview

This project analyzes hospital operations data using advanced SQL techniques to generate executive-level operational insights for healthcare management.

The analysis focuses on:
- Doctor workload optimization
- Department performance tracking
- Revenue analysis
- Patient flow trends
- Operational efficiency monitoring
- Resource utilization

The project demonstrates how advanced SQL can transform raw healthcare datasets into actionable business intelligence.

---

# 🎯 Stakeholder Focus

### Primary Stakeholders
- Hospital Operations Team
- Executive Management

### Business Questions Solved
- Which doctors are overloaded?
- Which departments perform best?
- How is revenue distributed?
- Is operational activity increasing?
- Are patient visits concentrated?
- Which departments are improving or declining?

---

# 🛠️ Tools & Technologies

| Category | Tools |
|---|---|
| Database | SQL |
| Concepts | CTEs, Window Functions |
| Functions | RANK, NTILE, LAG, FIRST_VALUE |
| Analysis | Healthcare Analytics |
| Visualization Ready | Power BI Compatible |

---

# 📂 Dataset Overview

The dataset contains:
- Patients
- Doctors
- Appointments
- Treatments

The project includes large-scale hospital operational records enabling advanced healthcare analytics.

---

# 🧠 Advanced SQL Concepts Used

## ✅ Common Table Expressions (CTEs)
Used for layered analytical transformations.

## ✅ Window Functions
Implemented:
- `DENSE_RANK()`
- `NTILE()`
- `LAG()`
- `FIRST_VALUE()`
- `LAST_VALUE()`
- Running Totals

## ✅ Business Analytics SQL
- Trend Analysis
- Segmentation
- Operational KPIs
- Performance Comparison
- Revenue Contribution Analysis

---

# 📊 SQL Business Analysis

# 1️⃣ Doctor Workload Ranking

### Business Problem
How do doctors rank within their departments based on patient visits?

### Business Impact
- Identifies overloaded doctors
- Detects staffing imbalance
- Helps optimize scheduling

![](https://miro.medium.com/v2/resize:fit:1400/1*8q1Q6v2b0i4hK0h0lM0xCg.png)

---

# 2️⃣ Revenue Contribution Leaders

### Business Problem
Which doctors contribute most to hospital revenue?

### Business Impact
- Supports incentive planning
- Tracks financial contribution
- Helps performance evaluation

![](https://miro.medium.com/v2/resize:fit:1400/1*wK4Wf5tB4Lx4j8sK7n7s5Q.png)

---

# 3️⃣ Patient Visit Trend Change

### Business Problem
How are patient visits changing over time?

### Business Impact
- Monitors operational growth
- Tracks patient demand
- Detects inflow trends

![](https://miro.medium.com/v2/resize:fit:1400/1*L9VY5f9eU8x5PjN5K8JvLQ.png)

---

# 4️⃣ Cumulative Hospital Load

### Business Problem
How does hospital workload accumulate over time?

### Business Impact
- Supports capacity planning
- Helps operational forecasting
- Assists staffing decisions

![](https://miro.medium.com/v2/resize:fit:1400/1*8nP8z0d0zPjv5r0gW8A0RA.png)

---

# 5️⃣ High vs Low Utilization Doctors

### Business Problem
How can doctors be grouped by workload intensity?

### Business Impact
- Improves workload balancing
- Helps resource allocation
- Supports operational planning

![](https://miro.medium.com/v2/resize:fit:1400/1*h9Wf2u9sM9L2vJ0gY9w8yA.png)

---

# 6️⃣ Repeat Visit Gap Analysis

### Business Problem
How frequently do patients revisit the hospital?

### Business Impact
- Measures patient engagement
- Tracks follow-up behavior
- Supports continuity-of-care analysis

![](https://miro.medium.com/v2/resize:fit:1400/1*7gY3wL8z2u8v9X0kK2tQfA.png)

---

# 7️⃣ Department Performance Comparison

### Business Problem
How do departments compare with hospital averages?

### Business Impact
- Identifies top-performing departments
- Detects inefficiencies
- Helps strategic planning

![](https://miro.medium.com/v2/resize:fit:1400/1*3K7h9uA4vB7mM8kP1sW7NQ.png)

---

# 8️⃣ Doctor Consistency Analysis

### Business Problem
Which doctors consistently perform above average?

### Business Impact
- Identifies reliable performers
- Tracks operational consistency
- Supports leadership evaluation

![](https://miro.medium.com/v2/resize:fit:1400/1*6yD8kP2nQ9wV4fR7xT0cXg.png)

---

# 9️⃣ Treatment Cost Concentration

### Business Problem
Which treatments contribute most to overall costs?

### Business Impact
- Helps cost optimization
- Supports budgeting
- Improves financial planning

![](https://miro.medium.com/v2/resize:fit:1400/1*X8z0kL7fP5tN4rM2vW1yQA.png)

---

# 🔟 Operational Growth Momentum

### Business Problem
Is hospital operational activity accelerating?

### Business Impact
- Supports expansion planning
- Tracks operational momentum
- Assists infrastructure planning

![](https://miro.medium.com/v2/resize:fit:1400/1*4V7f9mN0kP8xQ2zL1sT5Rg.png)

---

# 💡 Sample SQL Query

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

# 📈 Business Impact

This project demonstrates how SQL-driven analytics can help hospitals:

✅ Optimize doctor workload  
✅ Improve operational efficiency  
✅ Monitor department performance  
✅ Support executive decision-making  
✅ Improve resource planning  
✅ Track hospital growth trends  

---

# 🚀 Key Highlights

✔ Real-world healthcare analytics project  
✔ Advanced SQL implementation  
✔ Executive-level business insights  
✔ Operational KPI analysis  
✔ Large-scale dataset analysis  
✔ Power BI-ready analytical approach  

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

Read the detailed article here:

👉 https://medium.com/@patelkp021/hospital-operations-performance-analytics-using-advanced-sql-a9474f55a438

---

# 👨‍💻 Author

## Karan Patel

Aspiring Data Analyst | SQL | Power BI | Business Intelligence | Healthcare Analytics

<div align="center">

### ⭐ If you found this project useful, consider giving it a star!

</div>
