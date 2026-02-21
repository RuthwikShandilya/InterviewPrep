##Pattern 1 : every month ,every day, last 30 days

find the customers who made purchase for every month last year :
SELECT name
FROM Cusomter
WHERE purchase_date >= CURRENT_DATE - INTERVAL '30 days'
GROUP BY name
HAVING COUNT(DISTINCT DATE(purchase_date)) = 30;

the point is to use distinct and count without using cte we can use having.more optimzed
