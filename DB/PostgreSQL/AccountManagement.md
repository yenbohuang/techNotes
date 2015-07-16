# Create super user

    CREATE USER yenbo WITH SUPERUSER CREATEDB CREATEROLE REPLICATION PASSWORD '????';

The role attributes LOGIN, SUPERUSER, CREATEDB, and CREATEROLE can be thought of as special privileges, but they are never inherited as ordinary privileges on database objects are. You must actually SET ROLE to a specific role having one of these attributes in order to make use of the attribute. Continuing the above example, we might well choose to grant CREATEDB and CREATEROLE to the admin role. Then a session connecting as role joe would not have these privileges immediately, only after doing SET ROLE admin.

See details on <http://www.postgresql.org/docs/8.1/static/role-membership.html>

# Revoke permissions
 
    REVOKE ALL ON schema public FROM public;

See details on <http://dba.stackexchange.com/questions/35316/why-is-a-new-user-allowed-to-create-a-table>

# List all roles

    select * from pg_roles;

# Grant permission to application account

    GRANT SELECT, UPDATE ON ALL SEQUENCES IN SCHEMA public TO appuser;
    GRANT SELECT, INSERT, DELETE, UPDATE ON ALL TABLES IN SCHEMA public TO appuser;