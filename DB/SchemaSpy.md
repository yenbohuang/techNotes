# Using SchemaSpy

## Download files

* Download SchemaSpy <http://schemaspy.sourceforge.net/>
* Install Graphviz
  * Windows 
      * Download from <http://www.graphviz.org/>
  * Ubuntu
      * Install from Ubuntu Software Center
* Download JDBC driver
* Prepare shell script or batch file

## Shell script sample

```
    #!/bin/sh

    HOST=localhost:5432
    DB=sampleDB
    SCHEMA=public
    USER=sampleUser
    PWD=samplePassword
    OUTPUT=/home/yenbohuang/dbschema/sampledb

    java -jar schemaSpy_5.0.0.jar \
      -t pgsql -host $HOST -db $DB -s $SCHEMA -u $USER -p $PWD -o $OUTPUT \
      -dp postgresql-9.4-1201.jdbc41.jar
```

## Batch file sample

```
    @echo off
    SET HOST=localhost:5432
    SET DB=sampleDB
    SET SCHEMA=public
    SET USER=sampleUser
    SET PWD=samplePassword
    SET OUTPUT=d:\var\schema\deltas3db

    java -jar schemaSpy_5.0.0.jar -t pgsql -host %HOST% -db %DB% -s %SCHEMA% -u %USER% -p %PWD% -o %OUTPUT% -dp postgresql-9.4-1201.jdbc41.jar -gv .\graphviz-2.38\release
```
