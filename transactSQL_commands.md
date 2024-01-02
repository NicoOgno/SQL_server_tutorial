# $${\color{orange}SQL\space Clauses ✨}$$


🔸 **clauses in SQL** are specific components of a SQL statement used to define, filter, or manipulate sets of data in a database. These clauses allow specific operations and are essential for creating and manipulating queries in a relational database.

### Some of the most common clauses in SQL include:

1. **SELECT:** Used to select specific columns from a table or view.

2. **FROM:** Indicates the table or tables from which data is being selected.

3. **WHERE:** Allows setting conditions to filter records that meet certain criteria.

4. **GROUP BY:** Used to group rows based on a specific set of columns.

5. **HAVING:** Similar to WHERE, but applied to resulting groups after using GROUP BY.

6. **ORDER BY:** Used to sort results based on one or more columns.

7. **JOIN:** Allows combining rows from two or more tables based on a related condition.

8. **INNER JOIN**, **LEFT JOIN**, **RIGHT JOIN**, **FULL JOIN:** Variants of JOIN for different types of table combinations.

9. **LIMIT** / **OFFSET** or **FETCH FIRST** / **ROWS:** Limits the number of rows returned by a query.

10. **INSERT INTO:** Adds new records to a table.

11. **UPDATE:** Modifies existing records in a table.

12. **DELETE:** Removes records from a table.

<br>

### TOP

The **TOP** clause in SQL is used in databases such as *SQL Server and Microsoft Access* to limit the number of rows returned by a query. This clause is commonly used in SELECT queries to *specify an upper limit on the number of rows that should be returned as the result of the query*.

    SELECT TOP (n) column1, column2, ...
    FROM table_name;

    SELECT TOP (5) * FROM customers;

<br>

### ORDER BY

The **ORDER BY** clause in SQL is used to sort the result set returned by a query based on one or more columns. It arranges the rows in either ascending (ASC) or descending (DESC) order according to the specified column(s).

    SELECT column1, column2, ...
    FROM table_name
    ORDER BY column1 [ASC|DESC], column2 [ASC|DESC], ...;

- **column1, column2, ...:** Columns used to sort the result set.
- **table_name:** The table from which data is being retrieved.
- **ASC:** Optional keyword used to sort in ascending order (default if not specified).
- **DESC:** Keyword used to sort in descending order.

<br>

      SELECT employee_id, first_name, last_name
      FROM employees
      ORDER BY last_name ASC, first_name ASC;

This query will return the employee IDs, first names, and last names from the "employees" table, *sorted alphabetically by last name (in ascending order) and then by first name (also in ascending order)*.

- Example **TOP** and **ORDER BY:**

      SELECT TOP 3 * FROM Paciente ORDER BY FNacimiento DESC

<br>

### DISTINCT

The **DISTINCT** keyword in SQL is used within the **SELECT** statement to retrieve unique values from a specific column or combination of columns in a table. It eliminates duplicate rows from the result set.

    SELECT DISTINCT column1, column2, ...
    FROM table_name;

- **column1, column2, ...:** Columns from which unique values are retrieved.
- **table_name:** The table from which data is being retrieved.

<br>

    SELECT DISTINCT city
    FROM customers;

This query will return *a list of distinct cities present in the "city" column of the "customers" table, eliminating duplicate city names from the result set*.

<br>

### GROUP BY


The **GROUP BY** clause in SQL is used to group rows that have the same values in one or more columns. It's typically *used in conjunction with aggregate functions like COUNT, SUM, AVG, MAX, or MIN to perform calculations on groups of rows* rather than individual rows.

    SELECT column1, column2, ..., aggregate_function(column)
    FROM table_name
    GROUP BY column1, column2, ...;
  
- **column1, column2, ...:** Columns by which you want to group the data.
- **aggregate_function:** A function such as COUNT, SUM, AVG, MAX, or MIN used to perform calculations on the grouped data.
- **table_name:** The table from which data is being retrieved.

<br>

    SELECT product_id, COUNT(order_id) AS total_orders
    FROM orders
    GROUP BY product_id;

This query will group the rows in the "orders" table by "product_id" and *count the number of orders for each unique product, displaying the product ID alongside the total number of orders placed for that product*.

<br>

### WHERE

The **WHERE** clause in SQL is used to *filter records or rows from a table that satisfy a specified condition*. It allows you to retrieve only the rows that meet the specified criteria.

    SELECT column1, column2, ...
    FROM table_name
    WHERE condition;

- **column1, column2, ...:** Columns you want to retrieve data from.
- **table_name:** The table from which data is being retrieved.
- **condition:** The condition that must be met for a row to be included in the result set.

<br>

    SELECT employee_id, first_name, last_name
    FROM employees
    WHERE department = 'Marketing';

This query will retrieve the "employee_id", "first_name", and "last_name" columns from the "employees" table where the "department" column is equal to 'Marketing'. Only rows that satisfy this condition will be included in the result set.

> [!WARNING]
> 👁️
> When using the WHERE clause in SQL to compare a string, it's essential to `enclose the string within single quotes (' ')` or `double quotes (" ")`. This is particularly important in SQL to *differentiate string values from column names or other SQL elements*. `Dates also must be enclose by quotes`.

<br>

### INSERT INTO

The **INSERT INTO** statement in SQL is used to add new records or rows into a table.

    INSERT INTO table_name (column1, column2, ...)
    VALUES (value1, value2, ...);

- **table_name:** The name of the table where you want to insert data.
- **column1, column2, ...:** The columns in the table where you want to insert values.
- **value1, value2, ...:** The values to be inserted into the respective columns.

<br>

For example, suppose you have a table named 'customers' with columns 'first_name', 'last_name', and 'email', and you want to insert a new record into this table:

    INSERT INTO customers (first_name, last_name, email)
    VALUES ('John', 'Doe', 'john@example.com');

This query will add a new record to the 'customers' table with 'John' as the first name, 'Doe' as the last name, and 'john@example.com' as the email.

You can also insert multiple records at once using a single INSERT INTO statement by providing multiple sets of values separated by commas. For instance:

    INSERT INTO customers (first_name, last_name, email)
    VALUES ('Alice', 'Smith', 'alice@example.com'),
          ('Bob', 'Johnson', 'bob@example.com'),
          ('Emily', 'Brown', 'emily@example.com');