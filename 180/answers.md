## SQL and Relationship Database

1. What is relational database? include these terms in answer and do a lucid description of these terms
- relational model
- RDBMS
- SQL

A relational database is a database based on the relational model of data. A software system used to maintain relational database is call Relational Database Management System(RDBMS). In practice all RDBMS use SQL to operate relational database.

- Relational model organizes data into one or more tables(relaitons) of columns and rows, with an unique key identifying each row. Rows are also called records, columns are also called attributes. Generally each table(relation) represents one "[entity](https://en.wikipedia.org/wiki/Associative_entity) type".
- RDBMS is software/application used to maintain relational database
- SQL stands for standard query language, it's the language used by RDBMS to query and manipulate data in database.

2. What's the difference among:
- PostgreSQL client application(`createdb`, `psql`, `dropdb`)
  - these are commands/applications built for PostgreSQL, actually some of them are just wrappers of SQL, and can be seen as abstractions of SQL. The presence of client application is to simplify certain operations which may be tedious by using SQL sentence.
- meta-commands(`\c db_name`, `\list`)
  - they are specific to a PostgreSQL client application `psql`, in `psql` console we use meta-commands to perform some high level tasks like list all database managed by postgresql or view the schema of specific table.
- SQL
  - SQL is the language used by all relational database to operate the database.

3. What is the sign of the end of an sql statement?

A semicolon.

4. How to perform these operations by using postgresql client applications

- set up
  - how to create a database with a given name
    - `createdb db_name`
  - what is the extension name of a file that we write sql statements in?
    - `.sql`
  - how to import an external `.sql` file into an existent database?
    - in terminal: `psql -d db_name < file_name.sql`
    - in psql console: `\i ~/path/to/file/file_name.sql` (1.need to connect to target databse; 2.need absolute path)

- connect
  - how to connect to a database locally?
    - in terminal: `psql -d db_name`
    - in psql console: `\c db_name`
  - what does `-d` flag means in a `psql` Meta-commands(check `psql --help`)
    -  -d, --dbname=DBNAME  database name to connect to (default: "xullnn") `psql -d db_name` means enter the database named `db_name` owned by user `"Xullnn"` via psql console

5. how to select one or more columns from a table? how to separate the names of columns

Type one or more column names after `SELECT`, separate them with commas. For example `SELECT col_1, col_2, col_3 FROM tb_name;`

6. what's the means of database usually used to label a specific row? or say what will be used as unique identifier to a row?

Normally we use a column called `id` which holds non-empty, unique, integer values to identify each row.

7. what should be written before and after the `=` in sql statement? what is the difference on meaning of this in sql and programing language like Ruby.

