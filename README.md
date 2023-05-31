# Oracle Interview Questions And Answers

Most targeted up-to-date Oracle interview questions and answers list

# Table of Contents
1. [What is the difference between `SELECT INTO` and `INSERT INTO` statements in Oracle?](#1-what-is-the-difference-between-select-into-and-insert-into-statements-in-oracle)
2. [Explain the difference between `GROUP BY` and `HAVING` clauses in Oracle.](#2-explain-the-difference-between-group-by-and-having-clauses-in-oracle)
3. [How can you retrieve the top N rows from a table in Oracle?](#3-how-can-you-retrieve-the-top-n-rows-from-a-table-in-oracle)
4. [Explain the difference between `SUBSTR` and `INSTR` functions in Oracle.](#4-explain-the-difference-between-substr-and-instr-functions-in-oracle)
5. [How can you perform a case-insensitive search in Oracle?](#5-how-can-you-perform-a-case-insensitive-search-in-oracle)
6. [Explain the difference between `UNION` and `UNION ALL` operators in Oracle.](#6-explain-the-difference-between-union-and-union-all-operators-in-oracle)
7. [How can you calculate the average, minimum, and maximum values of a column in Oracle?](#7-how-can-you-calculate-the-average-minimum-and-maximum-values-of-a-column-in-oracle)
8. [Explain the difference between a primary key and a unique key in Oracle.](#8-explain-the-difference-between-a-primary-key-and-a-unique-key-in-oracle)
9. [How can you perform a self-join in Oracle?](#9-how-can-you-perform-a-self-join-in-oracle)
10. [Explain the difference between a view and a materialized view in Oracle.](#10-explain-the-difference-between-a-view-and-a-materialized-view-in-oracle)
- [Whats more?](#whats-more)
- [Contributing](#contributing)
- [License](#license)


## 1. What is the difference between SELECT INTO and INSERT INTO statements in Oracle?

SELECT INTO is used to assign the result of a query to variables in PL/SQL, while INSERT INTO is used to insert data into a table.

Example of SELECT INTO:

```sql
DECLARE
  l_employee_name employees.employee_name%TYPE;
BEGIN
  SELECT employee_name INTO l_employee_name FROM employees WHERE employee_id = 123;
  -- Use l_employee_name variable for further processing
END;
```

Example of INSERT INTO:

```sql
INSERT INTO employees (employee_id, employee_name) VALUES (123, 'John Doe');
```

## 2. Explain the difference between GROUP BY and HAVING clauses in Oracle.

GROUP BY is used to group rows based on specific columns, while HAVING is used to filter groups based on specific conditions.

Example of GROUP BY:

```sql
SELECT department_id, COUNT(*) FROM employees GROUP BY department_id;
```

Example of HAVING:

```sql
SELECT department_id, COUNT(*) FROM employees GROUP BY department_id HAVING COUNT(*) > 5;
```

## 3. How can you retrieve the top N rows from a table in Oracle?

You can use the ROWNUM pseudocolumn along with the ORDER BY clause to retrieve the top N rows.

Example:

```sql
SELECT * FROM employees WHERE ROWNUM <= 10 ORDER BY hire_date DESC;
```

## 4. Explain the difference between SUBSTR and INSTR functions in Oracle.

SUBSTR is used to extract a portion of a string, while INSTR is used to find the position of a substring within a string.

Example of SUBSTR:

```sql
SELECT SUBSTR('Hello, World!', 1, 5) FROM dual;
-- Output: "Hello"
```

Example of INSTR:

```sql
SELECT INSTR('Hello, World!', 'World') FROM dual;
-- Output: 8
```

## 5. How can you perform a case-insensitive search in Oracle?

You can use the UPPER or LOWER functions to convert both the search term and the column value to the same case.

Example:

```sql
SELECT * FROM employees WHERE UPPER(last_name) = UPPER('smith');
```

## 6. Explain the difference between UNION and UNION ALL operators in Oracle.

UNION combines the result sets of two or more SELECT statements, removing duplicate rows, while UNION ALL includes all rows, including duplicates.

Example of UNION:

```sql
SELECT employee_id FROM employees UNION SELECT employee_id FROM contractors;
```

Example of UNION ALL:

```sql
SELECT employee_id FROM employees UNION ALL SELECT employee_id FROM contractors;
```

## 7. How can you calculate the average, minimum, and maximum values of a column in Oracle?

You can use the aggregate functions AVG, MIN, and MAX respectively.

Example:

```sql
SELECT AVG(salary), MIN(salary), MAX(salary) FROM employees;
```

## 8. Explain the difference between a primary key and a unique key in Oracle.

- A primary key is used to uniquely identify each row in a table and cannot contain null values. Only one primary key is allowed per table.

- A unique key is used to ensure that each value in a column or a set of columns is unique, but it can contain null values. Multiple unique keys can be defined per table.

Example of a primary key:

```sql
CREATE TABLE employees (
  employee_id NUMBER PRIMARY KEY,
  employee_name VARCHAR2(100)
);
```

Example of a unique key:

```sql
CREATE TABLE departments (
  department_id NUMBER,
  department_name VARCHAR2(100),
  CONSTRAINT uk_department_name UNIQUE (department_name)
);
```

## 9. How can you perform a self-join in Oracle?

A self-join is performed when a table is joined with itself based on a common column.

Example:

```sql
SELECT e1.employee_name, e2.employee_name
FROM employees e1, employees e2
WHERE e1.manager_id = e2.employee_id;
```

## 10. Explain the difference between a view and a materialized view in Oracle.

A view is a virtual table that is based on the result of a SQL query, while a materialized view is a physical copy of the result of a query stored as a table.

Example of a view:

```sql
CREATE VIEW active_employees AS
SELECT * FROM employees WHERE status = 'Active';
```

Example of a materialized view:

```sql
CREATE MATERIALIZED VIEW mv_active_employees
AS SELECT * FROM employees WHERE status = 'Active';
```

## What's more?
<a href="https://interviewplus.ai/database-administration/oracle/questions">A comprehensive list of questions and answers</a>

## Contributing
We welcome contributions from our users to help make this resource as comprehensive and useful as possible. If you have been recently interviewed and encountered a question that is not currently covered on our website, feel free to suggest it as a new question. Your contributions will be added to our platform, and we will make sure to credit you for your contributions. We appreciate your help in making our platform a valuable tool for all job seekers.

## License
MIT License
