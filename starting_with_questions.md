Answer the following questions and provide the SQL queries used to find the answer.

    
**Question 1: Which cities and countries have the highest level of transaction revenues on the site?**


SQL Queries:SELECT al.country,
                   al.city,
                   SUM(a.revenue)AS transaction_revenues
            FROM all_sessions al
            JOIN analytics a USING(fullvisitorid)
            GROUP BY al.country,al.city
            ORDER BY SUM(a.revenue) ASC
            LIMIT 5



Answer:The cities and country having the highest level of transaction revenues are United States South San Francisco with 82420000




**Question 2: What is the average number of products ordered from visitors in each city and country?**


SQL Queries:  SELECT al.fullvisitorid,
                     al.city,
                     al.country,
                     AVG(p.orderedquantity) AS average_orderedquantity
              FROM all_sessions al
              JOIN products p USING(productsku)
               GROUP BY al.fullvisitorid,al.city,al.country



Answer:The average number of products ordered from each city and country are outlined from the follwoing query.





**Question 3: Is there any pattern in the types (product categories) of products ordered from visitors in each city and country?**


SQL Queries:SELECT al.city,
                   al.country,
                   al.v2productcategory,
                   al.type,
                   COUNT(*) as Count
            FROM all_sessions al
            JOIN products p USING(productsku)
            GROUP BY al.city,al.country,al.v2productcategory,al.type
            ORDER BY count DESC



Answer: In this we can see the pattern of which product categories in ordered most from Country and city.





**Question 4: What is the top-selling product from each city/country? Can we find any pattern worthy of noting in the products sold?**


SQL Queries:SELECT al.city,
                   al.country,
                   sr.name,
                   SUM(a.revenue)
            FROM all_sessions al
           JOIN analytics a USING(fullvisitorid)
           JOIN sales_report sr USING(productsku)
           GROUP BY al.city,al.country,sr.name
           ORDER BY SUM(a.revenue) ASC



Answer:The top selling product is Android Wool Heather Cap Heather/Black from UnitedStates/Mountain View.





**Question 5: Can we summarize the impact of revenue generated from each city/country?**

SQL Queries:  SELECT al.city,
                     al.country,
                     a.revenue
             FROM all_sessions al
            JOIN analytics a USING(fullvisitorid)
            GROUP BY al.city,al.country,a.revenue
             ORDER BY revenue ASC



Answer: The imapct of Revenue generated is mostly from United States.







