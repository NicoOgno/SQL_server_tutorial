# $${\color{orange}Stored\space Procedures,\space Variables,\space and\space Subqueries}$$

### Stored Procedures

🔹 **Create a Stored Procedure:** got to *File* at the top left corner ➡️ *Recent Projects and Solutions*, choose the one your are working on. Give right click on Queries in the *Solution Explorer* ➡️ *New Query*. There you can create your procedure.

🔹**Modify Stored Procedure:** got to folder *Programmability* ➡️ *Stored Procedures* in the *Object Explorer*, right click on the *Stored Procedure* ➡️ *Modify*.

A `Stored Procedure` in SQL is a *precompiled collection of SQL statements and procedural logic, stored in the database's data dictionary, which can be executed as a single unit*. It helps in organizing and managing complex SQL tasks, and it can accept input parameters and return results.

    CREATE PROCEDURE GetEmployeeDetails
    AS
    BEGIN
        SELECT * FROM Employees;
    END;

This **stored procedure** named `GetEmployeeDetails` retrieves all records from the `Employees` table when executed.

**Stored procedures** can also take parameters:

    CREATE PROCEDURE GetEmployeesByDepartment
        @DepartmentID INT
    AS
    BEGIN
        SELECT * FROM Employees WHERE DepartmentID = @DepartmentID;
    END;

This **stored procedure** named `GetEmployeesByDepartment` retrieves records from the `Employees` table based on the specified `DepartmentID`.

To execute a **stored procedure**:

    EXEC GetEmployeeDetails;

For ***procedures with parameters***:

    EXEC GetEmployeesByDepartment @DepartmentID = 123;

**Stored procedures** offer advantages such as:

1. **Modularity and Reusability:** Procedures can be reused across multiple queries or applications.
2. **Security:** They provide a way to grant access to data while abstracting underlying table structures.
3. **Performance:** Precompiled and stored in the database, reducing execution time for repetitive tasks.

> [!WARNING]
> 👁️
> Keep in mind that the syntax for creating **stored procedures** might slightly differ across different database systems like `MySQL`, `PostgreSQL`, `SQL Server`, etc., *although the concept remains the same*.

> [!NOTE]
> 📝
> A **Stored Procedure** *must have a purpose, insert records, delete records or update records*.
>
> El GO se pone para que se ejecute el próximo PROCEDURE (en caso de haber otro PROCEDURE) como función aparte

<br>

### GO

In `Transact-SQL (T-SQL)`, **`GO`** is a batch separator rather than a `Transact-SQL statement`. It is used by `SQL Server Management Studio` and the `sqlcmd utility` to **separate batches of commands**.

When a script contains multiple batches separated by `GO`, *each batch is executed separately*. This means that if you're defining multiple `stored procedures` or performing multiple tasks, using `GO` will ensure that *each subsequent block of code is treated as a separate unit and executed independently*.

    CREATE PROCEDURE Procedure1 AS
    -- SQL statements for Procedure1

    GO

    CREATE PROCEDURE Procedure2 AS
    -- SQL statements for Procedure2

In this example, `GO` separates the creation of `Procedure1` from `Procedure2`. If you execute this script in `SQL Server Management Studio`, *each `CREATE PROCEDURE` statement will be treated as a separate batch and executed accordingly*.

> [!NOTE]
> 📝
> `GO` **is not a SQL statement;** rather, *it's a directive recognized by `SQL Server Management Studio` and some other SQL tools to define batch boundaries*. It's often used for administrative purposes, script separation, or when you need to execute different parts of a script independently.

> [!IMPORTANT]
> 🚩
> This `PROCEDURES` are stored in the folder *Programmability* ➡️ *Stored Procedures*.

<br>

### SET ANSI_NULLS ON

In `SQL Server`, the `SET ANSI_NULLS ON` statement is used to control the behavior of how `NULL` values are compared. When `SET ANSI_NULLS` is set to `ON`, comparisons against `NULL` values follow the `ANSI` standard behavior, where `NULL` is not equal to any value, including another `NULL`.

By default, `ANSI_NULLS` is set to `ON` in modern versions of `SQL Server`, ensuring that queries adhere to the `ANSI SQL` standard for `NULL` comparisons.

    SET ANSI_NULLS ON;

    SELECT * FROM YourTable WHERE YourColumn = NULL;

