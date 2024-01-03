# $${\color{orange}Stored\space Procedures\space with\space INSERT}$$

This stored procedure takes parameters for inserting data into `Employee` table:

        -- Create a sample Employee table
        CREATE TABLE Employee (
            EmployeeID INT PRIMARY KEY,
            FirstName NVARCHAR(50),
            LastName NVARCHAR(50),
            Department NVARCHAR(50)
        );

        -- Create a stored procedure with an INSERT statement
        CREATE PROCEDURE InsertEmployee
            @EmpID INT,
            @FirstName NVARCHAR(50),
            @LastName NVARCHAR(50),
            @Department NVARCHAR(50)
        AS
        BEGIN
            -- Check if the employee already exists
            IF NOT EXISTS (SELECT 1 FROM Employee WHERE EmployeeID = @EmpID)
            BEGIN
                -- Insert the new employee
                INSERT INTO Employee (EmployeeID, FirstName, LastName, Department)
                VALUES (@EmpID, @FirstName, @LastName, @Department);

                PRINT 'Employee inserted successfully.';
            END
            ELSE
            BEGIN
                PRINT 'Employee with ID ' + CAST(@EmpID AS NVARCHAR(10)) + ' already exists.';
            END
        END;

In this example:

- The `stored procedure` is named `InsertEmployee`.

- It takes four parameters (`@EmpID`, `@FirstName`, `@LastName`, and `@Department`).

- It checks whether an employee with the given `EmployeeID` already exists in the `Employee` table.

- If the employee does not exist, it inserts a `new record` with the provided details.

- The `PRINT statements` are used for informational purposes.

- You can execute this `stored procedure` by calling it with appropriate parameter values, like this:

<br>

        EXEC InsertEmployee 101, 'John', 'Doe', 'IT';

<br><br>

### CREATE PROCEDURE

**Creates** a procedure:

    CREATE PROC InsertEmployee
        @EmpID INT,
        @FirstName NVARCHAR(50),
        @LastName NVARCHAR(50),
        @Department NVARCHAR(50)
    AS

<br>

### ALTER PROC

**Modifies** a procedure:

    ALTER PROC InsertEmployee
        @EmpID INT,
        @FirstName NVARCHAR(50),
        @LastName NVARCHAR(50),
        @Department NVARCHAR(50)
    AS