# Find SQL scripts run in a period of time

```
   SELECT A.SAMPLE_TIME,
          A.SESSION_ID,
          A.WAIT_CLASS,
          A.WAIT_TIME,
          A.SESSION_STATE,
          A.TIME_WAITED,
          A.BLOCKING_SESSION_STATUS,
          A.BLOCKING_SESSION,
          A.PROGRAM,
          C.PARSING_SCHEMA_NAME,
          C.SQL_TEXT
   FROM v$ACTIVE_SESSION_HISTORY A,
        v$SQLAREA C
   WHERE A.SQL_ID = C.SQL_ID
         AND C.PARSING_SCHEMA_NAME NOT IN ('SYS', 'ORACLE_OCM', 'SYSMAN')
         AND A.SAMPLE_TIME BETWEEN '15-APR-16 10.20.00 AM' AND '15-APR-16 10.45.00 AM' ORDER by A.SAMPLE_TIME;
```

See details on:

* <http://www.dba-oracle.com/oracle10g_tuning/t_v$active_session_history.htm>
* <https://docs.oracle.com/cd/B10500_01/server.920/a96533/sqlviews.htm>