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


[Back](README.md)