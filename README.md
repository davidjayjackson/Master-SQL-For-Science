# Master-SQL-For-Science
Course on Udemy

### Example SQL code 
#### Here is my solution to the employee count by the department with a total count.
```
SELECT department,count(*) as emp_count
FROM employees
GROUP BY department
UNION
SELECT 'TOTAL',count(*) as emp_count
FROM employees
ORDER BY emp_count;
```

#### MY solution to first/last hire date
```
WITH min_max_date
AS
(
SELECT min(hire_date) as min_date, max(hire_date) as max_date FROM employees
)
SELECT first_name,department,hire_date,r.country
FROM employees e
INNER JOIN min_max_date
ON e.hire_date = min_max_date.min_date OR e.hire_date = min_max_date.max_date
INNER JOIN regions r
ON e.region_id = r.region_id;
```

#### From SQL Practice Problems: 33
The manager has changed his mind. Instead of requiring that customers have at least one individual order totaling $10,000 or more, he wants to define high-value customers differently. Now, high value customers are customers who have orders totaling $15,000 or more in 2016. How would you change the answer to the problem above?

(Vasilik, Sylvia Moestl. SQL Practice Problems: 57 beginning, intermediate, and advanced challenges for you to solve using a “learn-by-doing” approach (p. 47). Kindle Edition.)

```
WITH big_spenders 
AS
(
SELECT o.CustomerID,CompanyName,
SUM(UnitPrice * Quantity) as TotalOrderAmount
FROM Orders o
INNER JOIN OrderDetails d
ON o.OrderID = d.OrderID
INNER JOIN Customers c
ON o.CustomerID = c.CustomerID
WHERE YEAR(OrderDate) =2016
GROUP BY o.CustomerID,CompanyName
)
SELECT *
FROM  big_spenders 
WHERE TotalOrderAmount >=15000
ORDER BY TotalOrderAmount desc;
```
