# E-commerce SQL Data Analysis Project

## Project Overview
This project analyzes an e-commerce dataset using PostgreSQL.

The goal is to explore sales performance, top customers, and revenue by country.

## Tools Used
- PostgreSQL
- SQL
- GitHub

## Dataset
The dataset contains 4 tables:
- customers
- products
- orders
- order_items

## Key Analysis

### Total Revenue
Calculated using:

SELECT SUM(quantity * unit_price)
FROM order_items;

### Revenue by Country

SELECT
c.country,
SUM(oi.quantity * oi.unit_price) AS revenue
FROM order_items oi
JOIN orders o ON oi.order_id = o.order_id
JOIN customers c ON o.customer_id = c.customer_id
GROUP BY c.country
ORDER BY revenue DESC;

### Top Customers

SELECT
c.customer_name,
SUM(oi.quantity * oi.unit_price) AS total_spent
FROM order_items oi
JOIN orders o ON oi.order_id = o.order_id
JOIN customers c ON o.customer_id = c.customer_id
GROUP BY c.customer_name
ORDER BY total_spent DESC
LIMIT 10;

## Insights
- Nigeria generated the highest revenue
- A small number of customers generate most sales
- Some products dominate total sales
