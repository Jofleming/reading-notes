# Sql Reading

Making queries with constraints uses the form of:

```
Select query with constraints
SELECT column, another_column, …
FROM mytable
WHERE condition
    AND/OR another_condition
    AND/OR …;
```


## Operators:

* `=, !=, < <=, >, >=` - Standard numerical operators - Ex. `col_name != 4`
* `BETWEEN … AND …` - Number is within range of two values (inclusive) - Ex. `col_name BETWEEN 1.5 AND 10.5`
* `NOT BETWEEN … AND …` - Number is not within range of two values (inclusive) - Ex. `col_name NOT BETWEEN 1 AND 10`
* `IN (…)` - Number exists in a list - Ex. `col_name IN (2, 4, 6)`
* `NOT IN (…)` - Number does not exist in a list - Ex. `col_name NOT IN (1, 3, 5)`
* `=` - Case sensitive exact string comparison (notice the single equals) - Ex. `col_name = "abc"`
* `!= or <>` - Case sensitive exact string inequality comparison - Ex. `col_name != "abcd"`
* `LIKE` - Case insensitive exact string comparison - Ex. `col_name LIKE "ABC"`
* `NOT LIKE` - Case insensitive exact string inequality comparison - Ex. `col_name NOT LIKE "ABCD"`
* `%` - Used anywhere in a string to match a sequence of zero or more characters (only with LIKE or NOT LIKE)
* `_` - Used anywhere in a string to match a single character (only with LIKE or NOT LIKE)
* `IN (…)` - String exists in a list
* `NOT IN (…)` - String does not exist in a list

## FIltering and sorting

In most real databases, data is added in no particular column order. To help you can use the `ORDER BY` clause.

```
SELECT column, another_column, …
FROM mytable
WHERE condition(s)
ORDER BY column ASC/DESC;
```

When an order by clause is specified, each row is sorta alpha-numerically based on the specified column's value.

Along with the `ORDER BY` clause you can use the `LIMIT` and `OFFSET` clauses. Limit will reduce the number of rows to return, and the optional offset will specify where to begin counting the number rows from.

## Multi-tables queries with JOINS

Tables that share info about a single entity need to have a 'primary key' that identifies that entity uniquely across the database. One common primary key type is an auto-incrmenting integer, but it can also be a string, hashed value, so long as it is unique.

The `JOIN` clause can be used in a query to combine row data across two separate tables using the unique key. First touched on is the `INNER JOIN`

```
SELECT column, another_table_column, …
FROM mytable
INNER JOIN another_table 
    ON mytable.id = another_table.id
WHERE condition(s)
ORDER BY column, … ASC/DESC
LIMIT num_limit OFFSET num_offset;
```

The `INNER JOIN` is a process that matches rows from the first table and the second table which have the same key (as defined by the ON constraint) to create a result row with the combined columns from both tables. After the tables are joined, the other clauses we learned previously are then applied.

If the two tables have asymmetric data, which can easily happen when data is entered in different stages, then we would have to use a `LEFT JOIN`, `RIGHT JOIN` or `FULL JOIN` instead to ensure that the data you need is not left out of the results.

```
SELECT column, another_column, …
FROM mytable
INNER/LEFT/RIGHT/FULL JOIN another_table 
    ON mytable.id = another_table.matching_id
WHERE condition(s)
ORDER BY column, … ASC/DESC
LIMIT num_limit OFFSET num_offset;
```

## Queries with expressions

In addition to querying and referencing raw column data with SQL, you can also use expressions to write more complex logic on column values in a query. These expressions can use mathematical and string functions along with basic arithmetic to transform values when the query is executed, as shown in this physics example.

```
SELECT particle_speed / 2.0 AS half_particle_speed
FROM physics_data
WHERE ABS(particle_position) * 10.0 > 500;
```

Each database has its own supported set of mathematical, string, and date functions that can be used in a query, which you can find in their own respective docs.

The use of expressions can save time and extra post-processing of the result data, but can also make the query harder to read, so we recommend that when expressions are used in the SELECT part of the query, that they are also given a descriptive alias using the AS keyword.

The AS keyword can be used at any time, not only with expressions.

## Queries with aggregates

`HAVING` is used specifically with the `GROUP BY` clause. This allows us to filter grouped rows from the result set.

```
SELECT group_by_column, AGG_FUNC(column_expression) AS aggregate_result_alias, …
FROM mytable
WHERE condition
GROUP BY column
HAVING group_condition;
```

The `HAVING` clause constraints are written the same way as the `WHERE` clause constraints, and are applied to the grouped rows. With our examples, this might not seem like a particularly useful construct, but if you imagine data with millions of rows with different properties, being able to apply additional constraints is often necessary to quickly make sense of the data.

If you are not using the `GROUP BY` clause then a simple `WHERE` clause will work.

## Order of Execution of a Query

1. `FROM` and `JOIN`S
    The `FROM` clause, and subsequent `JOIN`s are first executed to determine the total working set of data that is being queried. This includes subqueries in this clause, and can cause temporary tables to be created under the hood containing all the columns and rows of the tables being joined.
2. `WHERE`
    Once we have the total working set of data, the first-pass `WHERE` constraints are applied to the individual rows, and rows that do not satisfy the constraint are discarded. Each of the constraints can only access columns directly from the tables requested in the `FROM` clause. Aliases in the `SELECT` part of the query are not accessible in most databases since they may include expressions dependent on parts of the query that have not yet executed.
