# My-Analysis-and-Finding-Using-SQL

### Project Title: Data Insights and Analysis Using SQL: A Comprehensive Exploration

### Project Overview: 
-----------------------
 This project uses SQL (Structured Query Language) to analyze and extract meaningful insights from a dataset.
 The objective is to showcase how SQL can be used to query, manipulate, and transform data to solve business problems, uncover trends, and generate actionable findings. 
 Working with a structured database, various SQL commands and techniques will be applied, including data filtering, aggregation, joins, and subqueries.

### Project Objectives: 
------------------------
 - Understand the Dataset: Explore the structure and content of the dataset to ensure effective analysis.
 - Extract and Manipulate Data: Use SQL queries to retrieve, filter, and organize data for deeper analysis.
 - Perform Advanced Queries: Apply techniques like joins, subqueries, and aggregation to analyze data across multiple tables.
 - Generate Insights: Identify key patterns, trends, and actionable findings through data analysis.
 - Present Key Findings: Summarize insights in a clear, structured manner, highlighting their practical implications.

### Data Sources: 
-------------------------
The data sources include the following keys:
 1. Transactions_id: This is a unique identifier for each transaction.
 2. Sale_date: The date when the sale occurred.
 3. Sale_time: The time when the sale took place.
 4. Customer_id: The unique identifier for each customer.
 5. Gender: this entails customer gender.
 6. Age: This shows the age of customers.
 7. Category: This shows the product category being sold.
 8. Quantity: This shows the number of units sold.
 9. Price per Unit: This shows  the cost of a single unit of the product.
 10. Cogs: This shows the cost of goods sold; the direct cost to produce the sold item.
 11. Total Sales: Total revenue generated from the sale (Quantity × Price per Unit).

These datasets collectively provide a comprehensive view of sales performance, customer behavior, and market dynamics, enabling informed decision-making.

### Tools Used
-------------------
 - SQL MANAGEMENT STUDIO...

 ### Exploratory Data Analysis
 -----------------------------
EDA involves exploring the data to answer some questions about the data such as;
  1.  Write a SQL query to retrieve all columns for sales made on '2022-11-05'
  2.  Write a SQL query to retrieve all transactions where the category is 'Clothing' and the quantity sold is more than 10 in the month of Nov-2022.
  3.  Write a SQL query to calculate the total sales (total_sale) for each category.
  4.  Write a SQL query to find the average age of customers who purchased items from the 'Beauty' category.
  5.  Write a SQL query to find all transactions where the total_sale is greater than 1000.
  6.  Write a SQL query to find the total number of transactions (transaction_id) made by each gender in each category.
  7.  Write a SQL query to calculate the average sale for each month. Find out best selling month in each year.
  8.  Write a SQL query to find the top 5 customers based on the highest total sales.
  9.  Write a SQL query to find the number of unique customers who purchased items from each category.
  10. Write a SQL query to create each shift and number of orders (Example Morning <=12, Afternoon Between 12 & 17, Evening >17).


#### QUERIES 
----------------------
    1.                SELECT *
               FROM [dbo].[SALES]
                WHERE sale_date = '2022-11-05';

    2.         SELECT *
               FROM SALES
               WHERE category = 'Clothing'
               AND quantity> 10
               AND sale_date BETWEEN '2022-11-01' AND '2022-11-30';


     3.         SELECT category, SUM(total_sale) AS total_sales
                FROM SALES
                GROUP BY category;


     4.         SELECT AVG(age) AS average_age
                FROM SALES
                WHERE category = 'Beauty';


     5.         SELECT * 
                FROM SALES 
                WHERE total_sale > 1000;

     6.         SELECT gender, category, COUNT(transactions_id) AS total_transactions
                FROM SALES
                GROUP BY gender, category;   

     7.         SELECT 
                YEAR(sale_date) AS year, 
                MONTH(sale_date) AS month, 
                AVG(total_sale) AS average_sale
                FROM SALES
                GROUP BY YEAR(sale_date), MONTH(sale_date)
                ORDER BY average_sale DESC;


     8.        SELECT TOP (5) [total_sale]
               From SALES 


     9.        SELECT category, COUNT(DISTINCT customer_id) AS unique_customers
               FROM sales
               GROUP BY category; 


     10.        SELECT 
                CASE 
                WHEN DATEPART(HOUR, sale_time) < 12 THEN 'Morning'
                WHEN DATEPART(HOUR, sale_time) BETWEEN 12 AND 17 THEN 'Afternoon'
                  ELSE 'Evening'
                END AS Shift,
                COUNT(*) AS Number_of_Orders
                FROM SALES
                GROUP BY 
                CASE 
                WHEN DATEPART(HOUR, sale_time) < 12 THEN 'Morning'
                WHEN DATEPART(HOUR, sale_time) BETWEEN 12 AND 17 THEN 'Afternoon'
                  ELSE 'Evening'
                    END
               ORDER BY 
               Shift;


      
