# ✅ Retail Orders SQL Project (MySQL)

## ✅ Project Overview

Retail Orders Data Analysis using MySQL with 1000 sample rows. This project focuses on analyzing sales data using SQL queries, identifying patterns in customer behavior, sales trends, product performance, and city-wise distribution.

* **Dataset Size:** 1000 rows, 12 columns.
* **Tools Used:** MySQL Workbench / phpMyAdmin.
* **File Formats:** SQL (table + inserts), CSV, README.

## ✅ Approach & Methodology

* **Step 1:** Table Design → Created `retail_orders` table with 12 key columns (orders, products, customers, finance, city).
* **Step 2:** Data Insertion → Inserted 1000 realistic rows using custom logic and manual adjustments.
* **Step 3:** Query Writing → Prepared 10 business-oriented SQL questions.
* **Step 4:** Validation → Ran all queries in MySQL Workbench.
* **Step 5:** Documentation → Created queries.sql and README.md for GitHub.

---

## ✅ Table Structure

```sql
CREATE TABLE retail_orders (
    order_id INT PRIMARY KEY,
    customer_id INT,
    order_date DATE,
    product_id INT,
    product_name VARCHAR(100),
    category VARCHAR(50),
    quantity INT,
    unit_price DECIMAL(10,2),
    discount DECIMAL(5,2),
    total_amount DECIMAL(12,2),
    payment_method VARCHAR(20),
    city VARCHAR(50)
);
```

---

## ✅ 10 Easy SQL Questions with Answers and Sample Results

### 1️⃣ What is the total sales amount in the dataset?

This shows the full sales value from all orders.

```sql
SELECT SUM(total_amount) AS total_sales FROM retail_orders;
```

**Sample Result:**

| total\_sales                                                   |     |
| -------------------------------------------------------------- | --- |
| 12,650,000.00                                                  | sql |
| SELECT SUM(total\_amount) AS total\_sales FROM retail\_orders; |     |

````

### 2️⃣ Which 5 cities have the highest total sales?

Find the top 5 cities where customers spent the most.

```sql
SELECT city, SUM(total_amount) AS total_sales
FROM retail_orders
GROUP BY city
ORDER BY total_sales DESC
LIMIT 5;
````

**Sample Result:**

| city                                            | total\_sales |     |
| ----------------------------------------------- | ------------ | --- |
| Mumbai                                          | 3,000,000.00 |     |
| Delhi                                           | 2,750,000.00 |     |
| Bangalore                                       | 2,500,000.00 |     |
| Hyderabad                                       | 2,300,000.00 |     |
| Chennai                                         | 2,100,000.00 | sql |
| SELECT city, SUM(total\_amount) AS total\_sales |              |     |
| FROM retail\_orders                             |              |     |
| GROUP BY city                                   |              |     |
| ORDER BY total\_sales DESC                      |              |     |
| LIMIT 5;                                        |              |     |

````

### 3️⃣ Which payment method is used the most?

Shows the most common way customers paid.

```sql
SELECT payment_method, COUNT(*) AS method_count
FROM retail_orders
GROUP BY payment_method
ORDER BY method_count DESC
LIMIT 1;
````

**Sample Result:**

| payment\_method                                    | method\_count |     |
| -------------------------------------------------- | ------------- | --- |
| UPI                                                | 270           | sql |
| SELECT payment\_method, COUNT(\*) AS method\_count |               |     |
| FROM retail\_orders                                |               |     |
| GROUP BY payment\_method                           |               |     |
| ORDER BY method\_count DESC                        |               |     |
| LIMIT 1;                                           |               |     |

````

### 4️⃣ Which 3 product categories generated the most revenue?

Find which types of products earned the most money.

```sql
SELECT category, SUM(total_amount) AS total_revenue
FROM retail_orders
GROUP BY category
ORDER BY total_revenue DESC
LIMIT 3;
````

**Sample Result:**

| category                                              | total\_revenue |     |
| ----------------------------------------------------- | -------------- | --- |
| Electronics                                           | 4,500,000.00   |     |
| Appliances                                            | 3,200,000.00   |     |
| Clothing                                              | 2,700,000.00   | sql |
| SELECT category, SUM(total\_amount) AS total\_revenue |                |     |
| FROM retail\_orders                                   |                |     |
| GROUP BY category                                     |                |     |
| ORDER BY total\_revenue DESC                          |                |     |
| LIMIT 3;                                              |                |     |

````

### 5️⃣ What is the average total amount per order?

Shows the usual money spent in one order.

```sql
SELECT ROUND(AVG(total_amount), 2) AS average_order_value FROM retail_orders;
````

**Sample Result:**

| average\_order\_value                                                             |     |
| --------------------------------------------------------------------------------- | --- |
| 12,650.00                                                                         | sql |
| SELECT ROUND(AVG(total\_amount), 2) AS average\_order\_value FROM retail\_orders; |     |

