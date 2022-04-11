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
