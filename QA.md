What are your risk areas? Identify and describe them.

Risk areas include issues such as data quality problems, security vulnerabilities and complaince risks. The risk areas are identified and desribed using SQL queries which are listed below:
1. Data Quality
2. Identifying duplicate records based on specific columns
3. Verifying data types and formats
4. Checking for Unique values in column
5. Checking NULL values 

QA Process:
Describe your QA process and include the SQL queries used to execute it.

1.SELECT fullvisitorid,country,date::DATE,
       COUNT(CASE WHEN city IS NOT NULL THEN fullvisitorid 
			ELSE NULL END)
			OVER(ORDER BY date::DATE) as Total
  FROM all_sessions
  ORDER BY date ;

2.SELECT fullvisitorid,country,COUNT(*) AS duplicate_count
   FROM all_sessions
   GROUP BY fullvisitorid,country
   HAVING COUNT(*)>1;
   
3. SELECT column_name,data_type
   FROM information_schema.columns
   WHERE table_name ='all_sessions';
   
4.SELECT visitid,COUNT(*) AS duplicate_count
  FROM all_sessions
  GROUP BY visitid
  HAVING COUNT(*)>1;
  
5.SELECT city,COUNT(*) AS null_count
FROM all_sessions
WHERE city = 'not available in demo dataset' OR city = '(not set)'
GROUP BY city;

