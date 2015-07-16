
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
