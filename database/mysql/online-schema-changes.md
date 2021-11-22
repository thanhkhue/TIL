Why Online Schema Changes DDL doesn't support Foreign Keys?


* Foreign Keys : A column in one table indicates a column in another table, so that a row in one table have relationship with one or more rows in another table, that is the Foreign Key.
    + FK constraints is the enforcement of above relationship, its a db construct which watches over rows in tables and ensures the relationship does not break.
    + Mysql doesn't support FK per se, FKs are implemented by storage engine (InnoDB).
        -> so that, FK in InnoDB is coupled with table, there's space in the table FK exists, ADD/DROP FK is done by an ALTER TABLE statement.

- pt-online-schema-change is based on synchronous, same-transaction, data copy via [triggers](https://dev.mysql.com/doc/refman/8.0/en/trigger-syntax.html). At any point in time, when we populate data from original tables, that row of data definitely exists during the same transaction, thus make sure insert new row in ghost table is FK safe.

