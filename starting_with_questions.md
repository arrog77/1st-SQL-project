Answer the following questions and provide the SQL queries used to find the answer.

    
**Question 1: Which cities and countries have the highest level of transaction revenues on the site?**


SQL Queries:SELECT al.country,al.city,SUM(a.revenue)AS transaction_revenues
            FROM all_sessions al
            JOIN analytics a USING(fullvisitorid)
            GROUP BY al.country,al.city
            ORDER BY SUM(a.revenue) ASC
            LIMIT 5



Answer:The cities and country having the highest level of transaction revenues are United States South San Francisco with 82420000




**Question 2: What is the average number of products ordered from visitors in each city and country?**


SQL Queries:



Answer:





**Question 3: Is there any pattern in the types (product categories) of products ordered from visitors in each city and country?**


SQL Queries:



Answer:





**Question 4: What is the top-selling product from each city/country? Can we find any pattern worthy of noting in the products sold?**


SQL Queries:SELECT al.city,al.country,sr.name,SUM(a.revenue)
            FROM all_sessions al
           JOIN analytics a USING(fullvisitorid)
           JOIN sales_report sr USING(productsku)
           GROUP BY al.city,al.country,sr.name
           ORDER BY SUM(a.revenue) ASC



Answer:The top selling product is Android Wool Heather Cap Heather/Black from UnitedStates/Mountain View.





**Question 5: Can we summarize the impact of revenue generated from each city/country?**

SQL Queries:



Answer:







