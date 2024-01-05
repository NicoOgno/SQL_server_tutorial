# $${\color{orange}Database\space Backup\space and\space Restore}$$

## Performing Database Backups and Restores

### Database Backup

<br>

1. **Full Database Backup:**

To create a full backup of a database, you can use the following T-SQL command:

    BACKUP DATABASE YourDatabaseName
    TO DISK = 'C:\Backup\YourDatabaseName_Full.bak'
    WITH FORMAT, NAME = 'Full Backup of YourDatabaseName';

- **`TO DISK`** specifies the location where the backup file will be stored.
- **`WITH FORMAT`** reinitializes the backup media, overwriting any existing backup sets.
- **`NAME`** provides a name for the backup set.

<br>

2. **Transaction Log Backup:**

Transaction log backups are used to back up the transaction log and allow for *point-in-time recovery*. To perform a transaction log backup:

    BACKUP LOG YourDatabaseName
    TO DISK = 'C:\Backup\YourDatabaseName_LogBackup.trn'
    WITH FORMAT, NAME = 'Log Backup of YourDatabaseName';

<br>

3. **Differential Database Backup:**

Differential backups capture changes made since the last full backup, reducing the backup size and time compared to a full backup. To perform a differential backup:

    BACKUP DATABASE YourDatabaseName
    TO DISK = 'C:\Backup\YourDatabaseName_Diff.bak'
    WITH DIFFERENTIAL, FORMAT, NAME = 'Differential Backup of YourDatabaseName';

<br><br>

### Database Restore

<br>

1. **Full Database Restore:**

        RESTORE DATABASE YourDatabaseName
        FROM DISK = 'C:\Backup\YourDatabaseName_Full.bak'
        WITH REPLACE, RECOVERY;


- **`WITH REPLACE`** option is used to overwrite the existing `database` (if it exists) and **`WITH RECOVERY`** brings the `database` online.

<br>

2. **Transaction Log Restore (Point-in-Time Recovery):**

        -- Restore the full backup first
        RESTORE DATABASE YourDatabaseName
        FROM DISK = 'C:\Backup\YourDatabaseName_Full.bak'
        WITH NORECOVERY; -- Do not recover the database yet

        -- Restore the transaction log backups in sequence
        RESTORE LOG YourDatabaseName
        FROM DISK = 'C:\Backup\YourDatabaseName_LogBackup.trn'
        WITH RECOVERY; -- Recover the database after restoring all transaction logs

<br>

3. **Differential Database Restore:**

        RESTORE DATABASE YourDatabaseName
        FROM DISK = 'C:\Backup\YourDatabaseName_Diff.bak'
        WITH RECOVERY;

<br>

> [!IMPORTANT]
> 🚩
> Ensure proper permissions and consider the recovery model (such as Full or Simple) of your database, as it affects the types of backups that can be performed.

<br><br>

**Database Backup / Restore from the Object Explorer:**

  1. Right click on your DB ▶️ *`Tasks`* ▶️ *`Backup... / Restore`*

  2. In the *Back up Database* window choose the *Backup type* `Full/Differential`

  3. Confirm the destination where is going to be saved 💾, click *Add* to select a new path.

  4. Save the file with `.bak` extension.

  5. Give `OK`.

<br>

> [!NOTE]
> 📝
> Is way easier to make `Full Backups` 🤹. When restoring if you keep the same name of the DB, your DB will be replaced.

<br>

> [!IMPORTANT]
> 🚩
> It's essential to schedule regular backups based on your organization's backup policy and ensure that backups are securely stored in different locations to prevent data loss. Test your backup and restore procedures periodically to verify that backups are valid and can be restored when needed.

<br><br>

### Solution to common errors when restoring a Backup

<br>

1. **Exclusive access could not be obtained because the database is in use**

**Solution:** This error occurs when the database being restored is in use. To solve this issue, close any window open for the database or close Management Studio entirely, then log in again.

<br>

2. **Database in Restoring mode. Text alongside the database name "(Restoring...)" does not allow login.**

**Solution:** This error occurs when performing a `RESTORE operation` in SSMS, where, in certain situations, it doesn't recognize the `WITH RECOVERY` option. Consequently, the database being restored stays in a state of *'restoring'* and might take an extended amount of time or fail to complete the process.

To solve this issue, follow these steps:

1. Close Management Studio and reopen it.

2. Since the database is in a `restoring state`, you should log in to the `MASTER database`.

      **a.** In the Login window, click on the Options button.

      **b.** In "Connect to database," select the 'master' database.

      **c.** Log in using Windows Authentication by selecting this option in the Server Name field, allowing you to log in without a username or password.

      Then, press `CTRL + N` to open a new script window and execute the following statement:

        RESTORE DATABASE YourDB WITH RECOVERY

    This command will bring the database out of the restoring state.

