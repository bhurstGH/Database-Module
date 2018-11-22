# Database-Module
Bloc Database module, Checkpoint 1.

>What data types do each of these values represent?

A: These somewhat depend on how you want to define them and which database server you are using, but in general: 

1. "A Clockwork Orange" : A string.
2. 42: An integer.
3. 09/02/1945: A form of date. Though it could be a string, since from what I have seen SQL tends to format dates as 09-02-1945, with dashes rather thab slashes.
4. 98.7: A float.
5. $15.99: Money or a float.

>Explain when a database would be used. Explain when a text be used.

A: A database would need to be used for persistent, possibly online data that handles asynchronous queries, including updates and deletes. For things like store inventories, user accounts, or anything else that needs to be organized and quickly accessible by a program and its users. Particularly though not necessarily very large data sets.

A text file could be used for many of the same purposes but is not purpose-built for them. It also cannot easily handle the asynchronicity of multiple incoming queries like a database is able to do. It is prone to failures and collisions in this way. They can be useful for more local purposes, like a users preferred settings, or for data that needs to be human readable. A text file could also work hand in hand with databases in a scenario where you may query a larger database for data and store the query as a text file, like JSON, for manipulation in a user's session. This technique could be used to cut down on the number of database queries and to work on the data in a manner that is nondestructive to the database.

>Describe the difference between SQL and other programming languages.

A: SQL is specifically designed for querying databases and is declarative. It can almost read as plain English once you understand the query structure.

>In your own words, explain how the pieces of a database system fit together at a high level.

A: A database is an application that forms relationships between tables and the data within them in a binary file format. Data is any piece of information that we need to store or manipulate and access at a later time, particularly outside of a program's runtime. The data in each table column should share a type (such as text or integer) and the data in the columns form rows or records that have a relationship.

Using the SQL language, the database application or outside sources (such as a program you are writing, or perhaps a web API so others can access your database) can request the data from the tables. SQL allows you to conditionally retrieve and display data from one or more tables as well as make changes (updates or deletions, for example) as needed.

Databases and SQL provide a paradoxical combination of data stored in a non-human readable format that can be retrieved in a very declarative, human readable way, very quickly.

_old answer_ A database is a collection of columns and rows of related data. Each column contains a certain type of data and the rows (or records) are a collection of column data that represents an object or entity, such as a person, order, or item information.

>Explain the meaning of table, row, column, and value.

A: A table is the object containing the columns and rows. A column is represented as a vertical collection of data of a certain type. A row is represented as a horizontal collection of column data. A value the data stored in an individual cell at a cross-section of a column and row.

>List three types of data that can be used in a table.

A: Strings, integers, and floats.

>Given the payments table, provide an English description of the following queries and include their results.

`SELECT date, amount FROM payments;`

A: Return the date and amount columns from the payments table.

**Query #1**

    SELECT date, amount FROM payments;

| date                     | amount    |
| ------------------------ | --------- |
| 2016-05-01T00:00:00.000Z | 1500.0000 |
| 2016-05-10T00:00:00.000Z | 37.0000   |
| 2016-05-15T00:00:00.000Z | 124.9300  |
| 2016-05-23T00:00:00.000Z | 54.7200   |


`SELECT amount FROM payments WHERE amount > 500;`

A: Return the amount column from the payments table with only the records where the payment was greater than 500.

**Query #1**

    SELECT amount from payments where amount > 500;

| amount    |
| --------- |
| 1500.0000 |


`SELECT * FROM payments WHERE payee = 'Mega Foods';`

A: Return all records from the payments table where the payee was Mega Foods.

**Query #1**

    select * from payments where payee = 'Mega Foods';

| date                     | payee      | amount   | memo      |
| ------------------------ | ---------- | -------- | --------- |
| 2016-05-15T00:00:00.000Z | Mega Foods | 124.9300 | Groceries |

>Given this users table, write SQL queries using the following criteria and include the output:

>The email and sign-up date for the user named DeAndre Data.

---

**Query #1**

    SELECT email, signup
    FROM users
    WHERE name = 'DeAndre Data';

| email             | signup                   |
| ----------------- | ------------------------ |
| datad@comcast.net | 2008-01-20T00:00:00.000Z |


>The user ID for the user with email 'aleesia.algorithm@uw.edu'.

---

**Query #1**

    SELECT userid
    FROM users
    WHERE email = 'aleesia.algorithm@uw.edu';

| userid |
| ------ |
| 1      |

>All the columns for the user ID equal to 4.

**Query #1**

    SELECT *
    FROM users
    WHERE userid = 4;

| userid | name           | email             | signup                   |
| ------ | -------------- | ----------------- | ------------------------ |
| 4      | Brandy Boolean | bboolean@nasa.gov | 1999-10-15T00:00:00.000Z |
