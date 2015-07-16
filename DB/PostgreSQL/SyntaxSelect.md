# Syntax

    SELECT select_list
    FROM table_expression
    [ ORDER BY ... ]
    [ LIMIT { number | ALL } ] [ OFFSET number ]

When using `LIMIT`, it is important to use an `ORDER BY` clause that constrains the result rows into a unique order.

# Format String

    SELECT format(’Hello %s’, ’World’);
