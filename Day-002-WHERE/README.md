# Day 2 - WHERE Clause

## Topic

**Filtering Data Using WHERE**

---

## Why Do We Need WHERE?

Without `WHERE`, SQL returns all rows.

With `WHERE`, we can retrieve only the records we need.

Examples:

* Active users
* Orders above ₹1000
* Employees from the IT department
* Customers from a specific city

---

## SQL Query

### Find Employees with Salary Greater Than 50,000

```sql
SELECT *
FROM Employees
WHERE salary > 50000;
```

### Find Employees from IT Department

```sql
SELECT *
FROM Employees
WHERE department = 'IT';
```

### Multiple Conditions Using AND

```sql
SELECT *
FROM Employees
WHERE department = 'IT'
  AND salary >= 50000;
```

### Multiple Conditions Using OR

```sql
SELECT *
FROM Employees
WHERE department = 'IT'
   OR department = 'HR';
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

## Output

```text
employee_id | employee_name | department | salary
-------------------------------------------------
3           | Ravi          | IT         | 60000
4           | Neha          | Finance    | 55000
```

---

## Real-World Backend Example

Suppose you're building a login system.

Find an active user:

```sql
SELECT *
FROM users
WHERE email = 'user@example.com'
  AND status = 'ACTIVE';
```

This type of query is commonly used in PHP, Laravel, CodeIgniter, Node.js, Java, and .NET applications.

---

# Interview Questions

## Q1. What is the purpose of the WHERE clause?

### Answer

The `WHERE` clause filters records based on a specified condition.

Example:

```sql
SELECT *
FROM Employees
WHERE salary > 50000;
```

---

## Q2. What operators can be used with WHERE?

Common operators:

```text
=
!=
>
<
>=
<=
BETWEEN
IN
LIKE
IS NULL
```

---

## Q3. What is the difference between WHERE and HAVING?

| WHERE                                   | HAVING                      |
| --------------------------------------- | --------------------------- |
| Filters rows                            | Filters groups              |
| Executes before GROUP BY                | Executes after GROUP BY     |
| Cannot directly use aggregate functions | Can use aggregate functions |

Example:

```sql
SELECT department,
       COUNT(*)
FROM Employees
GROUP BY department
HAVING COUNT(*) > 5;
```

---

## Q4. What is the difference between IN and OR?

### Using OR

```sql
SELECT *
FROM Employees
WHERE department = 'IT'
   OR department = 'HR';
```

### Using IN

```sql
SELECT *
FROM Employees
WHERE department IN ('IT', 'HR');
```

`IN` is cleaner and easier to read when checking multiple values.

---

## Q5. How do you check NULL values?

### Incorrect

```sql
SELECT *
FROM Employees
WHERE manager_id = NULL;
```

### Correct

```sql
SELECT *
FROM Employees
WHERE manager_id IS NULL;
```

This is one of the most frequently asked SQL interview questions.

---

## Q6. Which executes first: SELECT or WHERE?

Consider:

```sql
SELECT employee_name
FROM Employees
WHERE salary > 50000;
```

Logical execution order:

```text
FROM
WHERE
SELECT
```

SQL first identifies the table, filters rows, and then returns selected columns.

---

## Q7. What is the difference between = and LIKE?

### Using =

```sql
SELECT *
FROM Employees
WHERE employee_name = 'Praveen';
```

### Using LIKE

```sql
SELECT *
FROM Employees
WHERE employee_name LIKE 'Pra%';
```

`LIKE` is used for pattern matching.

---

## Common Interview Scenario

### Question

Find employees whose salary is between 40,000 and 60,000.

### Answer

```sql
SELECT *
FROM Employees
WHERE salary BETWEEN 40000 AND 60000;
```

---

## Performance Tip

Instead of:

```sql
SELECT *
FROM Employees
WHERE department = 'IT';
```

Use:

```sql
SELECT employee_id,
       employee_name
FROM Employees
WHERE department = 'IT';
```

Fetching only the required columns improves query performance and reduces memory usage.

---

## Key Takeaways

* Use `WHERE` to filter records.
* Combine conditions using `AND` and `OR`.
* Use `IN` for multiple values.
* Use `LIKE` for pattern matching.
* Use `IS NULL` to check NULL values.
* Avoid `SELECT *` in production systems.
* Understand the difference between `WHERE` and `HAVING`.

---

#100DaysOfSQL #SQL #MySQL #PostgreSQL #Database #BackendDeveloper #PHPDeveloper #DataAnalyst #SoftwareEngineer #LearningInPublic #InterviewPreparation
