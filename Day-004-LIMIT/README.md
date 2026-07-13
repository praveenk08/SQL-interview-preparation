# Day 4 - LIMIT Clause

## Topic

**Restricting the Number of Rows Returned**

---

## Why Do We Need LIMIT?

In real-world applications, tables can contain millions of records.

Fetching all rows is inefficient and can slow down applications.

The `LIMIT` clause helps retrieve only the required number of rows.

Examples:

* Top 10 products
* Latest 5 orders
* First page of search results
* Dashboard widgets

---

## SQL Query

### Retrieve First 5 Records

```sql
SELECT *
FROM Employees
LIMIT 5;
```

### Retrieve Top 3 Highest Paid Employees

```sql
SELECT *
FROM Employees
ORDER BY salary DESC
LIMIT 3;
```

### Retrieve Top 10 Latest Orders

```sql
SELECT *
FROM Orders
ORDER BY created_at DESC
LIMIT 10;
```

---

## Sample Table

| employee_id | employee_name | salary |
| ----------- | ------------- | ------ |
| 1           | Praveen       | 50000  |
| 2           | Amit          | 45000  |
| 3           | Ravi          | 60000  |
| 4           | Neha          | 55000  |
| 5           | Ankit         | 70000  |

---

## Output

```text
employee_id | employee_name | salary
------------------------------------
5           | Ankit         | 70000
3           | Ravi          | 60000
4           | Neha          | 55000
```

---

## Real-World Backend Example

Display the latest blog posts:

```sql
SELECT *
FROM posts
ORDER BY created_at DESC
LIMIT 10;
```

Show recent user registrations:

```sql
SELECT *
FROM users
ORDER BY id DESC
LIMIT 20;
```

Used extensively in:

* PHP applications
* Laravel projects
* CodeIgniter projects
* Node.js APIs
* Admin dashboards

---

# Interview Questions

## Q1. What is the purpose of LIMIT?

### Answer

`LIMIT` restricts the number of rows returned by a query.

Example:

```sql
SELECT *
FROM Employees
LIMIT 5;
```

Returns only 5 rows.

---

## Q2. Why is LIMIT important?

### Answer

Benefits:

* Faster query execution
* Reduced memory usage
* Better user experience
* Efficient pagination

---

## Q3. How do you get the top 5 highest-paid employees?

### Answer

```sql
SELECT *
FROM Employees
ORDER BY salary DESC
LIMIT 5;
```

Very common SQL interview question.

---

## Q4. What is the difference between LIMIT and TOP?

### MySQL/PostgreSQL

```sql
SELECT *
FROM Employees
LIMIT 5;
```

### SQL Server

```sql
SELECT TOP 5 *
FROM Employees;
```

---

## Q5. Does LIMIT work without ORDER BY?

### Answer

Yes, but results may not be predictable.

```sql
SELECT *
FROM Employees
LIMIT 5;
```

Recommended:

```sql
SELECT *
FROM Employees
ORDER BY employee_id
LIMIT 5;
```

---

## Q6. Which executes first: ORDER BY or LIMIT?

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

`LIMIT` executes after sorting.

---

## Q7. What is pagination?

### Answer

Pagination means dividing records into pages.

Example:

```sql
SELECT *
FROM Employees
LIMIT 10 OFFSET 0;
```

First page.

```sql
SELECT *
FROM Employees
LIMIT 10 OFFSET 10;
```

Second page.

---

## Common Interview Scenario

### Question

Retrieve the latest 10 users registered on the platform.

### Answer

```sql
SELECT *
FROM users
ORDER BY created_at DESC
LIMIT 10;
```

---

## Performance Tip

Avoid:

```sql
SELECT *
FROM Employees;
```

When you only need a few records:

```sql
SELECT employee_name,
       salary
FROM Employees
ORDER BY salary DESC
LIMIT 10;
```

This reduces memory consumption and network traffic.

---

## Common Mistakes

### Using LIMIT Without ORDER BY

```sql
SELECT *
FROM Employees
LIMIT 5;
```

Result order is not guaranteed.

Better:

```sql
SELECT *
FROM Employees
ORDER BY employee_id
LIMIT 5;
```

---

### Fetching Too Many Records

```sql
SELECT *
FROM Employees
LIMIT 100000;
```

Large limits can negatively impact performance.

---

## Key Takeaways

* `LIMIT` restricts the number of returned rows.
* Frequently used with `ORDER BY`.
* Essential for pagination.
* Improves performance.
* Used heavily in APIs and dashboards.
* SQL Server uses `TOP` instead of `LIMIT`.

---

