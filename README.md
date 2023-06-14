# Final-Project-Transforming-and-Analyzing-Data-with-SQL

## Project/Goals


## Process
### (your step 1)
### (your step 2)

## Results
I tried to look at the patterns of products ordered in each month and want to know which month has the largest.
SELECT EXTRACT(MONTH FROM al.date) AS month,AVG(p.orderedquantity)AS avg_order,a.units_sold
FROM all_sessions al
JOIN analytics a USING(fullvisitorid)
JOIN products p USING(productsku)
GROUP BY EXTRACT(MONTH FROM al.date),a.units_sold
ORDER BY month

## Challenges 
(discuss challenges you faced in the project)

## Future Goals
(what would you do if you had more time?)
