# 🛍️ ShopEase E-Commerce Sales Analysis - SQL Assignment

![E-commerce Analytics](https://images.unsplash.com/photo-1551288049-bebda4e38f71?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG0dGhvLXBhd2dlfHx8fGVufDB8fHx8fA%3D%3D&auto=format&fit=crop&w=1470&q=80)

## 📌 Table of Contents

- [Introduction](#-introduction)
- [Business Scenario](#-business-scenario)
- [Database Schema](#-database-schema)
  - [Customers Table](#customers-table)
  - [Orders Table](#orders-table)
  - [Order Details Table](#order-details-table)
- [Tasks](#-tasks)
  - [Basic Queries](#basic-queries-25)
  - [Intermediate Queries](#intermediate-queries-35)
  - [Advanced Queries](#advanced-queries-40)
- [Setting Up the Database](#-setting-up-the-database)
- [How to Practice Online](#-how-to-practice-online)
- [Conclusion](#-conclusion)
- [Additional Resources](#-additional-resources)

---

## 🚀 Introduction

This SQL assignment helps you develop your skills by analyzing e-commerce data. It covers basic to advanced SQL techniques.

---

## 📝 Business Scenario

ShopEase wants to gain insights into its sales data to understand customer patterns, identify top products, detect fraud, and analyze revenue trends.

---

## 🗃️ Database Schema

The database contains three tables:

### Customers Table

| Column        | Type          | Description                            |
|---------------|---------------|----------------------------------------|
| `customer_id` | INT           | Primary key                            |
| `customer_name`| VARCHAR(100)  | Customer's full name                   |
| `email`       | VARCHAR(100)  | Contact email                          |
| `city`        | VARCHAR(50)   | City of residence                      |
| `country`     | VARCHAR(50)   | Country of residence                   |
| `signup_date` | DATE          | Date when customer joined              |

### Orders Table

| Column        | Type          | Description                            |
|---------------|---------------|----------------------------------------|
| `order_id`    | INT           | Primary key                            |
| `customer_id` | INT           | Foreign key to customers               |
| `order_date`  | DATE          | Date when the order was placed         |
| `total_amount`| DECIMAL(10,2) | Total value of the order               |
| `status`      | VARCHAR(20)   | Order status ('Completed', 'Pending', 'Cancelled') |

### Order Details Table

| Column            | Type           | Description                            |
|-------------------|----------------|----------------------------------------|
| `order_detail_id` | INT            | Primary key                            |
| `order_id`        | INT            | Foreign key to orders                  |
| `product_id`      | INT            | Product identifier                     |
| `quantity`        | INT            | Quantity of the product purchased      |
| `unit_price`      | DECIMAL(10,2)  | Price per unit                         |
| `total_price`     | DECIMAL(10,2)  | Total price for the line item          |

---

## 👨‍💻 Tasks

### 🔹 Basic Queries (25%)

1. Retrieve all completed orders placed in the last 30 days.
2. List the top 10 customers who have spent the most.
3. Get the number of customers per country with at least one order.
4. Retrieve all customers who live in the USA.
5. Find the total number of orders placed by each customer.
6. List all products purchased by customer 'Alice Johnson'.
7. Find the average order amount per order status.
8. Identify customers who signed up in the last 3 months but haven't placed orders.

### 🔹 Intermediate Queries (35%)

9. Calculate the average order value (AOV) for completed orders in the last 3 months.
10. Find the top 5 best-selling products by total quantity sold.
11. Identify customers who have orders but never completed one.
12. Calculate total revenue in the last 6 months.
13. Identify customers with multi-product orders.
14. List the top 3 products with the highest total sales value.
15. Retrieve all orders with a total amount greater than $100.
16. Calculate the percentage of completed orders vs. pending ones in the last 3 months.
17. Find customers who haven't placed orders in the last 6 months.

### 🔹 Advanced Queries (40%)

18. Identify customers who have placed at least 3 completed orders.
19. Find the month-over-month revenue growth rate for the last 6 months.
20. Detect potential fraud: customers who placed multiple orders exceeding $5,000 in a day.
21. Calculate the revenue contribution from the top 20% of customers (Pareto Principle: 80/20 rule).
22. Compute customer lifetime value by country.
23. Identify products frequently purchased together.
24. Compare weekly sales trends between Q1 and Q2 of the current year.
25. Segment customers based on purchasing frequency and average order value.
26. Determine which products need restocking based on sales velocity.

---

## 💻 **How to Practice Online**

1.  Visit [SQLiteOnline](https://sqliteonline.com/).
2.  Select **PostgreSQL** as your database.
3.  Copy and paste the schema and data insertion queries into the query editor.
4.  Start executing the assignment queries.

---

## 💾 Setting Up the Database

```sql
-- Create tables
CREATE TABLE customers (
    customer_id INT PRIMARY KEY,
    customer_name VARCHAR(100),
    email VARCHAR(100),
    city VARCHAR(50),
    country VARCHAR(50),
    signup_date DATE
);

CREATE TABLE orders (
    order_id INT PRIMARY KEY,
    customer_id INT,
    order_date DATE,
    total_amount DECIMAL(10,2),
    status VARCHAR(20),
    FOREIGN KEY (customer_id) REFERENCES customers(customer_id)
);

CREATE TABLE order_details (
    order_detail_id INT PRIMARY KEY,
    order_id INT,
    product_id INT,
    quantity INT,
    unit_price DECIMAL(10,2),
    total_price DECIMAL(10,2),
    FOREIGN KEY (order_id) REFERENCES orders(order_id)
);
```
---

## 💾 DDL Scripts for (Data insertion)

```sql
INSERT INTO customers VALUES
(1, 'Alice Johnson', 'alice@email.com', 'New York', 'USA', '2023-01-10'),
(2, 'Bob Smith', 'bob@email.com', 'Los Angeles', 'USA', '2023-02-15'),
(3, 'Carlos Ruiz', 'carlos@email.com', 'Madrid', 'Spain', '2023-03-05'),
(4, 'Diana Chen', 'diana@email.com', 'Beijing', 'China', '2023-04-18'),
(5, 'Emma Wilson', 'emma@email.com', 'London', 'UK', '2023-05-22');

INSERT INTO orders VALUES
(101, 1, '2024-01-10', 150.00, 'Completed'),
(102, 2, '2024-01-12', 200.00, 'Completed'),
(103, 3, '2024-01-15', 75.50, 'Pending'),
(104, 4, '2024-01-20', 320.00, 'Completed'),
(105, 1, '2024-02-05', 95.00, 'Completed'),
(106, 2, '2024-02-10', 225.00, 'Cancelled'),
(107, 1, '2024-03-01', 180.00, 'Completed'),
(108, 3, '2024-03-15', 420.00, 'Completed'),
(109, 4, '2024-04-02', 150.00, 'Pending'),
(110, 2, '2024-04-10', 300.00, 'Completed');

INSERT INTO order_details VALUES
(201, 101, 1, 2, 50.00, 100.00),
(202, 101, 2, 1, 50.00, 50.00),
(203, 102, 3, 1, 200.00, 200.00),
(204, 103, 4, 3, 25.00, 75.00),
(205, 104, 1, 4, 80.00, 320.00),
(206, 105, 5, 1, 95.00, 95.00),
(207, 106, 2, 3, 75.00, 225.00),
(208, 107, 3, 2, 90.00, 180.00),
(209, 108, 6, 3, 140.00, 420.00),
(210, 109, 2, 2, 75.00, 150.00),
(211, 110, 1, 2, 150.00, 300.00);

```
---

## 🎯 **Conclusion**

This assignment helps build SQL proficiency through practical e-commerce scenarios.

---

## 📚 **Additional Resources**

* SQL Documentation: [PostgreSQL Documentation](https://www.postgresql.org/docs/)
* SQL Tutorial: [W3Schools SQL Tutorial](https://www.w3schools.com/sql/)
* Online SQL Practice: [SQLZoo](https://sqlzoo.net/)
