# $${\color{orange}User\space Defined\space Functions}$$

### user-defined functions

`User-defined functions` (UDFs) allow you to encapsulate a set of `T-SQL statements` to perform a specific task and reuse that logic throughout your `SQL queries`. There are *three types of user-defined functions* in `SQL Server`:

<br>

1. **Scalar Functions:** These functions *return a single value based on the input parameters*.

        -- Syntax for creating a scalar function
        CREATE FUNCTION dbo.MyScalarFunction
        (
            @Param1 INT,
            @Param2 INT
        )
        RETURNS INT
        AS
        BEGIN
            DECLARE @Result INT;
            SET @Result = @Param1 + @Param2;
            RETURN @Result;
        END;

<br>

You can then use the `scalar function` in a query like this:

    SELECT dbo.MyScalarFunction(5, 3) AS SumResult;

<br><br>

2. **Inline Table-Valued Functions:** These functions *return a `table variable`*.

        -- Syntax for creating an inline table-valued function
        CREATE FUNCTION dbo.MyInlineTVF
        (
            @Param INT
        )
        RETURNS TABLE
        AS
        RETURN
        (
            SELECT *
            FROM SomeTable
            WHERE SomeColumn = @Param
        );

<br>

Usage, `inline table-valued function`:

    SELECT *
    FROM dbo.MyInlineTVF(123);

<br><br>

3. **Multi-Statement Table-Valued Functions:** These functions also return a `table variable` but *can contain multiple `T-SQL statements`*.

        -- Syntax for creating a multi-statement table-valued function
        CREATE FUNCTION dbo.MyMultiStatementTVF
        (
            @Param INT
        )
        RETURNS @ResultTable TABLE
        (
            ID INT,
            Name NVARCHAR(50)
        )
        AS
        BEGIN
            INSERT INTO @ResultTable (ID, Name)
            SELECT ID, Name
            FROM AnotherTable
            WHERE AnotherColumn = @Param;

            RETURN;
        END;

<br>

Usage, `multi-statement table-valued function`:

    SELECT *
    FROM dbo.MyMultiStatementTVF(456);

<br>

> [!NOTE]
> 📝
> These `user-defined functions` help *encapsulate logic, improve code readability, and promote code reuse* in SQL Server.