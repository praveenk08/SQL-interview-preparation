# Day 5 - DISTINCT Clause

## Topic

**Removing Duplicate Records Using DISTINCT**

---

## Why Do We Need DISTINCT?

In real-world databases, duplicate values are common.

Examples:

* Multiple employees from the same department
* Multiple customers from the same city
* Repeated product categories
* Duplicate status values

The `DISTINCT` keyword returns only unique values.

---

## SQL Query

### Get Unique Departments

```sql id="u4xnhs"
SELECT DISTINCT department
FROM Employees;
```

### Get Unique Cities

```sql id="y7q1pj"
SELECT DISTINCT city
FROM Customers;
```

### DISTINCT on Multiple Columns

```sql id="1y2h1t"
SELECT DISTINCT department,
                city
FROM Employees;
```

---

## Sample Table

| employee_id | employee_name | department |
| ----------- | ------------- | ---------- |
| 1           | Praveen       | IT         |
| 2           | Amit          | HR         |
| 3           | Ravi          | IT         |
| 4           | Neha          | Finance    |
| 5           | Rahul         | HR         |

---

## Output

```text id="w7ccg5"
department
----------
IT
HR
Finance
```

---

## Real-World Backend Example

Find all unique user roles:

```sql id="5g2c8s"
SELECT DISTINCT role
FROM users;
```

Get available product categories:

```sql id="v4h3y8"
SELECT DISTINCT category
FROM products;
```

Commonly used in:

* Filter dropdowns
* Reports
* Search systems
* Analytics dashboards

---

# Interview Questions

## Q1. What is DISTINCT in SQL?

### Answer

`DISTINCT` removes duplicate values and returns only unique records.

Example:

```sql id="1e1c3v"
SELECT DISTINCT department
FROM Employees;
```

---

## Q2. Does DISTINCT remove duplicate rows or duplicate values?

### Answer

It removes duplicate results from the selected columns.

Example:

```sql id="h4xj5k"
SELECT DISTINCT department
FROM Employees;
```

Returns each department only once.

---

## Q3. Can DISTINCT be used with multiple columns?

### Answer

Yes.

```sql id="m1y2s8"
SELECT DISTINCT department,
                city
FROM Employees;
```

Uniqueness is checked on the combination of both columns.

---

## Q4. What is the difference between DISTINCT and GROUP BY?

### DISTINCT

```sql id="z7v2t4"
SELECT DISTINCT department
FROM Employees;
```

### GROUP BY

```sql id="v3u8e2"
SELECT department
FROM Employees
GROUP BY department;
```

Both may produce similar results, but `GROUP BY` is mainly used with aggregate functions.

---

## Q5. Can DISTINCT be used with COUNT?

### Answer

Yes.

Count unique departments:

```sql id="f8p3q1"
SELECT COUNT(DISTINCT department)
FROM Employees;
```

Very common interview question.

---

## Q6. What is the difference between COUNT(*) and COUNT(DISTINCT)?

### COUNT(*)

```sql id="n4k2r9"
SELECT COUNT(*)
FROM Employees;
```

Counts all rows.

### COUNT(DISTINCT department)

```sql id="q6d5m8"
SELECT COUNT(DISTINCT department)
FROM Employees;
```

Counts only unique departments.

---

## Q7. Is DISTINCT expensive on large datasets?

### Answer

Yes.

When applied to large datasets, SQL may need additional sorting or hashing operations.

Performance can often be improved using indexes.

---

## Common Interview Scenario

### Question

How would you find the number of unique cities where customers live?

### Answer

```sql id="t8m2j5"
SELECT COUNT(DISTINCT city)
FROM Customers;
```

---

## Real-World Scenario

Populate a department dropdown in an HR system:

```sql id="p4e8x2"
SELECT DISTINCT department
FROM Employees
ORDER BY department;
```

This prevents duplicate department names from appearing.

---

## Performance Tip

Avoid:

```sql id="r5v8c1"
SELECT DISTINCT *
FROM Employees;
```

This can be expensive because SQL must compare all columns.

Prefer:

```sql id="a3n6k7"
SELECT DISTINCT department
FROM Employees;
```

Only retrieve the columns you need.

---

## Common Mistakes

### Using DISTINCT Unnecessarily

```sql id="s2m7q4"
SELECT DISTINCT employee_id
FROM Employees;
```

If `employee_id` is already unique, `DISTINCT` adds unnecessary overhead.

---

### Confusing DISTINCT with GROUP BY

`DISTINCT` removes duplicates.

`GROUP BY` groups records for aggregation.

---

## Key Takeaways

* `DISTINCT` returns unique values.
* Works on one or multiple columns.
* Frequently used in reports and dropdown filters.
* Can be combined with `COUNT`.
* Large datasets may require additional processing.
* Avoid using `DISTINCT *` unless necessary.

---