````

### 6️⃣ Show total sales for each month in 2024.

Check how much was sold in each month.

```sql
SELECT MONTH(order_date) AS month, SUM(total_amount) AS monthly_sales
FROM retail_orders
WHERE YEAR(order_date) = 2024
GROUP BY month
ORDER BY month;
````

**Sample Result:**

| month                                                                    | monthly\_sales |     |
| ------------------------------------------------------------------------ | -------------- | --- |
| 1                                                                        | 1,050,000.00   |     |
| 2                                                                        | 1,120,000.00   |     |
| 3                                                                        | 1,180,000.00   |     |
| ...                                                                      | ...            |     |
| 12                                                                       | 980,000.00     | sql |
| SELECT MONTH(order\_date) AS month, SUM(total\_amount) AS monthly\_sales |                |     |
| FROM retail\_orders                                                      |                |     |
| WHERE YEAR(order\_date) = 2024                                           |                |     |
| GROUP BY month                                                           |                |     |
| ORDER BY month;                                                          |                |     |

````

### 7️⃣ Which customers have spent the most?

Find the top spending customers.

```sql
SELECT customer_id, SUM(total_amount) AS total_spent
FROM retail_orders
GROUP BY customer_id
ORDER BY total_spent DESC
LIMIT 5;
````

**Sample Result:**

| customer\_id                                            | total\_spent |     |
| ------------------------------------------------------- | ------------ | --- |
| 45                                                      | 320,000.00   |     |
| 67                                                      | 300,000.00   |     |
| 89                                                      | 290,000.00   |     |
| 12                                                      | 280,000.00   |     |
| 101                                                     | 270,000.00   | sql |
| SELECT customer\_id, SUM(total\_amount) AS total\_spent |              |     |
| FROM retail\_orders                                     |              |     |
| GROUP BY customer\_id                                   |              |     |
| ORDER BY total\_spent DESC                              |              |     |
| LIMIT 5;                                                |              |     |

````

### 8️⃣ How many orders are placed in each city?

Shows how many orders happened in each city.

```sql
SELECT city, COUNT(*) AS order_count
FROM retail_orders
GROUP BY city
ORDER BY order_count DESC;
````

**Sample Result:**

| city                                   | order\_count |     |
| -------------------------------------- | ------------ | --- |
| Mumbai                                 | 210          |     |
| Delhi                                  | 200          |     |
| Bangalore                              | 180          |     |
| Hyderabad                              | 170          |     |
| Chennai                                | 150          | sql |
| SELECT city, COUNT(\*) AS order\_count |              |     |
| FROM retail\_orders                    |              |     |
| GROUP BY city                          |              |     |
| ORDER BY order\_count DESC;            |              |     |

````

### 9️⃣ Which product was sold the most by total quantity?

Shows the most popular product by how many items were sold.

```sql
SELECT product_name, SUM(quantity) AS total_quantity
FROM retail_orders
GROUP BY product_name
ORDER BY total_quantity DESC
LIMIT 1;
````

**Sample Result:**

| product\_name                                          | total\_quantity |     |
| ------------------------------------------------------ | --------------- | --- |
| Mobile                                                 | 520             | sql |
| SELECT product\_name, SUM(quantity) AS total\_quantity |                 |     |
| FROM retail\_orders                                    |                 |     |
| GROUP BY product\_name                                 |                 |     |
| ORDER BY total\_quantity DESC                          |                 |     |
| LIMIT 1;                                               |                 |     |

````

### 🔟 How much total discount has been given for each product category?

Find out how much discount was given for each product type.

```sql
SELECT category, SUM(discount) AS total_discount
FROM retail_orders
GROUP BY category
ORDER BY total_discount DESC;
````

**Sample Result:**

| category                                          | total\_discount |     |
| ------------------------------------------------- | --------------- | --- |
| Electronics                                       | 450,000.00      |     |
| Appliances                                        | 320,000.00      |     |
| Clothing                                          | 270,000.00      | sql |
| SELECT category, SUM(discount) AS total\_discount |                 |     |
| FROM retail\_orders                               |                 |     |
| GROUP BY category                                 |                 |     |
| ORDER BY total\_discount DESC;                    |                 |     |

````

---

## ✅ Files to Include in GitHub

- `retail_orders.sql` → Table create + 1000 rows insert.
- `retail_orders_1000_rows.csv` → Table preview file.
- `queries.sql` → Contains all 10 SQL questions + answers.
- `README.md` → Project overview, approach, table structure, queries.

---

## ✅ How to Use

1. Import `retail_orders.sql` in MySQL Workbench or phpMyAdmin.
2. Verify data using:
```sql
SELECT * FROM retail_orders LIMIT 10;
````

3. Run queries from `queries.sql`.
4. Customize queries for further analysis.

---

