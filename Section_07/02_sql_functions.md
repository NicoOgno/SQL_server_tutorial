# $${\color{orange}SQL\space Functions}$$

### MAX

In SQL, the `MAX()` function is an aggregate function used to retrieve the maximum value from a specific column within a table. It returns the highest value of the selected column.

    SELECT MAX(column_name) AS max_value
    FROM table_name;

- **column_name:** The column from which you want to find the maximum value.
- **table_name:** The table containing the specified column.

For example, if you have a table named sales and you want to find the maximum value of the amount column:

    SELECT MAX(amount) AS max_amount
    FROM sales;

This query will retrieve the maximum value present in the amount column of the sales table and label the result as `max_amount`.

You can also use `MAX()` function in combination with other clauses like `WHERE` to find the maximum value based on certain conditions:

    SELECT MAX(salary) AS highest_salary
    FROM employees
    WHERE department_id = 3;

This query retrieves the highest salary (`MAX(salary)`) from the `employees` table where the `department_id` is equal to 3.

<br>

### MIN

In SQL, the `MIN()` function is an aggregate function used to retrieve the minimum value from a specific column within a table. It returns the lowest value of the selected column.

    SELECT MIN(column_name) AS min_value
    FROM table_name;

- **column_name:** The column from which you want to find the minimum value.
- **table_name:** The table containing the specified column.

For example, if you have a table named `products` and you want to find the minimum value of the `price` column:

    SELECT MIN(price) AS min_price
    FROM products;

This query will retrieve the minimum value present in the `price` column of the `products` table and label the result as `min_price`.

Similarly to `MAX()`, you can use `MIN()` function in combination with other clauses like `WHERE` to find the minimum value based on certain conditions:

    SELECT MIN(age) AS youngest_employee_age
    FROM employees
    WHERE department_id = 5;

This query retrieves the minimum age (`MIN(age)`) from the `employees` table where the `department_id` is equal to 5, representing the youngest employee in that department.

<br>

### SUM

In SQL, the `SUM()` function is an aggregate function used to calculate the sum of values in a specific column. It adds up all the values within the column and returns the total.

    SELECT SUM(column_name) AS total_sum
    FROM table_name;

- **column_name:** The column containing the values you want to sum.
- **table_name:** The table containing the specified column.

For example, if you have a table named `orders` and you want to find the total sum of the `amount` column:

    SELECT SUM(amount) AS total_amount
    FROM orders;

This query will calculate the sum of all values in the `amount` column of the `orders` table and label the result as `total_amount`.

Additionally, you can use `SUM()` function in combination with other clauses like `WHERE` to find the sum based on specific conditions:

    SELECT SUM(salary) AS total_salary
    FROM employees
    WHERE department_id = 3;

This query retrieves the total sum of salaries (`SUM(salary)`) from the `employees` table where the `department_id` is equal to 3, representing the total salary expense for that department.

<br>

> [!WARNING]
> 👁️
> The `SUM()` function in SQL operates on individual `rows` within the specified `column`, *performing its calculation separately for each row*. If you wish `to execute an action that applies once`, it's necessary to `place it outside the context of the SUM()` function. Example a table with 3 records:
>
>     SELECT SUM(0) + 20 AS TotalAmount FROM Payment --> TotalAmount: 20; 
>     SELECT SUM(20) AS TotalAmount FROM Payment --> TotalAmount: 60;

<br>

### AVG

In SQL, the `AVG()` function is an aggregate function used to *calculate the average (mean) value of a specific column in a table*. It computes the arithmetic mean of the values in the specified column.

    SELECT AVG(column_name) AS average_value
    FROM table_name;

- **column_name:** The column for which you want to calculate the average value.
- **table_name:** The table containing the specified column.

For instance, if you have a table named scores and you want to find the average score from the points column:

    SELECT AVG(points) AS average_score
    FROM scores;

This query will calculate the average value from the `points` column of the `scores` table and label the result as `average_score`.

You can also utilize the `AVG()` function with additional clauses like `WHERE` to calculate the average based on certain conditions:

    SELECT AVG(salary) AS average_salary
    FROM employees
    WHERE department_id = 5;

This query calculates the average salary (`AVG(salary)`) from the employees table where the `department_id` is equal to 5, representing the average salary for employees in that department.

> [!WARNING]
> 👁️
> AVG() behaves similar to SUM()

<br>

### COUNT

In SQL, the `COUNT()` function is an aggregate function used to count the number of rows or non-null values in a specified column or the entire table.

    SELECT COUNT(column_name) AS count_value
    FROM table_name;

- **column_name:** The column you want to count the occurrences of. If you want to count all rows, you can use `COUNT(*)`.
- **table_name:** The table containing the specified column.

For example, to count the number of records in a table named `customers`:

    SELECT COUNT(*) AS total_records
    FROM customers;

This query will count all the rows in the `customers` table and label the result as `total_records`.

Additionally, you can use `COUNT()` with specific columns to count the occurrences of `non-null` values in that column:

    SELECT COUNT(email) AS total_emails
    FROM customers;

This query will count the number of `non-null` values in the `email` column of the `customers` table and label the result as `total_emails`.

Furthermore, `COUNT()` can be used with conditions in conjunction with other clauses like `WHERE` to count rows based on certain criteria:

    SELECT COUNT(*) AS active_customers
    FROM customers
    WHERE status = 'active';

This query will count the number of records in the `customers` table where the status column is set to `'active'`, representing the count of active customers.