# $${\color{orange}Conversion\space and\space Text\space Functions}$$

### LEFT and RIGHT Functions

`LEFT` and `RIGHT functions` are used to extract a specified number of characters from the left or right side of a `string`, respectively.

<br>

**LEFT Function:**

`LEFT function` returns a specified number of characters from the beginning (left side) of a string.

    LEFT(string_expression, number_of_characters)

<br>

- *Example 1:*

      -- Return the first 3 characters from the 'column_name' in the 'your_table_name' table
      SELECT LEFT(column_name, 3) FROM your_table_name;

<br>

- *Example 2:*

      -- Assuming 'employee_name' contains names like 'John Doe'
      SELECT LEFT(employee_name, 4) AS ShortName FROM employees;

This query would return the first four characters of each name in the `employee_name` `column`.

<br>

**RIGHT Function:**

`RIGHT function` returns a specified number of characters from the end (right side) of a string.

    RIGHT(string_expression, number_of_characters)

<br>

- *Example 1:* 

      -- Return the last 4 characters from the 'column_name' in the 'your_table_name' table
      SELECT RIGHT(column_name, 4) FROM your_table_name;

- *Example 2:*

      -- Assuming 'phone_number' contains numbers like '123-456-7890'
      SELECT RIGHT(phone_number, 4) AS LastFourDigits FROM contacts;

This query would return the last four digits of each phone number in the `phone_number` `column`.

<br><br>

### LEN

`LEN function` returns the number of characters in a string expression(**length**).

    LEN(string_expression)

<br>

Here's an example of how you might use the `LEN function`:

    -- Assuming 'column_name' contains strings
    SELECT LEN(column_name) AS StringLength FROM your_table_name;

<br><br>

### LOWER and UPPER Functions

`LOWER and UPPER functions` to convert characters in a string to lowercase or uppercase, respectively.

<br>

**LOWER Function:**

The `LOWER function` is used to convert all characters in a string to lowercase.

    LOWER(string_expression)

<br>

- *Example:*

      -- Assuming 'column_name' contains strings
      SELECT LOWER(column_name) AS LowercaseString FROM your_table_name;

<br>

**UPPER Function:**

The `UPPER function` is used to convert all characters in a string to uppercase.

    UPPER(string_expression)

<br>

- *Example:*

      -- Assuming 'column_name' contains strings
      SELECT UPPER(column_name) AS UppercaseString FROM your_table_name;

<br><br>

> [!TIP]
> 🧠
> Here's a more concrete example using both functions:

    DECLARE @firstname varchar(20)
    DECLARE @lastname varchar(20)
    SET @firstname = 'JOHN'
    SET @lastname = 'doE'

    PRINT UPPER(LEFT(@firstname, 1)) + LOWER(RIGHT(@firstname, LEN(@firstname) - 1)) + ' ' + UPPER(LEFT(@lastname, 1)) + LOWER(RIGHT(@lastname, LEN(@lastname) - 1))

The above query would print `John Doe`.

<br><br>

### REPLACE

`REPLACE` function is used to replace occurrences of a specified substring with another substring in a string.

    REPLACE(input_string, string_to_replace, replacement_string)

- **input_string:** The original string where replacements will be made.
- **string_to_replace:** The substring you want to replace.
- **replacement_string:** The substring that will replace occurrences of string_to_replace.

<br>

Here's an example:

    -- Replace 'old_value' with 'new_value' in the 'column_name' of 'your_table_name'
    UPDATE your_table_name
    SET column_name = REPLACE(column_name, 'old_value', 'new_value');

This example uses the `REPLACE function` within an `UPDATE statement` to replace occurrences of `'old_value'` with `'new_value'` in the specified `column` of the specified `table`.

<br>

> [!TIP]
> 🧠
> You can also use `REPLACE` in a `SELECT statement` to see the result without modifying the data:

    -- Select the column with replacements, without modifying the actual data
    SELECT column_name, REPLACE(column_name, 'old_value', 'new_value') AS ModifiedColumn
    FROM your_table_name;

<br>

- *Example:*

      DECLARE @firstname varchar(20)
      SET @firstname = 'Jo$hn'

      SELECT REPLACE(@firstname, '$', '')

This would show: `John`;

How it works `REPLACE(variable_name, substring_you_want_to_change, substring_to_replace_with)`

<br>

> [!NOTE]
> 📝
> `REPLACE` can be use over a `variable` or a `column field`.

<br><br>

### REPLICATE

`REPLICATE function` is used to *repeat a specific `string` a specified number of times*.

    REPLICATE (string_expression, number_of_repetitions)

- **string_expression:** The `string` you want to repeat.
- **number_of_repetitions:** The number of times to repeat the `string`.

