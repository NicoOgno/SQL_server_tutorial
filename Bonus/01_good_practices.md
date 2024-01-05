# $${\color{orange}Good\space Practices}$$

1. **Define short field names that best represent the stored value.** When naming them, use your preferred language, whether it's English, Spanish, etc., but maintain consistency in that language throughout the project.

2. **When defining a field name** (e.g., OrderID), **ensure that the field is named the same if you need to define it in another table.** This will save you many headaches when performing JOINS.

3. **When choosing a data type for a field, evaluate the values it will store and select the appropriate data type.** For example, if the field stores ages, it's unnecessary to define it as INT; a TINYINT type is more than sufficient. Saving bytes will improve database performance in the long run.

4. **When naming a Stored Procedure, it's recommended to use a naming convention that quickly defines the task that process performs**. For example:

        SEL_OrderOrders (SEL indicates it's a process that returns data)
        INS_Payments (INS indicates it's an insertion process)

5. **Normalize tables;** create as many tables as required by the database model. **Normalize up to the 3rd Normal Form (3NF).** If you believe certain fields should be in another table, do so.

6. **Ensure your database's security.** If you have access management capabilities, **create users, roles, and permissions that guarantee data security.** Do not allow any user to access and make modifications. Assign appropriate permissions to responsible users or those dedicated to development. You can use schemas if necessary.

7. **Always filter queries, whenever possible, by the Primary Key fields.** **When using JOINS, always place the PK fields in the ON clause.** This will optimize the query.

8. If you have implemented **Scheduled Jobs, ensure they run during off-peak hours** or when the **database has low activity to avoid affecting user performance.**

9. **Avoid excessive use of Triggers.** When these triggers are linked to highly concurrent inserts, updates, or deletes, **they can affect performance.**

10. **Periodically perform backups** and store the files preferably on a disk or external device.