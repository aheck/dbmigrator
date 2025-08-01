# dbmigrator

This tool applies database migrations written as SQL (DDL) files to a
MySQL database. The SQL files need to be in the same directory and they need to
be numbered with names like `1.sql`, `2.sql`, `3.sql` and so on.

The version of the database is stored in a table named `tbl_schema_version`.
This table will be automatically created by the program when it runs against
a certain database for the first time.

Whenever you run the program it will get the schema version of your database
and check if there are SQL files in the migrations directory with newer schema
numbers in their filenames. If this is the case, the program will try to apply
them in the order of their schema version number. Whenever a file is applied
sucessfully the version number in `tbl_schema_version` is raised to the now
current schema version.

# Environment Variables

To run the program you have to set the following environment variables:

| Environment Variable | Description                                 |
|----------------------|---------------------------------------------|
| `DB_HOST`            | The hostname or IP address of the database server  |
| `DB_PORT`            | The port number used to connect to the database    |
| `DB_NAME`            | The name of the database to connect to            |
| `DB_USER`            | The username for the database connection          |
| `DB_PASS`            | The password for the database connection          |
| `DB_MIGRATIONS_DIR`  | The directory with the numbered SQL files         |