Here's an example:

    -- Repeat the string 'abc' five times
    SELECT REPLICATE('abc', 5) AS RepeatedString;

This query would return a result with the value `abcabcabcabcabc`.

<br>

> [!TIP]
> 🧠
> You can use the `REPLICATE function` in various scenarios, such as when you need to *generate repeated characters for padding or when you want to repeat a specific pattern*.

Here's another example where `REPLICATE` is used to pad a string to a specific length:

    -- Pad the 'column_name' with leading zeros to make it 10 characters long
    SELECT 
        column_name,
        RIGHT(REPLICATE('0', 10) + column_name, 10) AS PaddedColumn
    FROM your_table_name;

This query pads the values in the `column_name` with leading zeros to make them 10 characters long.

<br><br>

### LTRIM and RTRIM

`LTRIM` and `RTRIM functions` are used to remove leading and trailing spaces, respectively, from a string.

<br>

**LTRIM Function:**

`LTRIM function` removes leading spaces from the left side of a string.

    LTRIM(string_expression)

Example:

    -- Remove leading spaces from the 'column_name' in 'your_table_name'
    SELECT LTRIM(column_name) AS TrimmedColumn FROM your_table_name;

<br>

**RTRIM Function:**

`The RTRIM function` removes trailing spaces from the right side of a string.

    RTRIM(string_expression)

Example:

    -- Remove trailing spaces from the 'column_name' in 'your_table_name'
    SELECT RTRIM(column_name) AS TrimmedColumn FROM your_table_name;

<br>

**Combined Example:**

If you want to *remove both leading and trailing spaces from a string*, you can use both functions:

    -- Remove leading and trailing spaces from the 'column_name' in 'your_table_name'
    SELECT LTRIM(RTRIM(column_name)) AS TrimmedColumn FROM your_table_name;

<br><br>

### CONCAT

`CONCAT function` is used to `concatenate` two or more `strings` into a single `string`. *It's a straightforward way to combine multiple `string` values*.

    CONCAT(string1, string2, ...)

- **string1, string2, ...:** The strings you want to concatenate.

Here's an example:

    -- Concatenate 'first_name' and 'last_name' columns with a space in between
    SELECT CONCAT(first_name, ' ', last_name) AS Full_Name
    FROM your_table_name;

This query would `concatenate` the values of the `first_name` and `last_name` `columns`, separated by a space.

> [!TIP]
> 🧠
> If any of the strings being `concatenated` is `NULL`, the `CONCAT function` will return `NULL`. If you want to handle potential `NULL` values differently, you might use the `ISNULL` or `COALESCE function` in conjunction with `CONCAT`.

    -- Concatenate with handling for potential NULL values
    SELECT CONCAT(ISNULL(first_name, ''), ' ', ISNULL(last_name, '')) AS Full_Name
    FROM your_table_name;

<br><br>

### GETDATE() and GETUTCDATE()

`GETDATE()` and `GETUTCDATE() functions` are used to retrieve the current date and time. However, there's a key difference between them:

<br>

**GETDATE():**

`GETDATE() function` returns the current date and time in the server's local time zone.

    -- Retrieve the current date and time
    SELECT GETDATE() AS CurrentDateTime;

<br>

**GETUTCDATE():**

`GETUTCDATE() function` returns the current Coordinated Universal Time (UTC), which is not affected by the local time zone of the server.

    -- Retrieve the current UTC date and time
    SELECT GETUTCDATE() AS CurrentUTCDateTime;

<br>

Example of using `GETDATE()` in an `INSERT` statement:

    -- Insert a new record with the current date and time
    INSERT INTO your_table_name (column1, timestamp_column)
    VALUES ('value1', GETDATE());

Example of using `GETUTCDATE()`:

    -- Insert a new record with the current UTC date and time
    INSERT INTO your_table_name (column1, timestamp_utc_column)
    VALUES ('value1', GETUTCDATE());

<br><br>

### DATEADD

`DATEADD function` *is used to add or subtract a specified time interval* (such as days, months, or years) from a date.

    DATEADD(datepart, number, date)

- **datepart:** The part of the date to add or subtract (e.g., 'day', 'month', 'year').
- **number:** The number of date parts to add or subtract.
- **date:** The date to which to add or subtract.

<br>

- *Example 1:* **Adding Days**

      -- Add 7 days to the current date
      SELECT DATEADD(day, 7, GETDATE()) AS NewDate;

- *Example 2:* **Subtracting Months**

      -- Subtract 3 months from a specific date
      SELECT DATEADD(month, -3, '2022-01-15') AS NewDate;

