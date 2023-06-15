Question 1: find all duplicate records

SQL Queries:SELECT fullvisitorid,productsku,COUNT(*) AS count
FROM all_sessions
GROUP BY fullvisitorid,productsku
HAVING COUNT(*) >1;

Answer: From all_sessions table I wanted to find how many duplicates were there in primary and foreign key and I quered only them as it makes sense to see duplicates in them.



Question 2: find the total number of unique visitors (fullVisitorID)

SQL Queries:SELECT COUNT(DISTINCT fullvisitorid)
            FROM all_sessions

Answer:The total number of unique visitors is 14223.



Question 3: find the total number of unique visitors by referring sites 

SQL Queries: SELECT COUNT(DISTINCT al.fullvisitorid) AS unique_visitors,a.visitnumber
           FROM all_sessions al
           JOIN analytics a USING(fullvisitorid)
           GROUP BY a.visitnumber

Answer:The highest number of unique visitors by referring sites is 3273.



Question 4: find each unique product viewed by each visitor

SQL Queries:SELECT COUNT(DISTINCT al.fullvisitorid) AS unique_visitors,a.visitnumber,p.name
FROM all_sessions al
JOIN analytics a USING(fullvisitorid)
JOIN products p USING(productsku)
GROUP BY a.visitnumber,p.name
ORDER BY a.visitnumber DESC

Answer:The unique product viewed by each visitor is outlined with the following query.



Question 5: compute the percentage of visitors to the site that actually makes a purchase

SQL Queries:SELECT (COUNT(DISTINCT a.visitid)/COUNT(DISTINCT al.visitid)) * 100 AS visitors_percentage
FROM analytics a
LEFT  JOIN all_sessions al USING(visitid)

Answer: The percentage of visitors to the site that actually makes a purchase was 40.

New Question : Which is the most number of produt that is sold?
SQL Queries:  SELECT al.city,al.country,p.name,a.units_sold
              FROM all_sessions al
               JOIN analytics a USING(fullvisitorid)
              JOIN products p USING(productsku)
               GROUP BY 1,2,3,4
              HAVING a.units_sold IS NOT NULL
              ORDER BY 4 DESC
Answer: The most units_sold is Collapsible Pet Bowl.
