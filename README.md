# Retail-Sales_Analysis-MySQL

## Project OverView

**Project Title** : Retail Sales Analysis
**Level**:Beginner

This project is designed to demonstrate SQL skills and techniques typically used by data analysts to explore, clean, and analyze retail sales data. The project involves setting up a retail sales database, performing exploratory data analysis (EDA), and answering specific business questions through SQL queries. 

## Objectives
* Set up a retail sales database: Create and populate a retail sales database with the provided sales data.
* Data Cleaning: Identify and remove any records with missing or null values.
* Exploratory Data Analysis (EDA): Perform basic exploratory data analysis to understand the dataset.
* Business Analysis: Use SQL to answer specific business questions and derive insights from the sales data.


## Project Structure

### 1.DATABASE SETUP
* Database Creation: The project starts by creating a database named 'retail_sales_db'.
* Table Import: the csv file as been imported for MYSQL workbench

### 2. DATA EXPLORATION & CLEANING
   
* Updating data type:updated and converted string to date format.
* Modified Column: Modified the column Names in the dataset.
* Record Count: Determine the total number of records in the dataset.
* Customer Count: Find out how many unique customers are in the dataset.
* Category Count: Identify all unique product categories in the dataset.

```sql
SELECT COUNT(*) FROM retail_sales_dataset;
DESCRIBE retail_sales_dataset;
UPDATE retail_sales_dataset
SET sales_date = STR_TO_DATE(sales_date, '%d-%m-%Y');

ALTER TABLE retail_sales_dataset
MODIFY COLUMN sales_date DATE;

ALTER TABLE retail_sales_dataset
CHANGE sales_date Sales_date DATE;

SELECT * FROM retail_sales_dataset
WHERE
	Transaction_ID is null or Sales_date is null or Customer_ID is null or 
    Gender is null or Age is null or Product_Category is null or Quantity is null or
    Price_per_Unit is null or Total_Amount is null;
    
SELECT COUNT(*) AS TOTAL_SALES FROM retail_sales_dataset;
SELECT distinct Product Category FROM retail_sales_dataset;
```

### Data Analysis & Findings
 
The following SQL queries were developed to answer specific business questions

1.**Write a SQL query to retrieve all columns for sales made on ''2023-04-25**
```sql
SELECT *
FROM retail_sales_dataset
WHERE Sales_date='2023-04-25';
```

2. **Write a SQL query to retrieve all transactions where the category is 'Clothing' and the quantity sold is more than 4 in the month of April-2023**:
```sql
SELECT * FROM retail_sales_dataset
WHERE Product_Category='clothing'
AND Sales_date BETWEEN '2023-4-1' AND '2023-4-30' 
AND Quantity >=4;
```

3. **Write a SQL query to calculate the total sales (total_sale) for each category.**:
```sql
SELECT Product_Category ,sum(Total_Amount) as Total_Sales,count(*) as Total_orders
FROM retail_sales_dataset
GROUP BY Product_Category;
```

4. **Write a SQL query to find the average age of customers who purchased items from the 'Beauty' category.**:
```sql
SELECT 
round(AVG(AGE),0)
from retail_sales_dataset
WHERE Product_Category='Beauty';
```

5. **Write a SQL query to find all transactions where the total_sale is greater than 1000.**:
```sql
SELECT *
FROM retail_sales_dataset
WHERE Total_Amount >1000;
```

## Findings

- **Customer Demographics**: The dataset includes customers from various age groups, with sales distributed across different categories such as Clothing and Beauty.
- **High-Value Transactions**: Several transactions had a total sale amount greater than 1000, indicating premium purchases.
- **Sales Trends**: Monthly analysis shows variations in sales, helping identify peak seasons.


  ## Reports

- **Sales Summary**: A detailed report summarizing total sales, customer demographics, and category performance.
- **Trend Analysis**: Insights into sales trends across different months.
- **Customer Insights**: Reports on top customers and unique customer counts per category.

  ## Conclusion

This project serves as a comprehensive introduction to SQL for data analysts, covering database setup, data cleaning, exploratory data analysis, and business-driven SQL queries. The findings from this project can help drive business decisions by understanding sales patterns, customer behavior, and product performance.
