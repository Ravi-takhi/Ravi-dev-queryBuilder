# Intoduction
## Project Name: queryBuilder
SqlKata Query Builder is a powerful Sql Query Builder written in C#. It's secure and framework agnostic. Inspired by the top Query Builders available, like Laravel Query Builder and Knex.SqlKata has an expressive API. it follows a clean naming convention, which is very similar to the SQL syntax. By providing a level of abstraction over the supported database engines, that allows you to work with multiple databases with the same unified API. SqlKata supports complex queries, such as nested conditions, selection from SubQuery, filtering over SubQueries, Conditional Statements and others. Currently, it has built-in compilers for SqlServer, MySql, PostgreSQL, and Firebird.

Checkout the full documentation on https://sqlkata.com
### Link
https://github.com/Ravi-takhi/Ravi-dev-queryBuilder/tree/Ravi-dev-branch
### Summary of issues examined
This [issue](https://github.com/sqlkata/querybuilder/issues/641), raised by H0nok4 on Nov 17, 2022, The person is having trouble with doing an "insert or replace" action in SQLite. They're finding it tricky to insert new data or replace existing data in the table at the same time. They're looking for a straightforward way to solve this problem in SQLite.
### Detailed discussion of issues contributed to
The person is asking about how to handle inserting or updating data in their SQLite database. They want to update the data if a key already exists. After checking the documentation for SqlKata and finding no solution, they looked into SQLite's documentation and found some helpful information. They want to refer to the SQLite language documentation available at: https://www.sqlite.org/lang.html
### Solution
#### Introduction to the SQLite REPLACE statement
The REPLACE statement works by executing two steps when a UNIQUE or PRIMARY KEY constraint violation happens:
* Initially, it removes the existing row that triggers the constraint violation.
* Then, it proceeds to insert a new row in its place.
#### Syntax of the REPLACE statement
``` sql
INSERT OR REPLACE INTO table(column_list)
VALUES(value_list);
```
#### Example of INSERT OR REPLACE students data
1. First, assuming you have a table named "students" with columns "id" (primary key), "name", and "age".
``` sql
CREATE TABLE IF NOT EXISTS students (
    id INTEGER PRIMARY KEY,
    name TEXT NOT NULL,
    age INTEGER
);
```
2. Then, you can use the following SQL statement to update or insert student records
``` sql
INSERT OR REPLACE INTO students (id, name, age)
VALUES 
    (1, 'Ravi', 20),  -- Assuming student with id 1 already exists, this will update Ravi's record
    (2, 'Kuljit', 22), -- Assuming student with id 2 doesn't exist, this will insert a new record for Kuljit
    (3, 'Monika', 21); -- Assuming student with id 3 doesn't exist, this will insert a new record for Monika
```