The comparison `YourColumn = NULL` will not return any rows, even if there are rows where `YourColumn` contains `NULL` values. This is because `NULL` is not considered equal to `NULL` when `ANSI_NULLS` is `ON`.

> [!IMPORTANT]
> 🚩
> *Changing the `ANSI_NULLS` setting might impact the behavior of existing queries and procedures in your database*. However, explicitly setting `ANSI_NULLS ON` or `OFF` within `stored procedures` or `query batches` can control the behavior for those specific executions.

<br>

### SET QUOTED_IDENTIFIER ON

In `SQL Server`, the `SET QUOTED_IDENTIFIER ON` statement is used to enforce the usage of double quotation marks for quoted identifiers, such as table names, column names, etc. This setting ensures that double quotation marks **(" ")** are treated as delimiters for identifiers instead of single quotation marks **(' ')**.

When `QUOTED_IDENTIFIER` is set to `ON`:

1. **Double quotation marks (" ")** are used to delimit identifiers.
2. **Single quotation marks (' ')** are used for string literals.

By default, `QUOTED_IDENTIFIER` is set to `ON` in modern versions of `SQL Server`, *ensuring that double quotation marks are recognized as delimiters for identifiers*.

    SET QUOTED_IDENTIFIER ON;

    SELECT * FROM "YourTable" WHERE "YourColumn" = 'SomeValue';

In the above query, `YourTable` and `YourColumn` are treated as quoted identifiers due to the presence of double quotation marks.

> [!NOTE]
> 📝
> Setting `QUOTED_IDENTIFIER` to `ON` can be useful when dealing with identifiers that contain reserved words, spaces, or special characters, but it's essential to consider the implications, especially if migrating or porting scripts across different database systems where identifier delimiters might differ.

<br>

### ALTER PROCEDURE

The `ALTER PROCEDURE` statement in `SQL` is used to modify an existing `stored procedure` in the database. *It allows you to change the definition of the `stored procedure` by adding parameters, altering the logic, or making other modifications*.

    ALTER PROCEDURE procedure_name
        [ { @parameter data_type } = value ]
    AS
    BEGIN
        -- SQL statements and logic here
    END;

- **procedure_name:** The name of the `stored procedure` you want to modify.
- **@parameter data_type:** Optional parameters and their data types to be added or modified.
- **value:** Optional default value for the parameter.
- **AS and BEGIN...END:** The procedural logic or `SQL` statements inside the `stored procedure`.

For example, to modify a **stored procedure** named `GetEmployeeDetails` by adding a new parameter:

    ALTER PROCEDURE GetEmployeeDetails
        @EmployeeID INT,
        @DepartmentID INT
    AS
    BEGIN
        SELECT * FROM Employees WHERE EmployeeID = @EmployeeID AND DepartmentID = @DepartmentID;
    END;

In this example, `GetEmployeeDetails` is altered to accept two additional parameters: `@EmployeeID` and `@DepartmentID`.

> [!WARNING]
> 👁️
> Remember that when modifying a **stored procedure** using `ALTER PROCEDURE`, you should be cautious as any changes might affect the behavior of other code or applications that rely on the **stored procedure**.

<br>

### EXEC

In SQL, the `EXEC` or `EXECUTE` statement is used to *execute stored procedures or dynamic SQL statements*.

    EXEC procedure_name;

Here's an example of executing a **stored procedure** named `GetEmployeeDetails`:

    EXEC GetEmployeeDetails;

If the **stored procedure** requires **parameters**, you can provide values for those **parameters**:

    EXEC GetEmployeesByDepartment @DepartmentID = 123;

In this example, `GetEmployeesByDepartment` is a **stored procedure** that accepts a `DepartmentID` **parameter**, and `EXEC` is used to **execute** it with the **parameter value** of `123`.

<br>

Additionally, the **EXEC statement** can be used to execute **dynamic SQL statements** that are constructed at *runtime* as a `string`. For example:

    DECLARE @sqlCommand NVARCHAR(MAX);
    SET @sqlCommand = 'SELECT * FROM Employees WHERE DepartmentID = 5';
    EXEC (@sqlCommand);

Here, `@sqlCommand` is a variable containing a `SQL query` as a `string`, and `EXEC` is used to *execute the dynamically constructed SQL command*.

> [!TIP]
> 🧠
> When using *`dynamic SQL` with `EXEC`, ensure to handle input carefully to prevent `SQL injection vulnerabilities`*.