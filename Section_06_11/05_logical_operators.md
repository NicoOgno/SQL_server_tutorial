# $${\color{orange}Logical\space Operators}$$

### AND

 In SQL, the `AND` operator is used to *combine multiple conditions in a query's `WHERE` clause to filter the rows returned by a `SELECT` statement*. When using the `AND` operator, all conditions must be true for a row to be included in the result set.

    SELECT column1, column2, ...
    FROM table_name
    WHERE condition1 AND condition2 AND ...;

- **column1, column2, ...:** Columns you want to retrieve data from.
- **table_name:** The table from which data is being retrieved.
- **condition1, condition2, ...:** Conditions that must all be true for a row to be included in the result set.

For example, if you want to retrieve employees from the employees table who work in the 'Sales' department and have a salary greater than 50000:

    SELECT *
    FROM employees
    WHERE department = 'Sales' AND salary > 50000;

This query uses the `AND` operator to combine two conditions: `department = 'Sales'` and `salary > 50000`. Only rows that meet both of these conditions will be included in the result set.

The `AND` operator requires that all specified conditions in the `WHERE` clause must evaluate to `TRUE` for a row to be selected. If any of the conditions evaluate to `FALSE`, the row will be excluded from the result set.

<br>

### OR

In SQL, the `OR` operator is a logical operator used to *combine multiple conditions within a `WHERE` clause* to retrieve rows that satisfy at least one of those conditions.

    SELECT column1, column2, ...
    FROM table_name
    WHERE condition1 OR condition2 OR ...;

- **column1, column2, ...:** Columns you want to retrieve data from.
- **table_name:** The table from which data is being retrieved.
- **condition1, condition2, ...:** Conditions where at least one must be true for a row to be included in the result set.

For example, if you want to retrieve `employees` from the `employees` table who work in either the `'Sales'` department or have a salary greater than 50000:

    SELECT *
    FROM employees
    WHERE department = 'Sales' OR salary > 50000;

This query uses the `OR` operator to combine two conditions: `department = 'Sales'` and `salary > 50000`. Rows that meet either of these conditions will be included in the result set.

The `OR` operator retrieves rows where at least one of the specified conditions in the `WHERE` clause evaluates to `TRUE`. If any of the conditions are `TRUE`, the row will be included in the result set.

<br>

### IN

In SQL, the `IN` operator is used in a `WHERE` clause to specify multiple values for a column and is used to determine if a value matches any value in a specified list.

    SELECT column1, column2, ...
    FROM table_name
    WHERE column_name IN (value1, value2, ...);

- **column1, column2, ...:** Columns you want to retrieve data from.
- **table_name:** The table from which data is being retrieved.
- **column_name:** The column being checked for matching values.
- **value1, value2, ...:** List of values to check against in the specified column.

For instance, if you want to retrieve `employees` from the `employees` table who belong to either the `'Sales'` or `'Marketing'` departments:

    SELECT *
    FROM employees
    WHERE department IN ('Sales', 'Marketing');

This query uses the `IN` operator to check if the `department` column's value matches either `'Sales'` or `'Marketing'`. Rows where the department is `'Sales'` or *'Marketing'* will be included in the result set.

The `IN` operator is particularly useful when you want to match values from a column against a list of specified values rather than using multiple `OR` conditions. *It simplifies the query and makes it more readable, especially when dealing with multiple values*.

<br>

### LIKE

In SQL, the `LIKE` operator is used in a `WHERE` clause to search for a specified pattern within a column.

The `LIKE` operator allows you to use **`wildcard characters`** to match patterns in string data. *The two primary wildcard characters used with LIKE are*:

- **% (percent sign):** Matches any sequence of zero or more characters.
- **_ (underscore):** Matches any single character.

    SELECT column1, column2, ...
    FROM table_name
    WHERE column_name LIKE pattern;

- **column1, column2, ...:** Columns you want to retrieve data from.
- **table_name:** The table from which data is being retrieved.
- **column_name:** The column being checked for the specified pattern.
- **pattern:** The pattern to match against using `LIKE`.

For example, if you want to retrieve all employees whose names start with the letter 'J':

    SELECT *
    FROM employees
    WHERE employee_name LIKE 'J%';

This query uses `LIKE` with the pattern `'J%'`, where the `% wildcard` means *"any sequence of zero or more characters."* It retrieves rows where the `employee_name` starts with `'J'` followed by any sequence of characters.

Another example is if you want to find employees whose names have `'ohn'` as a part of their name:

    SELECT *
    FROM employees
    WHERE employee_name LIKE '%ohn%';

In this case,` %ohn%` matches any sequence of characters that contain `'ohn'` anywhere within the `employee_name`.

> [!TIP]
> 🧠
> The `LIKE` operator is *particularly useful for pattern matching and searching for specific text patterns within string columns* in SQL databases. And it's not case sensitive.

<br>

### NOT

In SQL, the `NOT` operator is used to negate a condition specified within a `WHERE` clause. It reverses the result of a logical condition.

> [!TIP]
> 🧠
> The `NOT` operator can be used with various other operators such as `LIKE`, `IN`, `BETWEEN`, `IS NULL`, etc., to negate their effects.

    SELECT column1, column2, ...
    FROM table_name
    WHERE NOT condition;

- **column1, column2, ...:** Columns you want to retrieve data from.
- **table_name:** The table from which data is being retrieved.
- **condition:** The condition that needs to be negated.

For instance, if you want to retrieve all employees except those who work in the `'Sales'` department:

    SELECT *
    FROM employees
    WHERE NOT department = 'Sales';

This query uses `NOT` with the condition `department = 'Sales'`, which selects all rows where the department is anything other than `'Sales'`. It negates the condition, including employees from departments other than `'Sales'`.

Another example is using `NOT` with the `LIKE` operator. For instance, if you want to retrieve employees whose names do not start with the letter `'J'`:

    SELECT *
    FROM employees
    WHERE NOT employee_name LIKE 'J%';

In this case, `NOT` negates the condition specified with `LIKE`, retrieving rows where the `employee_name` does not start with `'J'`.

> [!TIP]
> 🧠
> The `NOT` operator in SQL is handy for negating specific conditions, allowing you to retrieve data that doesn't match a particular criterion or condition.

<br>

### BETWEEN

In SQL, the `BETWEEN` operator is used in a `WHERE` clause to filter the result set for values within a specified range.

    SELECT column1, column2, ...
    FROM table_name
    WHERE column_name BETWEEN value1 AND value2;

- **column1, column2, ...:** Columns you want to retrieve data from.
- **table_name:** The table from which data is being retrieved.
- **column_name:** The column being checked for values within the specified range.
- **value1, value2:** The range of values. The `BETWEEN` operator is inclusive of these values.

For example, if you want to retrieve orders from the `orders` table where the order date falls within a specific range, let's say between `'2023-01-01' and '2023-12-31'`:

    SELECT *
    FROM orders
    WHERE order_date BETWEEN '2023-01-01' AND '2023-12-31';

This query uses the `BETWEEN` operator to select rows where the `order_date` column falls within the specified range, inclusive of the dates `'2023-01-01' and '2023-12-31'`.

> [!NOTE]
> 📝
> With the `BETWEEN` operator, **both endpoints are inclusive**, meaning the range includes values that are equal to value1 and value2. *If you want to exclude either endpoint, you might need to adjust the conditions accordingly*.

<br>

### Combining Operators

In SQL, you can *combine multiple operators*, such as `AND`, `OR`, `NOT`, `LIKE`, `BETWEEN`, etc., within a `WHERE` clause to create more complex conditions for filtering data.

    SELECT *
    FROM employees
    WHERE department = 'Sales'
      AND (salary > 50000 OR experience_years >= 5)
      AND NOT (age < 30 AND location = 'New York');

- **department = 'Sales':** Retrieves employees from the `'Sales'` department.
- **(salary > 50000 OR experience_years >= 5):** Selects employees who either have a salary greater than 50000 or have an experience of 5 years or more.
- **NOT (age < 30 AND location = 'New York'):** Excludes employees who are younger than 30 and located in New York.

> [!NOTE]
> 📝
> The parentheses `( )` are used to define the precedence of operations and help in grouping conditions together to ensure the query behaves as intended.

> [!TIP]
> 🧠
> Use **`PRINT`** for depuration purposes.