# Intoduction
## Project Name: queryBuilder
SqlKata Query Builder is a powerful Sql Query Builder written in C#. It's secure and framework agnostic. Inspired by the top Query Builders available, like Laravel Query Builder and Knex.SqlKata has an expressive API. it follows a clean naming convention, which is very similar to the SQL syntax. By providing a level of abstraction over the supported database engines, that allows you to work with multiple databases with the same unified API. SqlKata supports complex queries, such as nested conditions, selection from SubQuery, filtering over SubQueries, Conditional Statements and others. Currently, it has built-in compilers for SqlServer, MySql, PostgreSQL, and Firebird.

The full documentation is avaiable on https://sqlkata.com
### Link
https://github.com/Ravi-takhi/Ravi-dev-queryBuilder/tree/Ravi-dev-branch
### Summary of issues examined
This [issue](https://github.com/sqlkata/querybuilder/issues/641), raised by H0nok4 on Nov 17, 2022, The person is having trouble with doing an "insert or replace" action in SQLite. They're finding it tricky to insert new data or replace existing data in the table at the same time. They're looking for a straightforward way to solve this problem in SQLite.
### Detailed discussion of issues contributed to
The person is asking about how to handle inserting or updating data in their SQLite database. They want to update the data if a key already exists. After checking the documentation for SqlKata and finding no solution, they looked into SQLite's documentation and found some helpful information. I refer to the SQLite language documentation available at: https://www.sqlite.org/lang.html
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
### Code review and outcomes
#### Code review
Kuljit has reviwed my code and shared some feedback points for making a table called "students" and putting in new information or updating existing information. She thought the way I made the table was good, with rules to keep the data organized. Using "INSERT OR REPLACE INTO" was smart because it either adds new info or changes old info if it's already there. The comments you wrote next to each new piece of information helped to understand what's going on. However, She suggested adding another part to the code before updating the records. This part would put some initial information into the table right after creating it. Doing this would help people see how the table works and how the updates happen. Kuljit also thought the code was easy to understand overall.
#### Outcome
After Kuljit's review of my code for creating and updating the "students" table, it's clear that the initial structure and approach were well-received. The thoughtful organization of the table and the use of "INSERT OR REPLACE INTO" for updating records were noted as smart choices. Additionally, the inclusion of explanatory comments alongside each piece of data was appreciated for enhancing clarity.

Kuljit's suggestion to add an initial data insertion step before updating records is insightful. This addition would provide a practical demonstration of the table's functionality, aiding in understanding for future developers. Overall, the feedback highlights the code's overall clarity and effectiveness, with the proposed improvement serving to further enhance its comprehensibility and utility.
### Updated version
1. First, assuming you have a table named "students" with columns "id" (primary key), "name", and "age".
``` sql
CREATE TABLE IF NOT EXISTS students (
    id INTEGER PRIMARY KEY,
    name TEXT NOT NULL,
    age INTEGER
);
```
2. Add the sudents data in table using the insert query.
```sql
INSERT INTO students (name, age)
VALUES 
    ('Ravi', 20);

```
3. Then, you can use the following SQL statement to update or insert student records
``` sql
INSERT OR REPLACE INTO students (id, name, age)
VALUES 
    (1, 'Ravi', 20),  -- Assuming student with id 1 already exists, this will update Ravi's record
    (2, 'Kuljit', 22), -- Assuming student with id 2 doesn't exist, this will insert a new record for Kuljit
    (3, 'Monika', 21); -- Assuming student with id 3 doesn't exist, this will insert a new record for Monika
```
### Reflection
Overall, I feel like I did a good job solving the problem. Someone needed help with the "insert or replace" query in SQL, so I did some research. I found a solution by creating a table first and then updating the data using the "insert or replace" query. After getting feedback from Kuljit, I added another step to add the data before updating it. This made the code easier to understand for everyone.
### References
* https://www.sqlitetutorial.net/sqlite-replace-statement/