- *Example 3:* **Adding Years**

      -- Add 2 years to a specific date
      SELECT DATEADD(year, 2, '2022-01-15') AS NewDate;

> [!NOTE]
> 📝
> In these examples:
>
> - The first argument specifies the part of the date you want to add or subtract ('day', 'month', 'year').
> - The second argument is the number of date parts to add or subtract.
> - The third argument is the base date to which the addition or subtraction occurs.

<br><br>

### DATEDIFF

`DATEDIFF function` is used to calculate the difference between two dates, expressed in the units specified (such as days, months, or years).

    DATEDIFF(datepart, start_date, end_date)

- **datepart:** The part of the date to calculate the difference in (e.g., 'day', 'month', 'year').
- **start_date:** The starting date.
- **end_date:** The ending date.

Here are a few examples:

- *Example 1:* **Calculate the Difference in Days**

      -- Calculate the difference in days between two dates
      SELECT DATEDIFF(day, '2022-01-01', '2022-02-15') AS DayDifference;

- *Example 2:* **Calculate the Difference in Months**

      -- Calculate the difference in months between two dates
      SELECT DATEDIFF(month, '2021-05-01', '2022-01-15') AS MonthDifference;

- *Example 3:* **Calculate the Difference in Years**

      -- Calculate the difference in years between two dates
      SELECT DATEDIFF(year, '1990-01-01', '2022-01-01') AS YearDifference;

> [!NOTE]
> 📝
> In these examples:
>
> - The first argument (`datepart`) specifies the part of the date for which to calculate the difference ('day', 'month', 'year').
> - The second argument (`start_date`) is the starting date.
> - The third argument (`end_date`) is the ending date.

<br><br>

### DATEPART

`DATEPART function` is used to extract a specific part (such as year, month, day, hour, etc.) from a date. 

    DATEPART(datepart, date)

- **datepart:** The part of the date to be extracted (e.g., 'year', 'month', 'day', 'hour', etc.).
- **date:** The date from which to extract the specified part.

Here are a few examples:

- *Example 1:* **Extract the Year from a Date**

      -- Extract the year from a specific date
      SELECT DATEPART(year, '2022-02-15') AS YearPart;

- *Example 2:* **Extract the Month from a Date**

      -- Extract the month from the current date
      SELECT DATEPART(month, GETDATE()) AS MonthPart;

- *Example 3:* **Extract the Day of the Week from a Date**

      -- Extract the day of the week from a specific date
      SELECT DATEPART(weekday, '2022-02-15') AS DayOfWeek;

> [!NOTE]
> 📝
>In these examples:
>
> -The first argument (`datepart`) specifies the part of the date to be extracted ('year', 'month', 'day', 'hour', etc.).
> - The second argument (`date`) is the date from which to extract the specified part.

<br><br>

### ISDATE

`ISDATE function` is used to check if a given expression can be converted to a valid date or time. The `ISDATE` function returns 1 if the expression can be converted to a valid date or time; otherwise, it returns 0.

    ISDATE(expression)

- **expression:** The expression to be evaluated for its convertibility to a date or time.

Example:

      -- Check if '2022-01-15' can be converted to a valid date
      SELECT ISDATE('2022-01-15') AS IsDateResult;

This query would return `1` because '2022-01-15' is a valid date.

<br><br>

### CAST and CONVERT

`CAST` and `CONVERT functions` are used to convert an expression from one data type to another. They are often used interchangeably, but there are some differences in syntax and behavior.
<br>

**CAST Function:**

The `CAST function` is used for explicit data type conversion.

    CAST (expression AS data_type)

Example:

    -- Cast a string '123' to an integer
    SELECT CAST('123' AS INT) AS Result;

<br>

**CONVERT Function:**

The `CONVERT function` is more versatile and allows you to specify the target data type, format, and style.

    CONVERT (data_type, expression [, style])

Example:

    -- Convert a date to a varchar with a specific style
    SELECT CONVERT(VARCHAR, GETDATE(), 101) AS FormattedDate;

In this example, 101 is the style parameter indicating the MM/DD/YYYY format.

<br>

**Common Usage:**

    -- Using CAST to convert a decimal to an integer
    SELECT CAST(123.45 AS INT) AS Result;

    -- Using CONVERT to convert a date to a string with a specific format
    SELECT CONVERT(VARCHAR, GETDATE(), 120) AS FormattedDate;

In general, `CAST` is simpler and is often used for straightforward conversions, while `CONVERT` provides more flexibility when you need to specify additional parameters like format or style.

<br>

> [!WARNING]
> 👁️
> Remember to handle potential conversion errors by validating the data or using functions like `ISNULL` or `CASE` accordingly.