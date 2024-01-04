# $${\color{orange}Variables 🤹}$$

## Variables

In SQL, **variables** are used to `store data temporarily within the scope of a script`, `stored procedure`, `function`, or `batch`. *These variables can hold single values or tables and can be manipulated or referenced throughout the script*.

The syntax for declaring and using variables varies slightly between different `SQL database systems`. Here is a general example using `T-SQL (SQL Server)`:

### Declaring Variables:

    DECLARE @variable_name datatype; -- Single variable declaration

For example:

    DECLARE @name VARCHAR(50); -- Declaring a variable to store a string value
    DECLARE @age INT; -- Declaring a variable to store an integer value

### Assigning Values to Variables:

    SET @variable_name = value; -- Assigning a value to a variable

For example:

    SET @name = 'John';
    SET @age = 30;

### Using Variables in SQL Statements:

**Variables** can be used in various `SQL statements` like `SELECT`, `INSERT`, `UPDATE`, `DELETE`, etc.

Example usage in a SELECT statement:

    SELECT * FROM Employees WHERE Name = @name;

### Table Variables:

**SQL Server** also allows declaring table variables that can hold multiple rows of data.

    DECLARE @EmployeeTable TABLE (
        ID INT,
        Name VARCHAR(50),
        Salary DECIMAL(10, 2)
    );

**Table variables** can be used *similarly to temporary tables in `SQL Server`*.

Remember, the **scope of variables is limited to the script or the batch where they are declared**. They can't be used across different connections or sessions.

> [!WARNING]
> 👁️
> The syntax and capabilities of variables might differ in other `SQL database systems` like `MySQL`, `PostgreSQL`, `Oracle`, etc., so it's important to *refer to the specific documentation of the database you're working with* for precise syntax and usage details.

### Other Declaration Examples:

    DECLARE @entero INT

    SET @entero = NULL

    SELECT ISNULL(@entero, 0) AS Valor



    DECLARE @decimal DECIMAL(10,2)

    SET @decimal = NULL

    SELECT ISNULL(@decimal, 0.00) AS Valor



    DECLARE @cadena VARCHAR(50)

    SET @cadena = NULL

    SELECT ISNULL(@cadena, 'Texto predeterminado') AS Valor



    DECLARE @fecha DATETIME

    SET @fecha = NULL

    SELECT ISNULL(@fecha, GETDATE()) AS Valor



    DECLARE @booleano BIT

    SET @booleano = NULL

    SELECT ISNULL(@booleano, 0) AS Valor



    DECLARE @moneda MONEY

    SET @moneda = NULL

    SELECT ISNULL(@moneda, 0.00) AS Valor

<br><br>

> [!NOTE]
> 📝
> Still lack of system variables, example: `@@IDENTITY`.