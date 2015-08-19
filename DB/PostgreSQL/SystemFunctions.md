# Useful system commands

```
    select version();
    select current_date;
```
    
# Drop existing connections

```
    SELECT pg_terminate_backend(pg_stat_activity.pid)
    FROM pg_stat_activity
    WHERE pg_stat_activity.datname = 'TARGET_DB'
    AND pid <> pg_backend_pid();
```

See details on <http://stackoverflow.com/questions/5408156/how-to-drop-a-postgresql-database-if-there-are-active-connections-to-it>.