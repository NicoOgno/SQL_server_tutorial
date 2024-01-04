# $${\color{orange}Defining\space Data\space Type}$$

> [!TIP]
> 🧠
> We define data types to *prevent errors* and keep the same data type for the same field across our DB.

<br><br>

🔸**Define Data Type through the *Object Explorer***

In **Object Explorer** got to your DB ➡️ `Programmability` ➡️ `Types` and give right click to `New User-defined Data Types`.

🔸**Define Data Type through the *Console***

    CREATE TYPE IdPaciente from int not null

<br><br>

* After you define a `Data Type` you can go to your tables in your DB and assign that Data Type to the Data Type in the respective column.

<br>

<center>

![defuserDT](/images/defuserDT.png)

</center>