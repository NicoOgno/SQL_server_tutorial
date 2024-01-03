# $${\color{orange}Arithmetic\space and\space Comparison\space Operators}$$

### Arithmetic Operators

In SQL, **arithmetic operators** are used to *perform mathematical operations on numeric values* in expressions. Here are the common arithmetic operators:

<br>

1. **Addition (+):** Adds two numbers.

        SELECT column1 + column2 AS Result FROM your_table;

<br>

> [!TIP]
> 🧠
> You may use the *Addition operator* to *concatenate strings*.
<br>

2. **Subtraction (-):** Subtracts the right-hand operand from the left-hand operand.

        SELECT column1 - column2 AS Result FROM your_table;

<br>

3. **Multiplication (*):** Multiplies two numbers.

        SELECT column1 * column2 AS Result FROM your_table;

<br>

4. **Division (/):** Divides the left-hand operand by the right-hand operand.

        SELECT column1 / column2 AS Result FROM your_table;

<br>

5. **Modulus (%):** Returns the remainder of the division of the left-hand operand by the right-hand operand.

        SELECT column1 % column2 AS Result FROM your_table;

6. **Exponentiation ( ** or POWER function):** Raises the left-hand operand to the power of the right-hand operand.

        SELECT POWER(column1, column2) AS Result FROM your_table;

<br><br>

### Comparison Operators

In SQL, **comparison operators** are used to compare values in conditions.

<br>

1. **Less Than (<):** Checks if the value on the left is less than the value on the right.

        SELECT column1 FROM your_table WHERE column1 < 10;

<br>

2. **Greater Than (>):** Checks if the value on the left is greater than the value on the right.

        SELECT column1 FROM your_table WHERE column1 > 10;

<br>

3. **Less Than or Equal To (<=):** Checks if the value on the left is less than or equal to the value on the right.

        SELECT column1 FROM your_table WHERE column1 <= 10;

<br>

4. **Greater Than or Equal To (>=):** Checks if the value on the left is greater than or equal to the value on the right.

        SELECT column1 FROM your_table WHERE column1 >= 10;

<br>

5. **Equal To (=):** Checks if the values on both sides are equal. It is also used in assignments.

        SELECT column1 FROM your_table WHERE column1 = 10;

<br>

6. **Not Equal To (!= or <>):** Checks if the values on both sides are not equal.

        SELECT column1 FROM your_table WHERE column1 != 10;

<br>

> [!NOTE]
> 📝
> `Comparison operators` are commonly used in the WHERE clause of SELECT statements to filter rows based on specified conditions.