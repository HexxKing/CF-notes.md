# Read: 08 - SQL

## [Complete SQLBolt](https://sqlbolt.com/)

### Intro
- SQL, or Structured Query Language, is a language designed to allow both technical and non-technical users query, manipulate, and transform data from a relational database.
- There are many popular SQL databases including SQLite, MySQL, Postgres, Oracle and Microsoft SQL Server. All of them support the common SQL language standard, which is what this site will be teaching, but each implementation can differ in the additional features and storage types it supports.

### Lessons 1-4
##### Lesson 1
- To retrieve data from a SQL database, we need to write SELECT statements, which are often colloquially refered to as queries. 
  - A query in itself is just a statement which declares what data we are looking for, where to find it in the database, and optionally, how to transform it before it is returned.
  - The most basic query we could write would be one that selects for a couple columns (properties) of the table with all the rows (instances).
- Think of a table in SQL as a type of an entity (ie. Dogs), and each row in that table as a specific instance of that type (ie. A pug, a beagle, a different colored pug, etc). This means that the columns would then represent the common properties shared by all instances of that entity (ie. Color of fur, length of tail, etc).
##### Lesson 2
- As you might have noticed by now, SQL doesn't require you to write the keywords all capitalized, but as a convention, it helps people distinguish SQL keywords from column and tables names, and makes the query easier to read.
- In order to filter certain results from being returned, we need to use a WHERE clause in the query. The clause is applied to each row of data by checking specific column values to determine whether it should be included in the results or not.
- More complex clauses can be constructed by joining numerous AND or OR logical keywords (ie. num_wheels >= 4 AND doors <= 2). 
##### Lesson 3
- When writing WHERE clauses with columns containing text data, SQL supports a number of useful operators to do things like case-insensitive string comparison and wildcard pattern matching. 
- All strings must be quoted so that the query parser can distinguish words in the string from SQL keywords.
##### Lesson 4
- Even though the data in a database may be unique, the results of any particular query may not be. 
  - In such cases, SQL provides a convenient way to discard rows that have a duplicate column value by using the DISTINCT keyword.
- Since the DISTINCT keyword will blindly remove duplicate rows, we will learn in a future lesson how to discard duplicates based on specific columns using grouping and the GROUP BY clause.
##### Ordering results
- Unlike our neatly ordered table in the last few lessons, most data in real databases are added in no particular column order. 
- As a result, it can be difficult to read through and understand the results of a query as the size of a table increases to thousands or even millions rows.
- To help with this, SQL provides a way to sort your results by a given column in ascending or descending order using the ORDER BY clause.
- When an ORDER BY clause is specified, each row is sorted alpha-numerically based on the specified column's value. In some databases, you can also specify a collation to better sort data containing international text.
- Another clause which is commonly used with the ORDER BY clause are the LIMIT and OFFSET clauses, which are a useful optimization to indicate to the database the subset of the results you care about.
- The LIMIT will reduce the number of rows to return, and the optional OFFSET will specify where to begin counting the number rows from.

### Lessons 13-18
##### What is a Schema?
- We previously described a table in a database as a two-dimensional set of rows and columns, with the columns being the properties and the rows being instances of the entity in the table. 
- In SQL, the database schema is what describes the structure of each table, and the datatypes that each column of the table can contain.
- This fixed structure is what allows a database to be efficient, and consistent despite storing millions or even billions of rows.
##### Inserting new data
- When inserting data into a database, we need to use an INSERT statement, which declares which table to write into, the columns of data that we are filling, and one or more rows of data to insert. 
- In general, each row of data you insert should contain values for every corresponding column in the table. You can insert multiple rows at a time by just listing them sequentially.
- In some cases, if you have incomplete data and the table contains columns that support default values, you can insert rows with only the columns of data you have by specifying them explicitly.
  - In these cases, the number of values need to match the number of columns specified. Despite this being a more verbose statement to write, inserting values this way has the benefit of being forward compatible. 
  - For example, if you add a new column to the table with a default value, no hardcoded INSERT statements will have to change as a result to accommodate that change.


In addition, you can use mathematical and string expressions with the values that you are inserting.
This can be useful to ensure that all data inserted is formatted a certain way.
##### Updating Rows
- In addition to adding new data, a common task is to update existing data, which can be done using an UPDATE statement. 
- Similar to the INSERT statement, you have to specify exactly which table, columns, and rows to update. 
- In addition, the data you are updating has to match the data type of the columns in the table schema.
- The statement works by taking multiple column/value pairs, and applying those changes to each and every row that satisfies the constraint in the WHERE clause.
- Most people working with SQL will make mistakes updating data at one point or another. 
  - Whether it's updating the wrong set of rows in a production database, or accidentally leaving out the WHERE clause (which causes the update to apply to all rows), you need to be extra careful when constructing UPDATE statements.
##### Deleting Rows
- When you need to delete data from a table in the database, you can use a DELETE statement, which describes the table to act on, and the rows of the table to delete through the WHERE clause.
- If you decide to leave out the WHERE constraint, then all rows are removed, which is a quick and easy way to clear out a table completely (if intentional).
- Like the UPDATE statement, it's recommended that you run the constraint in a SELECT query first to ensure that you are removing the right rows. 
  - Without a proper backup or test database, it is downright easy to irrevocably remove data, so always read your DELETE statements twice and execute once.
##### Creating Tables
- When you have new entities and relationships to store in your database, you can create a new database table using the CREATE TABLE statement.
- The structure of the new table is defined by its table schema, which defines a series of columns. 
- Each column has a name, the type of data allowed in that column, an optional table constraint on values being inserted, and an optional default value.
- If there already exists a table with the same name, the SQL implementation will usually throw an error, so to suppress the error and skip creating a table if one exists, you can use the IF NOT EXISTS clause.
- Different databases support different data types, but the common types support numeric, string, and other miscellaneous things like dates, booleans, or even binary data.
- Each column can have additional table constraints on it which limit what values can be inserted into that column.
##### Altering Tables
- As your data changes over time, SQL provides a way for you to update your corresponding tables and database schemas by using the ALTER TABLE statement to add, remove, or modify columns and table constraints.
- The syntax for adding a new column is similar to the syntax when creating new rows in the CREATE TABLE statement. 
- You need to specify the data type of the column along with any potential table constraints and default values to be applied to both existing and new rows. 
- In some databases like MySQL, you can even specify where to insert the new column using the FIRST or AFTER clauses, though this is not a standard feature.
- Dropping columns is as easy as specifying the column to drop, however, some databases (including SQLite) don't support this feature. Instead you may have to create a new table and migrate the data over.
- If you need to rename the table itself, you can also do that using the RENAME TO clause of the statement.
##### Dropping Tables
- In some rare cases, you may want to remove an entire table including all of its data and metadata, and to do so, you can use the DROP TABLE statement, which differs from the DELETE statement in that it also removes the table schema from the database entirely.
- Like the CREATE TABLE statement, the database may throw an error if the specified table does not exist, and to suppress that error, you can use the IF EXISTS clause.
- In addition, if you have another table that is dependent on columns in table you are removing (for example, with a FOREIGN KEY dependency) then you will have to either update all dependent tables first to remove the dependent rows or to remove those tables entirely.

## [Practice SQL on W3 Schools](https://www.w3schools.com/sql/trysql.asp?filename=trysql_select_all)
- This resource has sample databases you can use to practice writing SQL queries.

## [A Primer on SQL](https://openlibra.com/en/book/a-primer-on-sql-3rd-edition)
- this is a downloadble book

## [Sql Cheat Sheet](http://www.cheat-sheets.org/sites/sql.su/)