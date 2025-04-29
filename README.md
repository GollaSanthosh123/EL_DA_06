# Task 06 - SQL Data Analysis

This task is part of my Data Analyst Internship at **Elavate Labs**. The goal of this task was to perform SQL-based analysis on an e-commerce dataset, focusing on revenue insights using various SQL functions.

##  Task Overview

### Key SQL Operations Used:

- **EXTRACT**: Extracted the **month** from the `Date` column to perform time-based analysis.
- **GROUP BY**:
  - Grouped data by **month** to calculate monthly total revenue.
  - Grouped data by **year** to calculate yearly total revenue.
- **SUM()**: Used to compute the **total revenue** for different time periods.
- **DISTINCT**: Retrieved **unique values** from a specific column.
- **ORDER BY**: Sorted the total revenue in **descending order** to identify high-performing periods.
- **LIMIT**: Displayed a **limited number of rows**, such as top months or years by revenue.

## Tools Used

- **SQL**
- **MySQL Workbench** 

## Interview Questions & Answers

1. How do you group data by month and year?
-- Grouping by year and month to calculate total revenue
SELECT YEAR(date_col) AS year, MONTH(date_col) AS month, SUM(revenue)
FROM sales
GROUP BY year, month;

2. What's the difference between COUNT(*) and COUNT(DISTINCT col)?
-- COUNT(*) counts all rows; COUNT(DISTINCT col) counts only unique values in the column.

3. How do you calculate monthly revenue?
-- Grouping by month to get monthly revenue
SELECT MONTH(date_col) AS month, SUM(revenue) AS total_revenue
FROM sales
GROUP BY month;

4. What are aggregate functions in SQL?
-- Functions like SUM(), AVG(), MAX(), MIN(), and COUNT() that operate on sets of values and return a single value.

5. How to handle NULLs in aggregates?
-- Aggregates ignore NULLs by default; use COALESCE(col, 0) to treat NULLs as 0.
SELECT SUM(COALESCE(revenue, 0)) FROM sales;

6. What’s the role of ORDER BY and GROUP BY?
-- GROUP BY is used for aggregation; ORDER BY is used to sort the result set.
-- Example:
SELECT category, SUM(sales) AS total
FROM products
GROUP BY category
ORDER BY total DESC;

7. How do you get the top 3 months by sales?
-- Use ORDER BY with LIMIT to get top results
SELECT MONTH(date_col) AS month, SUM(revenue) AS total
FROM sales
GROUP BY month
ORDER BY total DESC
LIMIT 3;
