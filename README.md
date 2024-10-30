# My-Analysis-and-Finding-Using-SQL

### Project Title: Data Insights and Analysis Using SQL: A Comprehensive Exploration

[Project Overview](#project-overview)

[Project Objectives](#project-objectives)

[Data Sources](#data-sources)

[Tools Used](#tools-used)

[Queries](#queries)

[Exploratory Data Analysis](#exploratory-data-analysis)

[Conclusion](#conclusion)


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


#### Queries 
----------------------
    1.                SELECT *
               FROM [dbo].[Retail_Sales_Analysis]
                WHERE sale_date = '2022-11-05';

![analysis findingQ1](https://github.com/user-attachments/assets/700cf517-0846-4894-8223-dfb7ec8f9846)

                

    2.         SELECT *
               FROM [dbo].[Retail_Sales_Analysis]
               WHERE category = 'Clothing'
               AND quantity> 10
               AND sale_date BETWEEN '2022-11-01' AND '2022-11-30';

   ![analysis findingQ2](https://github.com/user-attachments/assets/07c5b077-3580-4e34-b45d-e1e5d826d076)



     3.         SELECT category, SUM(total_sale) AS total_sales
                FROM [dbo].[Retail_Sales_Analysis]
                GROUP BY category;
![analysis findingQ3](https://github.com/user-attachments/assets/b89a62ad-5787-4e06-b379-57eb04c62ec4)

    


     4.         SELECT AVG(age) AS average_age
                FROM [dbo].[Retail_Sales_Analysis]
                WHERE category = 'Beauty';
   
![analysis findingQ4](https://github.com/user-attachments/assets/3cc141be-2238-4c05-a9f0-31b92a374801)

   


     5.         SELECT * 
                FROM [dbo].[Retail_Sales_Analysis] 
                WHERE total_sale > 1000;
  ![analysis findingQ5](https://github.com/user-attachments/assets/97e33616-b181-4077-b6d9-043e6588f255)


   

     6.         SELECT gender, category, COUNT(transactions_id) AS total_transactions
                FROM [dbo].[Retail_Sales_Analysis]
                GROUP BY gender, category;   
![analysis findingQ6](https://github.com/user-attachments/assets/010af58f-dc6a-43bb-ae9e-b09e9fb0a1cb)

   

     7.         SELECT 
                YEAR(sale_date) AS year, 
                MONTH(sale_date) AS month, 
                AVG(total_sale) AS average_sale
                FROM [dbo].[Retail_Sales_Analysis]
                GROUP BY YEAR(sale_date), MONTH(sale_date)
                ORDER BY average_sale DESC;
                
![analysis findingQ7](https://github.com/user-attachments/assets/73b4a978-ba51-4d01-a807-295e10fa9c8f)




     8.        SELECT TOP (5) [total_sale]
               From [dbo].[Retail_Sales_Analysis]
![analysis findingQ8](https://github.com/user-attachments/assets/0e475a28-53f1-4ebc-ba4c-468619f93aba)

 


     9.        SELECT category, COUNT(DISTINCT customer_id) AS unique_customers
               FROM [dbo].[Retail_Sales_Analysis]
               GROUP BY category; 
   ![analysis findingQ9](https://github.com/user-attachments/assets/d31cd6b3-422c-4a1e-abd9-00a6b42f722a)



     10.        SELECT 
                CASE 
                WHEN DATEPART(HOUR, sale_time) < 12 THEN 'Morning'
                WHEN DATEPART(HOUR, sale_time) BETWEEN 12 AND 17 THEN 'Afternoon'
                  ELSE 'Evening'
                END AS Shift,
                COUNT(*) AS Number_of_Orders
                FROM [dbo].[Retail_Sales_Analysis]
                GROUP BY 
                CASE 
                WHEN DATEPART(HOUR, sale_time) < 12 THEN 'Morning'
                WHEN DATEPART(HOUR, sale_time) BETWEEN 12 AND 17 THEN 'Afternoon'
                  ELSE 'Evening'
                    END
               ORDER BY 
               Shift;
![analysis findingQ10](https://github.com/user-attachments/assets/517f661f-9568-4f7a-bc58-4c3d3315c767)

      


### Conclusion
----------------------
In conclusion, this project effectively demonstrates the power of SQL in analyzing and deriving valuable insights from structured data. Using SQL Management Studio, I executed a series of targeted queries to filter, manipulate, and transform data, uncovering key trends and patterns that can drive business decisions. My analysis enabled me to identify actionable insights that highlight customer behaviors, sales performance, and category trends. Using SQL queries on these data fields, I was able to analyze sales performance, customer demographics, product popularity, and profitability. This information supports data-driven decision-making to optimize inventory, target marketing efforts, and improve sales strategies.

The project underscores how SQL serves as an essential tool for data-driven problem-solving and strategic decision-making, showcasing the potential of structured data analysis in addressing complex business business challenges.


THIS PROJECT WAS ASSIGNED TO ME BY: 
#### MR. FEMI AYODELE (LITA)






