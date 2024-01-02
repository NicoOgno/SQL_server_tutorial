# $${\color{orange}Referential\space Integrity\space Rules}$$

**Primary Key Constraint:** A primary key constraint ensures that a column or a set of columns within a table uniquely identify each row in that table.

**Foreign Key Constraint:** A `foreign key` constraint `establishes a relationship between two tables`, where the `foreign key in one table refers to the primary key in another table`.

**Referential Integrity:** Referential integrity `ensures that relationships between tables are maintained`; it ensures that the foreign key value of each row in one table corresponds to a valid primary key value in the related table.

**CASCADE:** The CASCADE option `specifies that changes to a primary key will propagate to the foreign key`, maintaining referential integrity. For example, if a primary key is deleted, CASCADE will delete corresponding foreign key values.

**RESTRICT:** The RESTRICT option `prevents any action that would destroy referential integrity`, typically by `preventing deletion or modification of the primary key if it has dependent rows in another table`.

**NO ACTION:** Similar to RESTRICT, the NO ACTION option `prevents the deletion or modification of a primary key if it has dependent rows in other tables`.

**SET NULL:** When a row in the parent table `(primary key) is deleted or updated`, the corresponding `foreign key values in the child table are set to NULL`.

**SET DEFAULT:** If a `primary key value is deleted or updated`, the `foreign key` values in the related table are `set to their default values`.

**CHECK Constraints:** These constraints `allow you to define rules that restrict the values that can be inserted or updated in a column`.

<br><br>

> [!NOTE]
> 📝
> These rules help maintain data integrity in a relational database, ensuring that relationships between tables are coherent and consistent.

<br><br>

## $${\color{green}Database\space Diagrams\space DER}$$

**Create DB Diagram:** in `Object Explorer` got to your Database right click `Database Diagrams` ➡️ `New Database Diagram`, then add the tables you wish to see.

**Create Foreign Key:** in `Object Eplorer` got to the table you want to put the `FK`, right click on folder `Keys` ➡️ `New Foreign Key`. Then in the prompt (*Foreign Key Relationships*) go to `Tables And Columns Specification`. Then click the 3 dots button next to `Tables And Columns Specification`. There `set the Primary Key Table and the field` and do the same for the `Foreign Key Table`. Or make it the same way but in the `Database Diagrams` giving right click to a table and setting the relations.

**Give more than one Foreign Key:** If a table already have a `FK` click the `Add` button at the left bottom corner. Then proceed as specified above in `Tables And Columns Specification`.

**Create Relations from the Diagram window (`DER`):** In the Diagram window choose the field in the table you want to make the relation *click and **Drag** to the table in the Specific field you want the Foreign Key to be*. The prompt `Tables And Columns Specification` will open, to confirm the relation click OK. Finally save the changes in your Diagram to see the changes reflected.

<br><br>

<center>

![assignFK](/images/assignFK.png)

</center>

Then click OK and Close. Finally save the changes to the table 💾.

> [!NOTE]
> 📝
> The Database Diagram will automatically generate the visual relation between tables.

> [!TIP]
> 🧠
> If you have many tables in your `Database Diagram` right click in the Diagram window ➡️ `Arrange Tables` will help to organice the visualization.
>
> Right click on the restriction between tables (link) ➡️ `Properties` will give info about the `PK`, `FK` and more.

<br><br>

### $${\color{green}Relation\space One\space to\space Many}$$

<center>

![relOneToMany](/images/relOneToMany.png)

</center>

> [!TIP]
> 🧠
> In your `Database Diagram` the restriction between tables (link) tells you the relation between Tables 8 (infinit) means there are many of that and 🗝️ (key) means one.

<br><br>

### $${\color{green}Delete\space Foreign\space Key\space 🔑❌}$$

* In `Object Explorer` go to `Tables/Keys` right click on the `Foreign Key` ➡️ `Delete`. Or in the `Database Diagram` right click on the restriction (link) ➡️ `Delete Relationships from Database` and then save the Diagram 💾.

<br><br>

### $${\color{green}Modify\space Diagram}$$

* In `Object Explorer` go to YourDB/Database_Diagrams, double click on the Diagram you want to modify and make right click in the `Diagrams window`. You will be able to add Tables and more.

<br><br>

### $${\color{green}Many\space to\space Many\space Relation}$$

* To make a `Many to Many` relation between two tables you have to make a third table to relate them in order to keep the `Referential Intregrity Rules`.

<br><br>

### $${\color{green}One\space to\space One\space Relation}$$

> [!WARNING]
> 👁️
> If one table is "New" (empty) and the other already has data, create the `Foreign Key` in the "Empty Table".