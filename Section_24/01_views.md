# $${\color{orange}Views}$$

### Views

Views *are `virtual database objects` that represent a `stored query`*. They allow you to retrieve data from one or multiple tables using a predefined query stored in the database. Views do not store data themselves; they provide a way to present data stored in tables in a specific format or structure.

You can create a *`VIEW`* from the `Object Explorer`. Go to your `Database` ➡️ *`VIEWS`* ➡️ *`New View`*, then add the tables you want to check in that `VIEW`

Example of creating a simple view in `T-SQL`:

    -- Creating a view
    CREATE VIEW EmployeeView
    AS
    SELECT EmployeeID, FirstName, LastName, Department
    FROM Employees
    WHERE Department = 'IT';

- **EmployeeView** is the name of the view being created.
- **Employees** is the name of the table.
- The `SELECT statement` retrieves specific `columns` (`EmployeeID`, `FirstName`, `LastName`, `Department`) from the Employees table.
- The `WHERE clause` filters the data to include only those employees from the `'IT'` department.

Once the *`view`* is created, you can query it like a regular table:

    -- Querying the view
    SELECT * FROM EmployeeView;

Views offer several benefits:

1. **Simplicity:** They simplify complex queries by *encapsulating logic and business rules*.

2. **Security:** Views can be used to *restrict access to certain columns or rows*, allowing users to see only specific data.

3. **Consistency:** Views *ensure that users always see the data in a consistent format*, regardless of changes made to the underlying tables.

4. **Performance:** They can *optimize frequently used queries* by storing the logic and reducing the need to rewrite complex `joins` or `filters`.

<br>

Views can also be updated or dropped using `SQL commands`:

- **ALTER VIEW:** Modifies an existing view's definition.

- **DROP VIEW:** Deletes a view from the database.

Example: 

    -- Modifying a view
    ALTER VIEW EmployeeView
    AS
    SELECT EmployeeID, FirstName, LastName, Department
    FROM Employees
    WHERE Department = 'Sales';
