# Final-Project-Transforming-and-Analyzing-Data-with-SQL

## Project/Goals
The goal of this project was to find the some pattern related to sales of products and understand the data for better decision making process.

## Process
The process of the Transforming and Analyzing Data with SQL consists of following points
1. Data Understanding: This includes the understanding of tables,columns,datatypes and relationships.
2. Data Cleaning and Preparation: This step includes handling Null values, standardizing formats, correcting inconsistencies, removing duplicates and transforming data types.
3. Data Transformation : This include calculations,aggregations,joins, subqueries and window function.
4. Querying and Aggregating: This step includes writing SQL queries to extract the required data for analysis which involves selecting relevant columns,filtering rows based on conditions and aggregating data using functions such as COUNT,SUM,AVG.


## Results
I tried to look at the patterns of products ordered in each month and want to know which month has the largest.
       SELECT EXTRACT(MONTH FROM al.date) AS month,
       AVG(p.orderedquantity)AS avg_order,
       a.units_sold
FROM all_sessions al
JOIN analytics a USING(fullvisitorid)
JOIN products p USING(productsku)
GROUP BY EXTRACT(MONTH FROM al.date),a.units_sold
ORDER BY month

I tried to look at the customers of each city and their increase in number for every month.

SELECT fullvisitorid,city,date::DATE,
COUNT
(CASE WHEN city IS NOT NULL THEN fullvisitorid
ELSE NULL END)
OVER (ORDER BY date::DATE) AS Total_customers
FROM all_sessions
ORDER BY date

## Challenges 
Missing values,inconsistencies or incorrect data.
Cleaning and Validating data before was time-consuming and complex.

## Future Goals

Using statistical analysis and visualization functions to communicate complex information in a visual and understandable formats that helps in reporting. 
Identify patterns, trends and relationship in the data, making it easier to interpret and understand.
