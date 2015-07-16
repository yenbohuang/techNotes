# Syntax

The array subscript numbers are written within square brackets. By default PostgreSQL uses a one-based numbering convention for arrays, that is, an array of n elements starts with `array[1]` and ends with `array[n]`.


    SELECT name FROM sal_emp WHERE pay_by_quarter[1] <> pay_by_quarter[2];
    SELECT schedule[1:2][1:1] FROM sal_emp WHERE name = ’Bill’;

    INSERT INTO sal_emp
    VALUES (’Bill’,’{10000, 10000, 10000, 10000}’,’{{"meeting", "lunch"}, {"training", "presentation"}}’);


    UPDATE sal_emp SET pay_by_quarter = ’{25000,25000,27000,27000}’
    WHERE name = ’Carol’;

    UPDATE sal_emp SET pay_by_quarter[4] = 15000
    WHERE name = ’Bill’;

    UPDATE sal_emp SET pay_by_quarter[1:2] = ’{27000,27000}’
    WHERE name = ’Carol’;
