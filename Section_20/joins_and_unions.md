# $${\color{orange}Joins\space and\space Unions}$$

![joins_unions](/images/joins_unions.png)

### INNER JOIN

`INNER JOIN` is used to combine `rows` from two or more `tables` *based on a related column between them*. The result set includes only the rows that have matching values in the specified columns.

    SELECT 
        column1, column2, ...
    FROM 
        table1
    INNER JOIN 
        table2 ON table2.column_name = table1.column_name;

- **SELECT:** Specifies the columns you want to retrieve from the tables.
- **FROM:** Specifies the first table in the join.
- **INNER JOIN:** Specifies that you want to perform an inner join.
- **table2:** Specifies the second table in the join.
- **ON:** Specifies the condition for the join, i.e., the columns from both tables that should be matched.

<br>

Example:

    SELECT 
        Customers.CustomerID,
        Customers.CustomerName,
        Orders.OrderID,
        Orders.OrderDate
    FROM 
        Customers
    INNER JOIN 
        Orders ON Orders.CustomerID = Customers.CustomerID;

In this example, the `INNER JOIN` is based on the `CustomerID column`. The query selects the `CustomerID` and `CustomerName` from the `Customers table` and the `OrderID` and `OrderDate` from the `Orders table` for customers who have placed orders.

<br><br>

### LEFT JOIN

`LEFT JOIN` (or `LEFT OUTER JOIN`) is used to retrieve all records from the left `table` (the `table` mentioned before the `LEFT JOIN keyword`) and the matched records from the right `table` (the table mentioned after the `LEFT JOIN keyword`). *If there is no match, `NULL` values are returned for columns from the right `table`*.

    SELECT 
        column1, column2, ...
    FROM 
        table1
    LEFT JOIN 
        table2 ON table1.column_name = table2.column_name;

- **SELECT:** Specifies the columns you want to retrieve from the tables.
- **FROM:** Specifies the *first `table` in the join*.
- **LEFT JOIN (or LEFT OUTER JOIN):** Specifies that you want to perform a `left join`.
- **table2:** Specifies the *second `table` in the join*.
- **ON:** *Specifies the condition for the join*, i.e., the columns from both tables that should be matched.

<br>

Example:

Two `tables`, `Employees` and `Departments`, and you want to retrieve a list of all `employees` along with their `department` information. The common column between these tables is `DepartmentID`.

    SELECT 
        Employees.EmployeeID,
        Employees.EmployeeName,
        Departments.DepartmentName
    FROM 
        Employees
    LEFT JOIN 
        Departments ON Employees.DepartmentID = Departments.DepartmentID;

<br>

In this example, the `LEFT JOIN` is based on the `DepartmentID column`. The query selects the `EmployeeID` and `EmployeeName` from the `Employees table` and the `DepartmentName` from the `Departments table`. If an employee is not associated with any department (no match in the `Departments table`), `NULL` values will be returned for the `DepartmentName column`.

<br><br>

### RIGHT JOIN

`RIGHT JOIN` *is used to retrieve all records from the right table* (the second table mentioned in the `FROM clause`) *and the matched records from the left table* (the first table mentioned) based on the specified condition. *If there is no match, `NULL` values are returned for columns from the left table*.

    SELECT 
        column1, column2, ...
    FROM 
        table1
    RIGHT JOIN 
        table2 ON table1.column_name = table2.column_name;

- **SELECT:** Specifies the `columns` you want to retrieve from the `tables`.
- **FROM:** Specifies the *first `table` in the join*.
- **RIGHT JOIN:** Specifies that you want to perform a right join.
- **table2:** Specifies the *second `table` in the join*.
- **ON:** *Specifies the condition for the join*, i.e., the columns from both tables that should be matched.

<br>

Example: `tables Customers and Orders`

    SELECT 
        Customers.CustomerID,
        Customers.CustomerName,
        Orders.OrderID,
        Orders.OrderDate
    FROM 
        Customers
    RIGHT JOIN 
        Orders ON Customers.CustomerID = Orders.CustomerID;

`RIGHT JOIN` is based on the `CustomerID column`. The query selects the `CustomerID` and `CustomerName` from the `Customers table` and the `OrderID` and `OrderDate` from the `Orders table`. If a customer has placed an order, the information is included in the result set. *If there is an order without a corresponding customer, the `columns` from the `Customers table` will contain `NULL` values*.

<br>

> [!NOTE]
> 📝
> Many SQL developers prefer to use `LEFT JOIN` as it is more commonly used and can be more intuitive to read.

<br>

> [!IMPORTANT]
> 🚩
> In an **`INNER JOIN`**, in the `ON clause` you must use a `Primary Key` as condition, that will improve the perfomance of the `query`. Also the first `PK` to compare should be the one from the table right after the `INNER JOIN Keyword` (this **don't** apply for `RIGHT or LEFT JOIN`) this will also improve the performance on the `query`. And use `Aliases` to improve readibility.

Example:

    SELECT * FROM Customers C
    INNER JOIN Orders O
    ON O.CustomerID = C.CustomerID;

<br><br>

### UNION and UNION ALL

`UNION` and `UNION ALL` are used to combine the results of two or more `SELECT statements`. Both are used to merge the results from different queries into a single result set.

<br>

> [!IMPORTANT]
> 🚩
> Each `SELECT statement` within the `UNION` must have the same number of `columns` in the result sets with similar `data types`.

<br>

**UNION**

- *`UNION` operator is used to combine the results of two or more `SELECT statements` while eliminating duplicate rows*.

- Each `SELECT statement` within the `UNION` must have the same number of `columns` in the result sets with similar `data types`.

- The result set of a `UNION` will not include duplicate rows; *if a row exists in multiple `SELECT statements`, it will appear only once in the final result set*.

*Syntax:*

    SELECT column1, column2, ...
    FROM table1
    UNION
    SELECT column1, column2, ...
    FROM table2;

<br>

**UNION ALL**

- `UNION ALL` operator, like `UNION`, is used to combine the results of two or more `SELECT statements`, *but it includes all rows from all `SELECT statements`, even if they are duplicates*.

- Unlike `UNION`, `UNION ALL` does not eliminate duplicate rows from the result set. It simply concatenates the results.

*Syntax:*

    SELECT column1, column2, ...
    FROM table1
    UNION ALL
    SELECT column1, column2, ...
    FROM table2;

<br>

Here's a simple example to illustrate the difference:

    -- Using UNION to eliminate duplicates
    SELECT EmployeeID FROM Employees
    UNION
    SELECT EmployeeID FROM FormerEmployees;

    -- Using UNION ALL to include all rows, even duplicates
    SELECT EmployeeID FROM Employees
    UNION ALL
    SELECT EmployeeID FROM FormerEmployees;

In the first query with `UNION`, if an `EmployeeID` exists in both the `Employees` and `FormerEmployees tables`, it will only appear once in the result set. In the second query with `UNION ALL`, all rows from both tables are included, even if there are duplicates.

<br>

> [!NOTE]
> 📝
> Keep in mind that `UNION` may have a slight performance overhead as it needs to perform additional processing to eliminate duplicates.

<br>

> [!IMPORTANT]
> 🚩
> If you use more than one `JOIN` in a `batch` be sure to respect the order declaration of `Aliases`.