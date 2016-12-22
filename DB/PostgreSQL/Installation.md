# Install Portable Version on Windows (Not for Production Usage)

* Download software from <http://www.turnkeylinux.org/postgresql>
* Unzip the archive file. For example,
  * `D:\PortablePrograms\postgresql-9.4.1-3-windows-x64-binaries\pgsql`
* Create data and log folders. For example,
  * `D:\pgsql-repo\data`
  * `D:\pgsql-repo\log`
* Create a batch file (`pgsql-init.bat`) and run it for initializing DB repository when first install.

````
    @ECHO OFF
    SET USER=postgre
    SET ENCODING=UTF8
    SET DATADIR=D:\pgsql-repo\data
    SET PSSQLBIN=D:\PortablePrograms\postgresql-9.4.1-3-windows-x64-binaries\pgsql\bin
        
    %PSSQLBIN%\initdb -U %USER% -W -E %ENCODING% -D %DATADIR%
````

* Create another batch file (pgsql-start.bat) for starting DB.

````
    @ECHO OFF
    SET PSSQLBIN=D:\PortablePrograms\postgresql-9.4.1-3-windows-x64-binaries\pgsql\bin
    SET DATADIR=D:\pgsql-repo\data
    SET LOGFILE=D:\pgsql-repo\log\postgres-start.log

    %PSSQLBIN%\pg_ctl -D %DATADIR% -l %LOGFILE% start
````

* Create another batch file (pgsql-stop.bat) for stopping DB.

````
    @ECHO OFF
    SET PSSQLBIN=D:\PortablePrograms\postgresql-9.4.1-3-windows-x64-binaries\pgsql\bin
    SET DATADIR=D:\pgsql-repo\data
    
    %PSSQLBIN%\pg_ctl -D %DATADIR% stop
````

# Install on Linux

## Ubuntu

* No need to install PostgreSQL since it is installed with Ubuntu.
* Start PostgreSQL
  * `sudo –u postgres /etc/init.d/postgresql start`
* Stop PostgreSQL
  * `sudo -u postgres /etc/init.d/postgresql stop`
* Change password for “postgres” account
  * `sudo -u postgres psql postgres`
  * `Type command under PostgreSQL console “\password postgres”`
* Create DB
  * `sudo -u postgres createdb mydb`

Refer to detail document here: <https://help.ubuntu.com/community/PostgreSQL>

## CentOS

    $ sudo yum install postgresql-server
    $ sudo postgresql-setup initdb
    $ sudo service postgresql start
    $ sudo chkconfig postgresql on

# Create DB

The following contents are copied from manual.

    root# mkdir /usr/local/pgsql/data
    root# chown postgres /usr/local/pgsql/data
    root# su postgres
    postgres$ initdb -U yenbo -W -E UTF8 --lc-collate=en_US.UTF8 --lc-ctype=en_US.UTF8 -D /usr/local/pgsql/data
    postgres$pg_ctl start -l /usr/local/pgsql/logfile.log -D /usr/local/pgsql/data initdb

If you do not trust other local users, we recommend you use one of initdb’s `-W`, `--pwprompt` or `--pwfile` options to assign a password to the database superuser. Also, specify `-A md5` or `-A password` so that the default trust authentication mode is not used; or modify the generated `pg_hba.conf` ﬁle after running `initdb`, but before you start the server for the ﬁrst time.

For PostgreSQL servers starting with version 8.0, this is controlled using the `"listen_addresses"` parameter in the `postgresql.conf` file. Here, you can enter a list of IP addresses the server should listen on, or simply use `'*'` to listen on all available IP addresses.

The initial settings in `pg_hba.conf` are quite restrictive, in order to avoid unwanted security holes caused by unreviewed but mandatory system settings. You'll probably want to add something like 

    host all all 192.168.0.0/24 md5 

# Start/stop on Ubuntu

````
    /etc/init.d/postgresql start/stop
````

# Set password

    $ sudo -u postgres psql postgres
    # \password postgres

See details on <https://help.ubuntu.com/community/PostgreSQL> 

Or,

    # alter user postgres password '???';
