## SQL and Relationship Database

1. What is relational database? include these terms in answer and do a lucid describe of these terms
- relational model
- RDBMS
- SQL

2. What's the difference among:
- PostgreSQL client application(`createdb`, `psql`, `dropdb`)
- meta-commands(`\c db_name`, `\list`)
- SQL

3. What is the sign of the end of an sql statement?

4. How to perform these operations by using postgresql client applications

- set up
  - how to create a database with a given name
  - what is the extension name of a file that we write sql statements in?
  - how to import an external .sql file into an existent database?

- connect
  - how to connect to a database locally?
  - what does `-d` flag means in a `psql` Meta-commands(check `psql --help`)

5. how to select one or more columns from a table? how to separate the names of columns

6. what's the means of database usually used to label a specific row? or say what will be used as unique identifier to a row?

7. what should be written before and after the `=` in sql statement? what is the difference on meaning of this in sql and programing language like Ruby.

8. What is the schema of a database?

9. What is the data of a database?

10. What is the relationship between schema and database, database and data?

11. What sub-languages of SQL will be used to handle schema and data?

12. What DDL handles about within a database? What things DDL will not touch in a database?

13. How to create a new PostgreSQL database from terminal? And how to do so in psql console?

14. How to connect to another database in psql console?

15. If your psql prompt is `another_database=#`, and you want to delete the `another_database` database, how to do it? Two ways!

16. Point out the different components in this sql statement, which of these components are required.

```
sample_db=# CREATE TABLE users (
  id serial UNIQUE NOT NULL,
  username CHAR(25)
  );
```

17. Could constraints only be at table column level?

18. Why we need constraints?

19. How to view
  - all databases on your local machine
  - all relations in a database in psql console?
  - all tables in a database in psql console?
  - all sequences

20. How to check the schema of a specific table?

21. Is the 'security settings'(controlled by DCL) of a database part of its schema?

22. If part an sql statement is `(weight DECIMAL(8, 2))` what's the meaning of `8` and `2`? What the max and minimal value for this column?

23. What's in common on all below syntax?

- rename a table
- rename a column
- change a column's datatype
- adding a constraint(can we alter a constraint? like change `varchar(25)` to `varchar(50)`)
- removing a constraint
- adding a column
- removing a column

24. What are the four types of Data Manipulation Statements?

25. What is the syntax of inserting data?

26. How to add a `CHECK` constraint to a column to let it can't be inserted into empty string?

27. What's the alternative syntax of `<>` in SQL?

28. How to insert string `'O' Sullivan'` into a table?

29. What would cause a "Three State Boolean problem or Three Valued-logic problem" ?

30. What's the difference between `char` and `varchar` type when we use match pattern to match content in certain column(s)?

31. If you have a column named just as one of reserved words in SQL, how could you handle this?

32. If we order query results by a boolean column in ascending order, which ones would be listed first?

33. What is the sort logic which contains multiple sorting conditions, like:

```
SELECT * FROM users ORDER BY activated ASC, id DESC;
```

34. Operators are used in which clause in SQL Query?

35. What are the main 3 types of operator in SELECT query?

36. The meaning of `"predicates"` in Grammar can be seen as "the part of a sentence that is other than the subject". What's `comparison predicates` in `WHERE` clause?

- subject, verb, object
  - `id = 2`
  - `id IS NOT NULL`

37. How to get all rows of whose certain column is `NULL`?

38. Choose logical operator for each word:
- either
- both
- other than

39. What is the wild card character in a SQL to match string?

40. What's the key word used for string matching?

41. How to match all user names whose name contains `Lee`. like `Mary Lee. S`, `Lee Jhon`, `Wu Lee.`in a `char(15)` column?

42. What's the basci syntax of updating row(s) in a table?

43. What would happen if we omit the `WHERE` clause potion of our updating statement?

44. What's the basic syntax to delete row(s) in a table?

45. What would happen if we omit the `WHERE` clause potion of our deleting statement?

46. What is normalization of database?

47. Why we need normalization?

48. what's the mechanism for carrying out normalization?

49. How you understand entities and relationships in database design?

50. What is an Entity Relationship Diagram?

51. What is primary and foreign key, what are they used for?

52. What's the meaning of referential integrity?

53. Why we need `ON DELETE` clause, how it relates to referential integrity?

54. What a cross-reference table(join table) be used for?

55. What's the basic syntax of join tables?

56. What's the difference between `INNER JOIN`, `LEFT OUTER JOIN`, `RIGHT OUTER JOIN`, `FULL JOIN`, and `CROSS JOIN`, which two of them are less used?

57. What's the syntax of table name aliasing in SQL?(and shorthand form)

58. What's the syntax of column name aliasing in SQL?

59. What's subquery in SQL? Take the below example to explain:

```sql
SELECT u.full_name FROM users u
WHERE u.id NOT IN (SELECT c.user_id FROM checkouts c);
```

60. In some situations, can JOINs and subqueries interchangeable?

61. Does SQL only handle data in databases?

62. What is bit? What is byte?

63. What's the syntax to add multiple new columns to a table when creating a table?

64. How to extract a year number(as integer) from a timestamp/date column?

https://stackoverflow.com/questions/43397871/postgresql-getting-a-year-from-date-type-as-integer

65. How to split a string in PostgreSQL? How to get substring from a given string position in PostgreSQL?

https://www.postgresql.org/docs/11/functions-string.html

66. What would be the result if we perform any operator on `NULL` in postgresql?

67. What are the 3 aspects of restriction we can add to a column?

68. What is natural key and surrogate key?

69. What's the difference between `(id integer PRIMARY KEY)` and `(id serial)`

think of these:
- auto incrementing?
- allow null?
- enforce unique?
- type?

70. In SQL, is sequence independent to table?

https://www.postgresql.org/docs/11/sql-createsequence.html

https://www.ibm.com/support/knowledgecenter/ssw_ibm_i_71/sqlp/rbafysequence.htm

https://docs.oracle.com/cd/B19306_01/server.102/b14200/statements_6015.htm

71. If a column was originally set with a `DEFAULT` value, what would happen if we exclude the column name from the column list while performing inserting or updating?

https://www.postgresql.org/docs/11/ddl-default.html

72. If a column was originally set as `boolean` type and not added with a `NOT NULL` constraint. How to construct an expression to select all rows that are not `false` in this column?(notice the relationship between boolean values and `NULL`, what is the opposite(!=) of `true` or `false`)

73. How to distinguish relation and relationship?

74. What is cardinality of a relationship?

https://www.sqa.org.uk/e-learning/SoftDevRDS02CD/page_44.htm

75. What is modality within a relationship?

at least amount

76. What is crow's foot notation used for? Why it is named crow's foot?

77. Why we can't use aggregation functions in `WHERE` clause?(think of from what object(s) each them will perform on?)

https://stackoverflow.com/questions/42470849/why-are-aggregate-functions-not-allowed-in-where-clause

78. What are the two ways to create a foreign key constraint?

79. Does a foreign key constraint prevent NULL values from being stored in a column?What about primary key column

80. What is the two basic steps to perform a normalization?

81. What's the difference between `WHERE` and `HAVING`?

82. At which places we can put a subquery in SQL? What's the main difference?

83. Briefly describe the use of `EXISTS` `IN` `NOT IN` `ANY/SOME` `ALL` in `WHERE` clause?

84. How indexes work?

https://stackoverflow.com/questions/1108/how-does-database-indexing-work

85. How to create index on specified column(s) within a database?
