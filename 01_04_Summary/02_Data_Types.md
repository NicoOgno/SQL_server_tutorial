# $${\color{orange}Data\space Types\space 🔬}$$

## Common data types:

1. **INTEGER/INT:** To store whole numbers.

2. **VARCHAR(n)/CHAR(n):** VARCHAR for variable-length strings and CHAR for fixed-length strings, where "n" represents the maximum length of the string.

3. **FLOAT/REAL/DOUBLE:** To store decimal or floating-point numbers.

4. **DATE/TIME/DATETIME:** To store dates and times.

5. **BOOLEAN/BOOL:** To store logical values (true/false).

6. **NUMERIC/DECIMAL:** To store decimal numbers with fixed precision.

<br><br>

## Data types Description:

### $${\color{orange}Numbers}$$

<center>

||
|-------------|
**BIT** 1 byte 
0 or 1 
True o False
--
**TINYINT** 1 byte
0 To 255
--
**SMALLINT** 2 bytes
From -32,768 To 32,767
--
**INT** 4 bytes
From -2,147,483,648 To 2,147,483,647
--
**BIGINT** 8 bytes
From -9,223,372,036,854,775,808 To 9,223,372,036,854,775,807
--
**MONEY** 8 bytes
From -922,337,203,685,477.5808 To 922,337,203,685,477.5807
--
**DECIMAL** (10,2) Precision and Scale
1 To 9: 5 bytes
10 To 19: 9 bytes
20 To 28: 13 bytes
29 To 38: 17 bytes
</center>
<br><br>

### $${\color{orange}String}$$
<center>

||
|-------------|
**CHAR** 1 byte per character
From 1 To 8000
--
**VARCHAR** 1 byte per character variable
From 1 To 8000
--
**NCHAR** 2 bytes per character
From 1 To 4000
--
**NVARCHAR** 2 bytes per character variable
From 1 To 4000
--
**BINARY** 1 byte per value
From 1 To 8000
--
**VARBINARY** 1 byte per variable value
From 1 To 8000
</center>
<br><br>

### $${\color{orange}Date \space and \space Time}$$

<center>

||
|-------------|
**DATETIME** 8 bytes
YYYY-MM-DD hh:mm:ss:nnn
01/01/1753 To 31/12/9999
00:00:00 To 23:59:59.997
--
**DATE** 3 bytes
YYYY-MM-DD
From 01/01/0001 To 31/12/9999
--
**TIME** 5 bytes
hh:mm:ss:nnnnnnn
From 00:00:00.0000000 To 23:59:59.9999999
--
**SMALLDATETIME** 4 bytes
YYYY-MM-DD hh:mm:ss
01/01/1900 To 06/06/2079
00:00:00 To 23:59:59
</center>

<br>

> [!TIP]
> 🧠
> You may `SET` a `SMALLDATETIME` as follows:
> `DECLARE @newDate = SMALLDATETIME`
> `SET @newDate = '20240119 14:30:20`
> If you don't put a specific hour (14:30:20) SQL will put 12:00 as default.