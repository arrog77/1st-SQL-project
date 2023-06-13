Consider the data you have available to you. You can use the data to: - find all duplicate records - find the total number of unique visitors (fullVisitorID) - find the total number of unique visitors by referring sites - find each unique product viewed by each visitor - compute the percentage of visitors to the site that actually makes a purchase

In the starting_with_data.md file, write 3 - 5 new questions that you could answer with this database. For each question, include The queries you used to answer the question The answer to the question




Question 1: find all duplicate records

SQL Queries:SELECT fullvisitorid,productsku,COUNT(*) AS count
FROM all_sessions
GROUP BY fullvisitorid,productsku
HAVING COUNT(*) >1;

Answer: From all_sessions table I wanted to find how many duplicates were there in primary and foreign key and I quered only them as it makes sense to see duplicates in them.



Question 2: 

SQL Queries:

Answer:



Question 3: 

SQL Queries:

Answer:



Question 4: 

SQL Queries:

Answer:



Question 5: 

SQL Queries:

Answer:
