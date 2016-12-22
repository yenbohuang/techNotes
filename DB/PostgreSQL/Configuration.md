# Configure Postgre SQL

## Configuration file on Ubuntu

````
    /etc/postgresql/9.4/main/postgresql.conf
````

## Edit postgresql.conf

### Windows

* Stop PostgreSQL
* Open `"postgresql.conf"` by pgAdmin (or change it by text editor).

![Open postgresql.conf](https://github.com/yenbohuang/techNotes/blob/master/DB/PostgreSQL/images/pgAdmin_OpenPostgresqlConf1.png) 

* Change "listen_addresses" to "*" and allow connections from other computers.

![Change listen_addresses](https://github.com/yenbohuang/techNotes/blob/master/DB/PostgreSQL/images/pgAdmin_OpenPostgresqlConf2.png)

* Start PostgreSQL

### Ubuntu

* Edit configuration file under `"/etc/postgresql/<version>/main/postgresql.conf"`
* Restart server by `"sudo /etc/init.d/postgresql restart"`.
* Remember adding "port forwarding" if you are using Virtual Box.

### CentOS

* Edit configuration file under `"/var/lib/pgsql/data/postgresql.conf"`.
* Restart server by `"sudo service postgresql restart"`

## Edit pg_hba.conf

### Windows

* Stop PostgreSQL.
* Open "pg_hba.conf" by pgAdmin (or change it by text editor).

![Open pg_hba.conf](https://github.com/yenbohuang/techNotes/blob/master/DB/PostgreSQL/images/pgAdmin_OpenPgHbaConf1.png)

* Change "Method" from "trust" to "md5".

![Change method to MD5](https://github.com/yenbohuang/techNotes/blob/master/DB/PostgreSQL/images/pgAdmin_OpenPgHbaConf2.png) 

* Add host IP and allow connections from other computers.
  * For example, "host all all 192.168.0.0/32 md5"
* Start PostgreSQL.

### Ubuntu

* Edit configuration file under `"/etc/postgresql/<version>/main/pg_hba.conf"`
* Reload configuration file `"sudo /etc/init.d/postgresql reload"`.