In SQL `=` can be used in `WHERE` clause or to update data
  - in SQL
    - `SELECT col_1 FROM tb_name WHERE id = 3;`. Here the `=` is a comparison operator used to compare each row's value of the `id` column the integer `3` and returns a boolean value.
    - `UPDATE tb_name SET(id = 1);` Here the `=` is no longer a comparison operator, it's used to update the values of the column `id`.
  - in Ruby
    - `=` can be used to perform [assignment](http://ruby-doc.org/core-2.6.2/doc/syntax/assignment_rdoc.html) (e.g to assign value to a local variable `var = 3`)
    - `=` can also be part of a method name(e.g `Person.new.name =` , `name=` is the name of the method)

8. What is the schema of a database?

The [schema of a database](https://en.wikipedia.org/wiki/Database_schema) can be simply understood as the structure of a database. The term "schema" refers to the organization of data as a blueprint of how the database is constructed (divided into database tables in the case of relational databases).

9. What is the data of a database?

Is the information/data content we want to store into database.

10. What is the relationship between schema and database, database and data?

- schema defines the structure of database
- database provide structured space to hold data

11. What sub-languages of SQL will be used to handle schema and data?

- DDL: Data Define Language
- DML: Data Manipulation Language
- DCL: Data Control Language

12. What DDL handles about within a database? What things DDL will not touch in a database?

DDL handles the schema of database and tables. If a SQL statement touches(CRUD) the data content in a database then it's not DDL.

13. How to create a new PostgreSQL database from terminal? And how to do so in psql console?

- terminal: `createdb db_name`
- psql console: `CREATE DATABASE db_name;`

14. How to connect to another database in psql console?

`\c db_name`

15. If your psql prompt is `another_database=#`, and you want to delete the `another_database` database, how to do it? Two ways!

- exit psql console by execute `\q` then perform `dropdb db_name`
- or in psql console
  - first switch to another database `\c another_database`
  - perform SQL `DROP DATABASE db_name;` (don't forget semicolon)

16. Point out the different components in this sql statement, which of these components are required.

```
sample_db=# CREATE TABLE users (
  id serial UNIQUE NOT NULL,
  username CHAR(25)
  );
```

- `sample_db=#` means we are now connecting to `sample_db` database
- `CREATE TABLE` is SQL key words used to create a new table
  - `users` is the table name
  - the 2 lines of code in first parentheses defines the schema of the table
    - `id` and `username` are column names
    - `serial` and `CHAR(25)` indicate the type for each column
    - `UNIQUE NOT NULL` is 2 constraints `UNIQUE` and `NOT NULL` that are imposed to the first column by us.
- `;` indicates the end of the SQL statement.

17. Could constraints only be at table column level?

- Not exactly. Constraints can be both added to database level or table level.

18. Why we need constraints?

To keep the integrity and consistency of data and the relationships between tables in a database.

19. How to view these things in psql console
  - all databases on your local machine
    - `\list`
  - all relations in a database in psql console?
    - `\d`
  - all tables in a database in psql console?
    - `\dt`
  - all sequences
    - `\ds`

20. How to check the schema of a specific table?

`\d table_name`

21. Is the 'security settings'(controlled by DCL) of a database part of its schema?

Yes.

22. If part an sql statement is `(weight DECIMAL(8, 2))` what's the meaning of `8` and `2`? What the max and minimal value for this column?

- `weight` is the name of the column
- `DECIMAL` indicates the type of column is an arbitrary decimal number with a specified precision and scale
  - `8` is called precision, it confines the total number of digits in this column
  - `2` is called scale, it confines the number of digits on the right side of the decimal point
  - in this case the number range is (-999999.99 to 999999.99) if negative allowed

23. What's in common on all below syntax?

- rename a table
- rename a column
- change a column's datatype
- adding a constraint(can we alter a constraint? like change `varchar(25)` to `varchar(50)`)
- removing a constraint
- adding a column
- removing a column

They all start with `ALTER TABLE`

24. What are the four types of Data Manipulation Statements?

CRUD, create, read, update, delete

25. What is the syntax of inserting data?

```sql
INSERT INTO table_name (col_1, col_2, col_n)
  VALUES
  (v_1, v_2, v3),
  (v_1_1, v_2_2, v_3_3);
```

26. How to add a `CHECK` constraint to a column to let it can't be inserted into empty string?

```sql
ALTER TABLE table_name ADD CHECK (check_expression); --
  --  `check_expression` can be things like `id < 9999`
ALTER TABLE table_name ADD CONSTRAINT check_name CHECK (check_expression);
  -- same results of the previous one but with an specified constraint name `id_limit`
```

In this case, check_expression may be `trim(both from name, ' ') != ''`

Notice here we can't use the syntax `SET` to add a `CHECK` to a column. If we want to add a `CHECK` constraint to a column we can:
- add constraint while creating table
- add constraint use table level syntax(as in the above example)

The syntax `SET` can only used to add constraints like `UNIQUE` and `NOT NULL`.(e.g `ALTER TABLE table_name ALTER COLUMN column_name SET UNIQUE;`)

27. What's the alternative syntax of `<>` in SQL?

`!=`

28. How to insert string `'O' Sullivan'` into a table?

In SQL string is wrapped by single quotation, we need to use single quotation mark `'` to escape single quotation in a string. Double quation is used to escape arguments whose name collide with the SQL key words.

29. What would cause a "Three State Boolean problem or Three Valued-logic problem" ?

Allow `NULL` in a boolean type column. If we did so the column can contain 3 values:
- true
- false
- NULL

Then if we choose values that is not true (e.g `paid != true`), the results will contain rows who have `NULL` and rows that are `false`,  and vice versa. We have to add another logic expression to exclude rows with `NULL`(`paid != true AND paid IS NOT NULL`).

30. What's the difference between `char` and `varchar` type when we use match pattern to match content in certain column(s)?

They are both character type, and accept an argument to confine the number of characters the column can hold(e.g `char(20)` or `varchar(20)`). The difference is:
- if the inserted string is less than 20 chars, `char(20)` will pad the remaining spaces with white spaces
- but `varchar(20)` only take the spaces needed

Therefore, if we store `Lee` both in a `varchar(5)` and `char(5)` column
- to match string in `varchar(5)`, we only need `name LIKE 'Lee'`
- but in `char(5)` we need `Lee%`

```
auction=# select 'Lee'::char(5) like 'Lee';
 ?column?
----------
 f
(1 row)

auction=# select 'Lee'::varchar(5) like 'Lee';
 ?column?
----------
 t
(1 row)
```

31. If you have a column named just as one of reserved words in SQL, how could you handle this?

Quote it with double quotation.

32. If we order query results by a boolean column in ascending order, which ones would be listed first?

When ordering by boolean values, `false` comes before `true` in ascending order.

33. What is the sort logic which contains multiple sorting conditions, like:

```
SELECT * FROM users ORDER BY activated ASC, id DESC;
```

- first sort by `activated ASC`
- if the sort results contains rows which have the same value, then sort these rows by `id DESC`

34. Operators are used in which clause in SQL Query?

In `WHERE` clause.

35. What are the main 3 types of operator in SELECT query?

- comparison operator (`=`, `>=` ...)
- logic operator (`OR` `AND`...)
- string matching operator

36. The meaning of `"predicates"` in Grammar can be seen as "the part of a sentence that is other than the subject". What's `comparison predicates` in `WHERE` clause?

- subject, verb, object
  - `id = 2`
  - `id IS NOT NULL`

The part except the left side of the `=`, in above example, is `= 2` and ` IS NOT NULL`

37. How to get all rows of whose certain column is `NULL`?

Use `IS NULL` as comparison predicates.

38. Choose logical operator for each word:
- either `OR`
- both `AND`
- other than `NOT`

39. What is the wild card character in a SQL to match string?

Percent sign.

40. What's the key word used for string matching?

`LIKE`, or `ILIKE`(case insensitive)

41. How to match all user names whose name contains `Lee`. like `Mary Lee. S`, `Lee Jhon`, `Wu Lee.` in a `char(15)` column?

`SELECT name FROM table_name WHERE name LIKE '%Lee%';`

42. What's the basic syntax of updating row(s) in a table?

`UPDATE table_name SET (col_1 = 'some value') WHERE id = 2;`

43. What would happen if we omit the `WHERE` clause potion of our updating statement?

All the rows will be updated.

44. What's the basic syntax to delete row(s) in a table?

`DELETE FROM table_name WHERE id = 2;`

45. What would happen if we omit the `WHERE` clause potion of our deleting statement?

All rows will be deleted.

46. What is normalization of database?

The process of splitting up data to remove duplication and improve data integrity is known as normalization.

47. Why we need normalization?

The reason for normalization is to reduce data redundancy and improve data integrity.

48. what's the mechanism for carrying out normalization?

The mechanism for carrying out normalization is arranging data in multiple tables and defining relationships between them.

49. How you understand entities and relationships in database design?

Entity is a mental model of a noun such as `order`, `book` or `user`. In database we can use name of columns to represent the attributes of the entity, and each row of data represents an instance of that entity.

Relationship describes how different entities relate to each other.

50. What is an Entity Relationship Diagram?

It's a diagram use the name of entities and crow's foot notation to draw out the relationships among entities.

51. What is primary and foreign key, what are they used for?

In the context of database, key is a concept that used to reference a certain row of data. More specifically

- Primary key is a key used as an unique identifier for a single row, we can locate a row of data by using primary key of the table.
- Unlike primary key, foreign key references row of data from another table.
- Primary key and foreign key is the way how we implement the relationship between relations.

52. What's the meaning of referential integrity?

The need to keep data integrity across tables within a relationship. Or say prevent a foreign key column from containing(referencing) a non-existent record in relevant table.

53. Why we need `ON DELETE` clause, how it relates to referential integrity?

`ON DELETE` usually follows `FOREIGN KEY()` constraint to say that "when the referenced record of another table is deleted, delete this corresponding row in this table either.". It's a way to implement referential integrity.

54. What a cross-reference table(join table) be used for?

Used to implement a many-to-many relationship.

55. What's the basic syntax of join tables?

`SELECT col_1, col_2 FROM table_1 JOIN table_2 ON table_1.pkey = table_2.fkey WHERE col_1 LIKE 'Lee%';`

56. What's the difference between `INNER JOIN`, `LEFT OUTER JOIN`, `RIGHT OUTER JOIN`, `FULL JOIN`, and `CROSS JOIN`, which two of them are less used?

- INNER JOIN only joins rows matched the condition from all table, we can understand it as 'intersection'
- LEFT OUTER JOIN joins rows with the intersection part plus remaining rows from the first(left) table with the empty fields filled with `NULL`
- RIGHT OUTER JOIN is similar to LEFT but keeps all rows in the second(right) table
- FULL JOIN first get the intersection of all tables, then plus all the remaining rows of all tables, also fill all empty fields with `NULL`. It can be understood as the union of all rows from all tables
- CROSS JOIN is different from the above ones, it don't need a `ON` condition to specify the join condition. It perform combination across all rows of all tables.

57. What's the syntax of table name aliasing in SQL?(and shorthand form)

`SELECT t.name FROM table_1 AS t;`

We can omit `AS`

`SELECT t.name FROM table_1 t;`

58. What's the syntax of column name aliasing in SQL?

`SELECT first_name AS name FROM table_1;`

59. What's subquery in SQL? Take the below example to explain:

```sql
SELECT u.full_name FROM users u
WHERE u.id NOT IN (SELECT c.user_id FROM checkouts c);
```

A Subquery or Inner query or a Nested query is a query within another SQL query.

In the above example the result of `(SELECT c.user_id FROM checkouts c)` will serve as the further query condition of the main query.

60. In some situations, can JOINs and subqueries interchangeable?

Yes. Most queries can have multiple ways to accomplish.

61. Does SQL only handle data in databases?

Not exactly, the DDL and DCL part won't touch actual data.

62. What is bit? What is byte?

"bit" stands for binary digit. It is a basic unit of information in information theory, computing, and digital communications. 1 bit can be `1` or `zero`.

A group of 8 binary digits is commonly called one byte, but historically the size of the byte is not strictly defined. If we use binary number to represent decimal numbers, the positive or negative sign take 1 bit then we left 7 bits in a byte, then this 1 byte can range from `-1111111` to `+11111111` that is -127 to +127. If we only consider positive numbers then we can represent number from `00000000` to `11111111` that is 0 to 255.

63. What's the syntax to add multiple new columns to a table when creating a table?

```SQL
CREATE TABLE table_name (
  col_name integer,
  col_name1 text NOT NULL
);
```

64. How to extract a year number(as integer) from a timestamp/date column?

https://stackoverflow.com/questions/43397871/postgresql-getting-a-year-from-date-type-as-integer

Use `extract()` function

`SELECT extract(year from published_date)::int FROM reviews;`

65. How to split a string in PostgreSQL? How to get substring from a given string position in PostgreSQL?

https://www.postgresql.org/docs/11/functions-string.html

To split a string into an array we can use `regexp_split_to_array(string text, pattern text [, flags text ])`

```
sql_book=# SELECT regexp_split_to_array('I am an alient.', '\s');
 regexp_split_to_array
-----------------------
 {I,am,an,alient.}
(1 row)
```

To get substring from a given string position use `substring(string [from int] [for int])`

```
sql_book=# SELECT substring ('simultaneously' from 3 for 2);
 substring
-----------
 mu
(1 row)
```

Notice the `3` is not zero based index.

66. What would be the result if we perform any operator on `NULL` in postgresql?

It will return `NULL`

```
sql_book=# SELECT NULL = NULL;
 ?column?
----------

(1 row)

sql_book=# SELECT NULL * 2;
 ?column?
----------

(1 row)
```

But notice when we use comparison predicates `IS NULL` OR `IS NOT NULL` it will return boolean value.

```
sql_book=# SELECT NULL IS NULL;
 ?column?
----------
 t
(1 row)
```

67. What are the 3 aspects of restriction we can add to a column?

- type
- length
- constraints

68. What is natural key and surrogate key?

- Natural key means using existing values of a column in a table as the primary key of the table.
- surrogate key means create another column which solely used as its primary key.

69. What's the difference between `(id integer PRIMARY KEY)` and `(id serial)`

think of these:
- auto incrementing?
- allow null?
- enforce unique?
- type?

`(id integer PRIMARY KEY)`
- integer type
- not auto incrementing
- UNIQUE
- NOT NULL

`(id serial)`
- integer type
- auto incrementing
- allow NULL
- doesn't require UNIQUE

70. In SQL, is sequence independent to table?

https://www.postgresql.org/docs/11/sql-createsequence.html

https://www.ibm.com/support/knowledgecenter/ssw_ibm_i_71/sqlp/rbafysequence.htm

https://docs.oracle.com/cd/B19306_01/server.102/b14200/statements_6015.htm

Yes.

```sql
sql_book=# \d
               List of relations
 Schema |       Name       |   Type   | Owner
--------+------------------+----------+--------
 public | addresses        | table    | xullnn
 public | books            | table    | xullnn
 public | books_id_seq     | sequence | xullnn -- sequence
 public | checkouts        | table    | xullnn
 public | checkouts_id_seq | sequence | xullnn -- sequence
```

Type `sequence` indicates that a sequence is independent to a table, but a table can use a sequence as part of itself. Another evidence is that when we create or delete a sequence we don't have to mention the table name.

71. If a column was originally set with a `DEFAULT` value, what would happen if we exclude the column name from the column list while performing inserting or updating?

https://www.postgresql.org/docs/11/ddl-default.html

That column will filled with the default value. If no default value is declared explicitly, the default value is the null value. This usually makes sense because a null value can be considered to represent unknown data.

72. If a column was originally set as `boolean` type and not added with a `NOT NULL` constraint. How to construct an expression to select all rows that are not `false` in this column?(notice the relationship between boolean values and `NULL`, what is the opposite(!=) of `true` or `false`)

`... WHERE column_name != false AND column_name IS NULL;`

73. How to distinguish relation and relationship?

Relation is just another way to say table, relationship describe how different relations(tables) relate to each other.

74. What is cardinality of a relationship?

https://www.sqa.org.uk/e-learning/SoftDevRDS02CD/page_44.htm

Cardinality of a relationship is the number of entities on each side of the relation. For example, in a one-to-many relationship. The cardinality of this relationship is 1 and many. We can think of cardinality as the maximum number of connections of each side.

75. What is modality within a relationship?

https://www.calebcurry.com/cardinality-and-modality/

Modality indicates whether the relationship between relations is required. Or we can understand it as the minimum number of connections of each side.

For example in a one-to-many relationship
- the cardinality of this relationship is one-to-many
- if the `many` side can have 1 entity of the `one` side, but it can also not to have 1 of the `one` side, or say on the `one` side the relationship is not required, then in this relationship the `one` side can be 0 or 1.
- if the `many` side must have 1 entity of the `one` side, means the relationship is required, then in this relationship the number of entities on the `one` side can only be 1.
- if the `one` side can have many entities of the `many` side, but it doesn't have to have 1 of them, or say the relationship on the `many` side is not required, then in this relationship the number of entities on the `many` side can be zero or more(0, 1, 2, 3 ...)
- same logic can perform to other situations

76. What is crow's foot notation used for? Why it is named crow's foot?

Crow's foot notation is used to draw out the relationship of tables, or say it's a graphic description of a relationship's cardinality and modality.

77. Why we can't use aggregation functions in `WHERE` clause?(think of from what object(s) each them will perform on?)

https://stackoverflow.com/questions/42470849/why-are-aggregate-functions-not-allowed-in-where-clause

- Where handles 1 row each time, it filters rows by scanning the table row by row.
- aggregate function perform operation on multiple rows, the choosing of rows in aggregate function is based on the result of `WHERE` clause
- so the order of operation is scan and filter rows by `FROM` and `WHERE` then perform aggregate function, so we cannot perform aggregate function in the middle of the work of `WHERE`

If want to perform further filter based on `WHERE`'s work, we can add a `HAVING` clause.

78. What are the two ways to create a foreign key constraint?

- Add as column constraint when creating table
- Add as table constraint using `ALTER TABLE` sentence

```
CREATE TABLE table_name (
  id serial,
  user_id integer REFERENCES users(id)
  );

CREATE TABLE table_name (
  id serial,
  user_id integer,
  FOREIGN KEY (user_id) REFERENCES users(id)
  );


ALTER TABLE table_name ADD FOREIGN KEY (book_id) REFERENCES books(id);
```

79. Does a foreign key constraint prevent NULL values from being stored in a column?What about primary key column

No, foreign key will not prevent `NULL`. But a primary key constraint will impose both `UNIQUE` AND `NOT NULL`.

80. What is the two basic steps to perform a normalization?

- split table
- build relationship between new tables

81. What's the difference between `WHERE` and `HAVING`?

https://stackoverflow.com/questions/287474/whats-the-difference-between-having-and-where

- HAVING: is used to check conditions after the aggregation takes place.
- WHERE: is used to check conditions before the aggregation takes place.

82. At which places we can put a subquery in SQL?

A subquery may occur in :
- A SELECT clause
- A FROM clause
- A WHERE clause
The subquery can be nested inside a SELECT, INSERT, UPDATE, or DELETE statement or inside another subquery.

83. Briefly describe the use of `EXISTS` `IN` `NOT IN` `ANY/SOME` `ALL` in `WHERE` clause which contains subquery?

Similar to comparison operators(`>` `<` `!=` ...), in WHERE clause all the keywords above plus a set of(or a single) value(s) form the predicate of the comparison expression. Some possible examples may be:

- `WHERE EXISTS (SELECT name FROM users WHERE age > 110);`
- `WHERE age NOT IN (SELECT age FROM users);`
- `WHERE age > ALL (SELECT age FROM users);`

Notice in certain cases, some syntaxes are interchangeable. For example `WHERE age > ALL (SELECT age FROM users);` or `WHERE age < ALL (SELECT age FROM users);` can also write as `WHERE age NOT IN (SELECT age FROM users);`.

84. How indexes work?

https://stackoverflow.com/questions/1108/how-does-database-indexing-work

From low level view, data are stored in physical medium like a disk. A disk are normally formed with many basic block units which have a fixed storage capability like say 1024 bytes. And each disk block has an address to let it can be found.

Reading a specific row of data from a table within a database involves this disk accessing process. The database server has to first load the data from physical medium, then filter out the row we want. The purpose of adding index is to accelerate this accessing process.

Adding index to a specific is actually creating another table to hold all the addresses for certain pieces of information.

For example if we have a `users` table which has 5 million users in it. Then we want find all the information about users who named `Bob`. If we don't want to miss any `Bob` in the table, we have to scan all the rows(5million) to find all `Bob` there.

Suppose 1 disk block can just hold 1 row of data, so the number of times to access the disk would be 5000000.

But if we add an index to `name` column. There may be a row like this in the index table

| Name     | disk address     |
| :------------- | :------------- |
| Alice       | 243, 10998 ...      |
| Bob       | 76589, 100001, 4532000 ...      |
| ...      | ...       |

Notice index is normally sorted and unique. If this index table has 4 million rows(due to people have same names), and every row only take half size of the `users` table, so it only need `4m / 2 = 2000000` times disk access to iterate through the index table. Since the names in index table are sorted and unique so it only take `log2 2000000 = 20.93 = 21` times to find the `Bob` row, then another 1 time access to load all Bob's information from the disk based on the `disk addresses` given by index table, so it takes `21 + 1 = 22` times to find all Bob.

5000000 vs 22, that's the difference.

85. How to create index on specified column(s) within a database?
`CREATE INDEX index_name ON table_name (field_name);`
