# Master-SQL-For-Science
Course on Udemy

#### Example SQL code

```
Here is my solution to the employee count by the department with a total count.
SELECT department,count(*) as emp_count
FROM employees
GROUP BY department
UNION
SELECT 'TOTAL',count(*) as emp_count
FROM employees
ORDER BY emp_count;
```
