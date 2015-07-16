# Syntax

To insert the next value of the sequence into the serial column, specify that the serial column
should be assigned its default value. This can be done either by excluding the column from the list of
columns in the INSERT statement, or through the use of the DEFAULT key word.

# Insert and select ID immediately

    INSERT INTO persons (lastname,firstname) VALUES ('Smith', 'John') RETURNING id;

See details on  <http://stackoverflow.com/questions/2944297/postgresql-function-for-last-inserted-id> 

# Insert timestamp with time zone

    TIMESTAMP WITH TIME ZONE '2004-10-19 10:23:54+02'