3. `GROUP BY`
    The remaining rows after the `WHERE` constraints are applied are then grouped based on common values in the column specified in the `GROUP BY` clause. As a result of the grouping, there will only be as many rows as there are unique values in that column. Implicitly, this means that you should only need to use this when you have aggregate functions in your query.
4. `HAVING`
    If the query has a `GROUP BY` clause, then the constraints in the `HAVING` clause are then applied to the grouped rows, discard the grouped rows that don't satisfy the constraint. Like the `WHERE` clause, aliases are also not accessible from this step in most databases.
5. `SELECT`
    Any expressions in the `SELECT` part of the query are finally computed.
6. `DISTINCT`
    Of the remaining rows, rows with duplicate values in the column marked as `DISTINCT` will be discarded.
7. `ORDER BY`
    If an order is specified by the `ORDER BY` clause, the rows are then sorted by the specified data in either ascending or descending order. Since all the expressions in the `SELECT` part of the query have been computed, you can reference aliases in this clause.
8. `LIMIT` / `OFFSET`
    Finally, the rows that fall outside the range specified by the `LIMIT` and `OFFSET` are discarded, leaving the final set of rows to be returned from the query.


## Inserting Rows

When inserting data into a database, we need to use an `INSERT` statement, which declares which table to write into, the columns of data that we are filling, and one or more rows of data to insert. In general, each row of data you insert should contain values for every corresponding column in the table. You can insert multiple rows at a time by just listing them sequentially.

```
INSERT INTO mytable
(column, another_column, …)
VALUES (value_or_expr, another_value_or_expr, …),
      (value_or_expr_2, another_value_or_expr_2, …),
      …;
```

Example:
```
INSERT INTO boxoffice
(movie_id, rating, sales_in_millions)
VALUES (1, 9.9, 283742034 / 1000000);
```

## Updating Rows

In addition to adding new data, a common task is to update existing data, which can be done using an `UPDATE` statement. Similar to the `INSERT` statement, you have to specify exactly which table, columns, and rows to update. In addition, the data you are updating has to match the data type of the columns in the table schema.

```
UPDATE mytable
SET column = value_or_expr, 
    other_column = another_value_or_expr, 
    …
WHERE condition;
```

Most people working with SQL will make mistakes updating data at one point or another. Whether it's updating the wrong set of rows in a production database, or accidentally leaving out the `WHERE` clause (which causes the update to apply to all rows), you need to be extra careful when constructing `UPDATE` statements.

One helpful tip is to always write the constraint first and test it in a `SELECT` query to make sure you are updating the right rows, and only then writing the column/value pairs to update.

Exercise Solution:
```
UPDATE movies
SET title = "Toy Story 3", director = "Lee Unkrich"
WHERE id = 11;
```

## Deleting Rows

When you need to delete data from a table in the database, you can use a `DELETE` statement, which describes the table to act on, and the rows of the table to delete through the `WHERE` clause.

If you decide to leave out the `WHERE` constraint, then all rows are removed, which is a quick and easy way to clear out a table completely (if intentional).

## Creating Tables

The structure of the new table is defined by its table schema, which defines a series of columns. Each column has a name, the type of data allowed in that column, an optional table constraint on values being inserted, and an optional default value.

If there already exists a table with the same name, the SQL implementation will usually throw an error, so to suppress the error and skip creating a table if one exists, you can use the `IF NOT EXISTS` clause.


Data types
`INTEGER, BOOLEAN` - The integer datatypes can store whole integer values like the count of a number or an age. In some implementations, the boolean value is just represented as an integer value of just 0 or 1.

`FLOAT, DOUBLE, REAL` - The floating point datatypes can store more precise numerical data like measurements or fractional values. Different types can be used depending on the floating point precision required for that value.

`CHARACTER(num_chars), VARCHAR(num_chars), TEXT` - The text based datatypes can store strings and text in all sorts of locales. The distinction between the various types generally amount to underlaying efficiency of the database when working with these columns.

Both the `CHARACTER` and `VARCHAR` (variable character) types are specified with the max number of characters that they can store (longer values may be truncated), so can be more efficient to store and query with big tables.

`DATE, DATETIME` - SQL can also store date and time stamps to keep track of time series and event data. They can be tricky to work with especially when manipulating data across timezones.

`BLOB` - Finally, SQL can store binary data in blobs right in the database. These values are often opaque to the database, so you usually have to store them with the right metadata to requery them.

Table Constraints

`PRIMARY KEY` - This means that the values in this column are unique, and each value can be used to identify a single row in this table.

`AUTOINCREMENT` - For integer values, this means that the value is automatically filled in and incremented with each row insertion. Not supported in all databases.

`UNIQUE` - This means that the values in this column have to be unique, so you can't insert another row with the same value in this column as another row in the table. Differs from the `PRIMARY KEY` in that it doesn't have to be a key for a row in the table.

`NOT NULL` - This means that the inserted value can not be `NULL`.

`CHECK (expression)` - This allows you to run a more complex expression to test whether the values inserted are valid. For example, you can check that values are positive, or greater than a specific size, or start with a certain prefix, etc.

`FOREIGN KEY` - This is a consistency check which ensures that each value in this column corresponds to another value in a column in another table.

For example, if there are two tables, one listing all Employees by ID, and another listing their payroll information, the `FOREIGN KEY` can ensure that every row in the payroll table corresponds to a valid employee in the master Employee list.

EXAMPLE:
```
CREATE TABLE movies (
    id INTEGER PRIMARY KEY,
    title TEXT,
    director TEXT,
    year INTEGER, 
    length_minutes INTEGER
);
```

[Back](README.md)