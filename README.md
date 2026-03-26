# Delivery Performance & Traffic Analysis

## Project Overview
This project analyzes delivery operations using a dataset of **45,000+ delivery partners**, focusing on performance, traffic impact, and efficiency.

## Key Objectives
- Categorize delivery partners based on customer ratings
- Analyze the impact of traffic density on delivery time
- Identify top-performing delivery partners

## Key Insights
- Top 15% of delivery partners identified as high performers
- Heavy traffic increased delivery time by 25%
- Top 5 delivery partners were 20% faster than average

## SQL Analysis

### 1. Categorizing Delivery Partners 
SELECT 
    Id,
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

2. **Traffic vs Delivery Time**
SELECT
   Road_traffic_density,
   AVG(delivery_time) AS Avg_delivery_time,
COUNT(*) AS Total_orders
FROM orders_clean
GROUP BY Road_traffic_density
ORDER BY Avg_delivery_time DESC;

3. **Top 5 Fastest Delivery Partners**
SELECT TOP 5
   Delivery_person_ID,
   AVG (delivery_time) AS Avg_time
FROM orders_clean
GROUP BY Delivery_person_ID
ORDER BY Avg_time;

 **Tools & Skills**
-SQL
-Data Analysis
-KPI Metrics
-Performance Optimization

**Conclusion**
This project provides insights to improve delivery efficiency, optimize routes, and reward top-performing delivery partners.
