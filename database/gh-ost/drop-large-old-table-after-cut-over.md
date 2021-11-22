- When you're running innodb_file_per_table=1, dropping a table issueing dropping tablespace, and InnoDB has to go through LRU lists and discard the pages which belong to the tablespace. This can take a lot of time with large buffer pool. Worst of all this is done while table_cache lock is being held so no other queries can start.

- 
------------------------
[1] http://code.openark.org/blog/mysql/the-problem-with-mysql-foreign-key-constraints-in-online-schema-changes
[2] https://vitess.io/blog/2021-06-15-online-ddl-why-no-fk/
[3] https://github.com/vitessio/vitess/issues/6689