Consider the data you have available to you. You can use the data to: - find all duplicate records - find the total number of unique visitors (fullVisitorID) - find the total number of unique visitors by referring sites - find each unique product viewed by each visitor - compute the percentage of visitors to the site that actually makes a purchase

In the starting_with_data.md file, write 3 - 5 new questions that you could answer with this database. For each question, include The queries you used to answer the question The answer to the question




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

Answer:



Question 4: find each unique product viewed by each visitor

SQL Queries:SELECT COUNT(DISTINCT al.fullvisitorid) AS unique_visitors,a.visitnumber,p.name
FROM all_sessions al
JOIN analytics a USING(fullvisitorid)
JOIN products p USING(productsku)
GROUP BY a.visitnumber,p.name
ORDER BY a.visitnumber DESC

Answer:



Question 5: compute the percentage of visitors to the site that actually makes a purchase

SQL Queries:

Answer:
