# $${\color{orange}Records\space Manipulation\space \space UPDATE\space DELETE 📛}$$

### UPDATE

The **UPDATE** statement in SQL is used to *modify or update existing records* in a table.

    UPDATE table_name
    SET column1 = value1, column2 = value2, ...
    WHERE condition;

- **table_name:** The name of the table you want to update.
- **column1, column2, ...:** The columns that you want to modify.
- **value1, value2, ...:** The new values that you want to assign to the specified columns.
- **condition:** Specifies the condition that must be met for the update to occur. If omitted, all rows in the table will be updated.

<br>

For example, let's say you want to update the 'salary' column of an 'employees' table for a specific employee (e.g., employee_id = 123) to a new salary value (e.g., 50000):

    UPDATE employees
    SET salary = 50000
    WHERE employee_id = 123;

This query will update the 'salary' column of the 'employees' table, setting it to 50000, but only for the employee with an 'employee_id' of 123.

> [!IMPORTANT]
> 🚩
> Please use caution when executing *UPDATE statements as they can modify data irreversibly*. Always ensure you have a `backup and double-check your conditions before running such statements, especially in a production environment`.

<br>

### DELETE

The **DELETE** statement in SQL is used to *remove records or rows from a table based on specified conditions*.

    DELETE FROM table_name
    WHERE condition;

- **table_name:** The name of the table from which you want to delete records.
- **condition:** Specifies the condition that must be met for the deletion to occur. If omitted, all rows in the table will be deleted.

<br>

For instance, if you want to delete a specific record from an 'employees' table where the 'employee_id' is 123:

    DELETE FROM employees
    WHERE employee_id = 123;

> [!IMPORTANT]
> 🚩
> Please exercise caution when `using DELETE statements as they permanently remove data from your database`. Ensure your conditions are accurate before executing such statements, *especially in a production environment, and consider performing backups* before making significant changes to your data.

<br>

### DELETE and Foreign Key

When using the **DELETE** `statement in SQL for a table that has a foreign key constraint`, the deletion might be restricted by the foreign key relationship.

If a `foreign key constraint` exists on a table referencing another table, deleting records from the `referenced table might cause an error or restrict the deletion of records` if there are related records in the referencing table.

For example, consider two tables: orders and customers. The orders table has a foreign key constraint referencing the customer_id column in the customers table.

    CREATE TABLE customers (
        customer_id INT PRIMARY KEY,
        customer_name VARCHAR(100)
    );

    CREATE TABLE orders (
        order_id INT PRIMARY KEY,
        customer_id INT,
        order_details VARCHAR(255),
        FOREIGN KEY (customer_id) REFERENCES customers(customer_id)
    );

If you try to delete a record from the `customers` table that has related records in the `orders` table, depending on the database settings, the deletion might be prevented, and *you may receive a foreign key constraint violation error*.

However, you can configure the behavior of `foreign key constraints using different ON DELETE actions`. For instance:

    CREATE TABLE orders (
        order_id INT PRIMARY KEY,
        customer_id INT,
        order_details VARCHAR(255),
        FOREIGN KEY (customer_id) REFERENCES customers(customer_id) ON DELETE CASCADE
    );

The `ON DELETE CASCADE` option means that if a record in the `customers` table is deleted, all related records in the `orders` table with a matching `customer_id` will also be deleted automatically. Other options include `ON DELETE SET NULL`, `ON DELETE SET DEFAULT`, or `ON DELETE RESTRICT`, which define different actions when deleting records from the referenced table.

<br>

> [!WARNING]
> 👁️
> Always use caution when setting these constraints, as they can affect the integrity and behavior of your database. It's essential to understand the implications of `foreign key constraints` and their associated `ON DELETE actions` *before implementing them in a production environment*.