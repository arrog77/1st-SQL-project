What issues will you address by cleaning the data?
Cleaning data involves resolving various issues in the dataset to improve its quality, reliability and consistency.
The common issues addresses during cleaning the data includes:

1. Removing Redundant Records
2. Handling Missing Values
3. Changing Date Formats
     




Queries:
Below, provide the SQL queries you used to clean your data.

1. ALTER TABLE all_sessions
  DROP COLUMN eCommerceAction_type;
  DROP COLUMN searchkeyword;

2..SELECT 
      fullvisitorid,
	  COALESCE (sessionqualitydim,0) AS sessionqualitydim
FROM all_sessions

3.UPDATE analytics
SET revenue = (SET AVG(revenue)
			  FROM analytics
			  WHERE revenue IS NOT NULL)
WHERE revenue IS NULL;
