# Backup DB Schema

* Use backup function by pgAdmin

![Backup function](https://github.com/yenbohuang/techNotes/blob/master/DB/PostgreSQL/images/pgAdmin_BackupSchema1.png)

* Configure "File Options"
  * Change format to "Plain"
  * Change encoding to "UTF8"

![File Options](https://github.com/yenbohuang/techNotes/blob/master/DB/PostgreSQL/images/pgAdmin_BackupSchema2.png)

* Configure "Dump Options #1"
  * Check "Only Schema", "Owner" and "Privilege"

![Dump Options #1](https://github.com/yenbohuang/techNotes/blob/master/DB/PostgreSQL/images/pgAdmin_BackupSchema3.png)

* Configure "Dump Options #2"
  * Uncheck "Verbose messages"

![Dump Options #2](https://github.com/yenbohuang/techNotes/blob/master/DB/PostgreSQL/images/pgAdmin_BackupSchema4.png)

* Review "Objects"
  * Make sure all tables are checked.

![xxx](https://github.com/yenbohuang/techNotes/blob/master/DB/PostgreSQL/images/pgAdmin_BackupSchema5.png)