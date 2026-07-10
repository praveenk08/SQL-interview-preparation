# Day 3 - ORDER BY Clause

## Topic

**Sorting Data Using ORDER BY**

---

## Why Do We Need ORDER BY?

By default, SQL does not guarantee the order of returned rows.

The `ORDER BY` clause is used to sort data in ascending or descending order.

Examples:

* Top-selling products
* Highest-paid employees
* Latest orders
* Students ranked by marks

---

## SQL Query

### Sort Employees by Salary (Ascending)

```sql
SELECT *
FROM Employees
ORDER BY salary ASC;
```

### Sort Employees by Salary (Descending)

```sql
SELECT *
FROM Employees
ORDER BY salary DESC;
```

### Sort by Employee Name

```sql
SELECT *
FROM Employees
ORDER BY employee_name ASC;
```

### Sort by Multiple Columns

```sql
SELECT *
FROM Employees
ORDER BY department ASC,
         salary DESC;
```

---

## Sample Table

| employee_id | employee_name | department | salary |
| ----------- | ------------- | ---------- | ------ |
| 1           | Praveen       | IT         | 50000  |
| 2           | Amit          | HR         | 45000  |
| 3           | Ravi          | IT         | 60000  |
| 4           | Neha          | Finance    | 55000  |

---

## Output (ORDER BY salary DESC)

```text
employee_id | employee_name | department | salary
-------------------------------------------------
3           | Ravi          | IT         | 60000
4           | Neha          | Finance    | 55000
1           | Praveen       | IT         | 50000
2           | Amit          | HR         | 45000
```

---

## Real-World Backend Example

Show the latest orders first:

```sql
SELECT *
FROM Orders
ORDER BY created_at DESC;
```

Show top-paid employees:

```sql
SELECT employee_name,
       salary
FROM Employees
ORDER BY salary DESC;
```

This is commonly used in dashboards, admin panels, reports, and APIs.

---

# Interview Questions

## Q1. What is the purpose of ORDER BY?

### Answer

The `ORDER BY` clause is used to sort the result set based on one or more columns.

Example:

```sql
SELECT *
FROM Employees
ORDER BY salary DESC;
```

---

## Q2. What is the default sorting order?

### Answer

If no order is specified, SQL uses ascending order (`ASC`) by default.

```sql
SELECT *
FROM Employees
ORDER BY salary;
```

Equivalent to:

```sql
SELECT *
FROM Employees
ORDER BY salary ASC;
```

---

## Q3. What is the difference between ASC and DESC?

### ASC (Ascending)

```sql
SELECT *
FROM Employees
ORDER BY salary ASC;
```

Output:

```text
45000
50000
55000
60000
```

### DESC (Descending)

```sql
SELECT *
FROM Employees
ORDER BY salary DESC;
```

Output:

```text
60000
55000
50000
45000
```

---

## Q4. Can ORDER BY be used with multiple columns?

### Answer

Yes.

```sql
SELECT *
FROM Employees
ORDER BY department ASC,
         salary DESC;
```

SQL first sorts by department and then by salary.

---

## Q5. Which executes first: ORDER BY or SELECT?

### Answer

Logical execution order:

```text
FROM
WHERE
GROUP BY
HAVING
SELECT
ORDER BY
LIMIT
```

`ORDER BY` executes after `SELECT`.

---

## Q6. Can we sort by column position?

### Answer

Yes.

```sql
SELECT employee_id,
       employee_name,
       salary
FROM Employees
ORDER BY 3 DESC;
```

Here `3` refers to the third selected column (`salary`).

However, using column names is recommended for readability.

---

## Q7. Can ORDER BY be used with aliases?

### Answer

Yes.

```sql
SELECT employee_name,
       salary AS employee_salary
FROM Employees
ORDER BY employee_salary DESC;
```

---

## Common Interview Scenario

### Question

Retrieve the top 5 highest-paid employees.

### Answer

```sql
SELECT *
FROM Employees
ORDER BY salary DESC
LIMIT 5;
```

For SQL Server:

```sql
SELECT TOP 5 *
FROM Employees
ORDER BY salary DESC;
```

---

## Performance Tip

Sorting large datasets can be expensive.

Adding indexes on frequently sorted columns can improve performance.

Example:

```sql
CREATE INDEX idx_salary
ON Employees(salary);
```

---

## Common Mistakes

### Forgetting DESC

```sql
SELECT *
FROM Employees
ORDER BY salary;
```

This sorts in ascending order, not descending.

---

### Sorting by Unnecessary Columns

```sql
SELECT *
FROM Employees
ORDER BY employee_name;
```

When only salary ranking is needed:

```sql
SELECT employee_name,
       salary
FROM Employees
ORDER BY salary DESC;
```

---

## Key Takeaways

* `ORDER BY` is used to sort data.
* `ASC` = Ascending order.
* `DESC` = Descending order.
* Multiple columns can be used for sorting.
* Frequently used in reports, dashboards, and APIs.
* Indexes can improve sorting performance.

---
