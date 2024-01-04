# $${\color{orange}sp\_help\space \space \&\space \space sp\_helptext}$$

### sp_help

**`sp_help`** is a `system stored procedure` in *SQL Server* that provides *information about a database object such as a table, view, stored procedure, or user-defined datatype*. It displays information like column names, data types, length, and other details about the specified object.

    sp_help [ [ @objname = ] 'name' ]

- **@objname:** Specifies the name of the object for which to display information.

For example, if you want to get information about a table named `MyTable`, you would execute:

    sp_help MyTable;

This would return details about the table, including its columns, data types, and other relevant information.

<br>


### sp_helptext

**`sp_helptext`** is a `system stored procedure` in SQL Server that is used to display the definition (text) of a `user-defined` rule, default, `unencrypted Transact-SQL stored procedure`, `user-defined Transact-SQL function`, trigger, or view.

    sp_helptext [ @objname = ] 'name' [ , [ @columnname = ] 'column' ]

- **@objname:** Specifies the name of the object for which to display the definition.
- **@columnname:** Specifies the name of the column in the specified table or view for which to display the definition.

<br>

For example, if you want to see the definition of a `stored procedure` named `MyStoredProcedure`, you would execute:

    sp_helptext MyStoredProcedure;

<br>

> [!NOTE]
> 📝
> Keep in mind that the user executing the `sp_help` or `sp_helptext` needs the necessary permissions to view the object's definition.