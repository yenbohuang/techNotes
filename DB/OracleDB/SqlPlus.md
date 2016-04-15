# Login by Oracle account

```
    su - oracle
    sqlplus / as sysdba
```

# Save query result into a file

## Save query result

```
   spool yenbo-trace.log

   <some sql scripts>

   spool off
```

See details on <http://stackoverflow.com/questions/15253440/how-to-output-oracle-sql-result-into-a-file-in-windows>

## As a CSV file

Use "~" as separator since comma is very common in SQL scripts.

```
   set colsep ~
   set pagesize 0
   set trimspool on
   set headsep off
   set linesize 2000

   spool yenbo-trace.log

   <some sql scripts>

   spool off
```

See details on <http://stackoverflow.com/questions/643137/how-do-i-spool-to-a-csv-formatted-file-using-sqlplus>.