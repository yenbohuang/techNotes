# Check Oracle DB server time

```
   SELECT TO_CHAR(SYSDATE, 'MM-DD-YYYY HH24:MI:SS') "NOW"
   FROM DUAL;
```

See details on <https://docs.oracle.com/cd/B19306_01/server.102/b14200/functions172.htm>.