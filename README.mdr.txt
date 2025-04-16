⸻

Task 6: Sales Trend Analysis Using Aggregations

Objective

To analyze monthly revenue and order volume trends using SQL aggregation techniques.

⸻

Dataset

Name: vehicle_sales_data.csv
Columns:
	•	order_id – Unique identifier for each order
	•	order_date – Date when the order was placed
	•	amount – Total amount of the order
	•	product_id – ID of the product ordered

⸻

Tools Used
	•	SQLite (v3.49)
	•	Command Line / SQLite CLI

⸻

Steps Followed
	1.	Created SQLite Table                                                                CREATE TABLE vehicle_sales_data (
    order_id INTEGER,
    order_date TEXT,
    amount REAL,
    product_id INTEGER
);
2.imported Data from csv
.mode csv
.import vehicle_sales_data.csv vehicle_sales_data
3.Analyzed Monthly Revenue and Order Volume
CREATE TABLE monthly_sales_summary AS
SELECT 
    strftime('%Y', order_date) AS year,
    strftime('%m', order_date) AS month,
    SUM(amount) AS total_revenue,
    COUNT(DISTINCT order_id) AS total_orders
FROM vehicle_sales_data
GROUP BY year, month
ORDER BY year, month; 
4.view results
SELECT * FROM monthly_sales_summary;
Output
	•	A table showing monthly sales trends
	•	Identified top 3 highest revenue-generating months

⸻

Learning Outcome
	•	Learned how to use GROUP BY, SUM(), COUNT(DISTINCT), and strftime() for time-based analysis in SQL.
	•	Understood how to import .csv data into SQLite.
	•	Practiced creating result tables and querying for trends.