# $${\color{orange}Stored\space Procedures\space SELECT,\space UPDATE,\space DELETE\space and\space CREATE}$$

## Stored Procedures

`Stored procedures` in `SQL Server` *are named sets of SQL statements that can be executed with a single command*. They can accept parameters, perform actions like querying or modifying data, and return results.

<br><br>

### SELECT stored procedure

Fetch data from a table:

    CREATE PROCEDURE MySelectProcedure
    AS
    BEGIN
        SELECT *
        FROM YourTableName; -- Replace YourTableName with the name of your table
    END;

Execute this stored procedure:

    EXEC MySelectProcedure;

<br>

You can also create `stored procedures` that accept `parameters`:

    CREATE PROCEDURE SelectByCategory
        @CategoryID INT
    AS
    BEGIN
        SELECT *
        FROM Products
        WHERE CategoryID = @CategoryID;
    END;

Execute this `stored procedure` with a `parameter`:

    EXEC SelectByCategory @CategoryID = 2; -- Replace 2 with the desired CategoryID

<br><br>

### UPDATE stored procedure

    CREATE PROCEDURE UpdateEmployeeSalary
        @EmployeeID INT,
        @NewSalary DECIMAL(10, 2)
    AS
    BEGIN
        UPDATE Employees
        SET Salary = @NewSalary
        WHERE EmployeeID = @EmployeeID;
    END;

`UpdateEmployeeSalary` is a `stored procedure` that accepts two `parameters`: `@EmployeeID` for identifying the employee whose salary needs to be updated and `@NewSalary` for the new salary value.

Execute this `stored procedure`:

    EXEC UpdateEmployeeSalary @EmployeeID = 123, @NewSalary = 55000.00;

This execution will update the salary of the employee with ID 123 to $55,000.00.

<br><br>

### DELETE stored procedure

    CREATE PROCEDURE DeleteEmployee
        @EmployeeID INT
    AS
    BEGIN
        DELETE FROM Employees
        WHERE EmployeeID = @EmployeeID;
    END;

In this example, `DeleteEmployee` is a `stored procedure` that accepts `@EmployeeID` as a parameter to identify the employee to be deleted from the `Employees table`.

Execute this `stored procedure`:

    EXEC DeleteEmployee @EmployeeID = 123;

This execution will delete the employee with ID 123 from the `Employees table`.

<br><br>

### CREATE stored procedure

    CREATE PROCEDURE MyProcedureName
    AS
    BEGIN
        -- Your SQL statements here
        SELECT * FROM YourTableName; -- Replace YourTableName with the name of your table or specify your SQL logic
    END;

Execute this `stored procedure`:

    EXEC MyProcedureName;

<br>

You can also create `stored procedures` that accept `parameters`:

    CREATE PROCEDURE MyProcedureWithParams
        @Param1 INT,
        @Param2 VARCHAR(50)
    AS
    BEGIN
        -- Your SQL statements using parameters here
        SELECT * FROM YourTable WHERE Column1 = @Param1 AND Column2 = @Param2; -- Replace YourTable and Column1, Column2 with actual table and column names
    END;

Execute this `stored procedure` with `parameters`:

    EXEC MyProcedureWithParams @Param1 = 123, @Param2 = 'SomeValue';
