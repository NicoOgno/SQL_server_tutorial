# $${\color{orange}Subqueries}$$

### Subquery

In SQL, a **subquery** (also known as an `inner query` or `nested query`) is a *query nested within another query*. **Subqueries** *are used to retrieve data that will be used as a part of a larger query*.

**There are two primary types of subqueries:**

1. **Single-row subquery:** A subquery that returns only one row of results.
2. **Multi-row subquery:** A subquery that returns multiple rows of results.

<br>

Example of a **single-row** subquery:

    SELECT *
    FROM Employees
    WHERE Salary > (SELECT AVG(Salary) FROM Employees);

In this example, the **subquery** `(SELECT AVG(Salary) FROM Employees)` calculates the average salary from the `Employees` table. The outer query selects employees whose salary is higher than the calculated average.

<br>

Example of a **multi-row** subquery used with the `IN` operator:

    SELECT *
    FROM Orders
    WHERE CustomerID IN (SELECT CustomerID FROM Customers WHERE Country = 'MEXICO');

In this example, the **subquery** `(SELECT CustomerID FROM Customers WHERE Country = 'MEXICO')` retrieves a list of `CustomerIDs` from the `Customers` table where the country is 'MEXICO'. The outer query selects orders from customers located in the MEXICO.

> [!TIP]
> 🧠
> **Subqueries** can be used in various parts of `SQL statements`, including the `SELECT`, `INSERT`, `UPDATE`, and `DELETE statements`. They allow for more complex and conditional querying, where the result of one query is used as a condition or filter in another.

<br>

### Table Alias

In SQL, **table aliases** are used to *assign a temporary name to a table or a subquery in a SQL statement*. **Table aliases** make *queries more readable*, especially when dealing with complex queries involving multiple tables or subqueries.

    SELECT alias.column_name, alias2.column_name
    FROM table_name AS alias
    JOIN another_table AS alias2 ON alias.column = alias2.column;

Example:

    SELECT e.EmployeeID, e.EmployeeName, d.DepartmentName
    FROM Employees AS e
    JOIN Departments AS d ON e.DepartmentID = d.DepartmentID;

In this example, `Employees` table is given the `alias e`, and `Departments` table is given the `alias d`. These aliases (e and d) are used to reference the columns from their respective tables in the `SELECT statement` and the `JOIN condition`.

**Using table aliases:**

- Reduces the amount of typing required in complex queries.
- Helps improve query readability and understandability.
- Allows you to refer to columns in a more concise manner.

> [!TIP]
> 🧠
> When using **table aliases**, it's essential to choose *meaningful and easily understandable aliases* to enhance the readability of your `SQL queries`. However, *make sure that the aliases are unique within the scope of the query to avoid ambiguity*.