# Basic scripts

    CREATE TABLE products (
        product_no integer,
        name text,
        price numeric DEFAULT 9.99
    );

    CREATE TABLE products (
        product_no SERIAL,
        ...
    );

    CREATE TABLE products (
        product_no integer,
        name text,
        price numeric CONSTRAINT positive_price CHECK (price > 0)
    );

    CREATE TABLE products (
        product_no integer NOT NULL,
        name text NOT NULL,
        price numeric
    );

    CREATE TABLE products (
        product_no integer UNIQUE,
        name text,
        price numeric
    );

    CREATE TABLE example (
        a integer,
        b integer,
        c integer,
        UNIQUE (a, c)
    );


    CREATE TABLE products (
        product_no integer PRIMARY KEY,
        name text,
        price numeric
    );

# Reference

    CREATE TABLE orders (
        order_id integer PRIMARY KEY,
        product_no integer REFERENCES products (product_no),
        quantity integer
    );

    CREATE TABLE order_items (
        product_no integer REFERENCES products ON DELETE RESTRICT,
        order_id integer REFERENCES orders ON DELETE CASCADE,
        quantity integer,
        PRIMARY KEY (product_no, order_id)
    );

Since a DELETE of a row from the referenced table or an UPDATE of a referenced column will require a scan of the referencing table for rows matching the old value, it is often a good idea to index the referencing columns too.

# Enum
 
    CREATE TYPE mood AS ENUM (’sad’, ’ok’, ’happy’);
    CREATE TABLE person (
        name text,
        current_mood mood
    );

# Array
 
    CREATE TABLE sal_emp (
        name text,
        pay_by_quarter integer[],
        schedule text[][]
    );
 
 # Database
 
     CREATE DATABASE <DB name> OWNER <user>;
 