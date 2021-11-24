For Postgres v10 or less, adding new columns without default values is non locking operation.
But when specifying default value, the entire table get rewritten the default value for every rows, blocks other queries from running.

With Postgres v11, above behavior change.

When adding new columns with default value, the default value is stored in catalog, and being used where needed for existing rows (rows available at the time the change was made). New rows or new version of existing rows filled with default value in place.

The great advantage of this is that adding a column with a default value is now quite a fast and cheap operation, whereas before for very large tables it has been horribly, often intolerably slow. Rewriting a whole multi-terabyte table is really something you want to avoid.



----
https://www.2ndquadrant.com/en/blog/add-new-table-column-default-value-postgresql-11/

