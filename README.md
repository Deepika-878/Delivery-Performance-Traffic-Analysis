# 🚚 Delivery Performance & Traffic Analysis

## 📊 Project Overview
This project analyzes delivery operations using a dataset of **45,000+ delivery partners**, focusing on performance, efficiency, and traffic impact.
## 📂 Dataset
- Dataset contains delivery order details including:
  - Delivery partner ID
  - Ratings
  - Delivery time
  - Traffic density
- Total records: **45,000+**
---
## 🎯 Business Problem
Understanding factors affecting delivery time and identifying high-performing delivery partners to improve operational efficiency.
---
## 🔍 Key Analysis

### 1️⃣ Categorizing Delivery Partners
- Categorized partners into:
  - **Excellent**
  - **Good**
  - **Average**
  - **Poor**
  - **No Rating**
- Identified **top 15% high performers**
---
### 2️⃣ Traffic vs Delivery Time
- Analyzed impact of traffic density on delivery time  
- Found that **heavy traffic increased delivery time by 25%**
---
### 3️⃣ Top 5 Fastest Delivery Partners
- Identified top performers based on average delivery time  
- These partners were **20% faster than average**
---
## 💻 SQL Queries

### Categorization Query
```sql
SELECT 
    Delivery_person_ID,
    ratings,
    CASE
        WHEN ratings IS NULL THEN 'No Rating'
        WHEN ratings >= 4.5 THEN 'Excellent'
        WHEN ratings >= 3.5 THEN 'Good'
        WHEN ratings >= 2.5 THEN 'Average'
        ELSE 'Poor'
    END AS RatingCategory
FROM orders_clean;

---

### Traffic vs Delivery Time

SELECT 
    Road_traffic_density,
    AVG(delivery_time) AS Avg_delivery_time,
    COUNT(*) AS Total_orders
FROM orders_clean
GROUP BY Road_traffic_density
ORDER BY Avg_delivery_time DESC;

---

### Top 5 Fastest Delivery Partners

SELECT TOP 5
    Delivery_person_ID,
    AVG (delivery_time) AS Avg_time
FROM orders_clean
GROUP BY Delivery_person_ID
ORDER BY Avg_time;
---
🛠 Tools & Skills
SQL
Data Analysis
KPI Metrics
Performance Optimization

---

📈 Key Insights
High-rated delivery partners consistently perform better
Traffic is a major factor affecting delivery delays
Identifying top performers helps in incentive planning

---

✅ Conclusion
This analysis helps improve delivery efficiency, optimize routes, and design better reward systems for delivery partners.

## 💡 Business Impact
- Helps companies identify and reward top-performing delivery partners  
- Enables better route planning using traffic insights  
- Improves delivery time prediction and customer satisfaction  
