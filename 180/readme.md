## SQL and Relationship Database

1. What is relational database? include these terms in answer and do a lucid describe of these terms
- relational model
- RDBMS
- SQL

2. What's the difference among:
- PostgreSQL client application(`createdb`, `psql`, `dropdb`)
- meta-commands(`\c db_name`, `\list`)
- SQL statements

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

21. How to check the schema of a specific table?

22. Is the 'security settings'(controlled by DCL) of a database part of its schema?

23. If part an sql statement is `(weight DECIMAL(8, 2))` what's the meaning of `8` and `2`? What the max and minimal value for this column?

24. What's in common on all below syntax?

- rename a table
- rename a column
- change a column's datatype
- adding a constraint(can we alter a constraint? like change `varchar(25)` to `varchar(50)`)
- removing a constraint
- adding a column
- removing a column

25. What are the four types of Data Manipulation Statements?

26. What is the syntax of inserting data?

27. How to add a `CHECK` constraint to a column to let it can't be inserted into empty string?

28. What's the alternative syntax of `<>` in SQL?

29. How to insert string `'O' Sullivan'` into a table?

30. What would cause a "Three State Boolean problem or Three Valued-logic problem" ?

31. What's the difference between `char` and `varchar` type when we use match pattern to match content in certain column(s)?

33. If you have a column named just as one of reserved words in SQL, how could you handle this?

34. If we order query results by a boolean column in ascending order, which ones would be listed first?

35. What is the sort logic which contains multiple sorting conditions, like:

```
SELECT * FROM users ORDER BY activated ASC, id DESC;
```

36. Operators are used in which clause in SQL Query?

37. What are the main 3 types of operator in SELECT query?

38. The meaning of `"predicates"` in Grammar can be seen as "the part of a sentence that is other than the subject". What's `comparison predicates` in `WHERE` clause?

- subject, verb, object
  - `id = 2`
  - `id IS NOT NULL`

39. How to get all rows of whose certain column is `NULL`?

40. Choose logical operator for each word:
- either
- both
- other than

41. What is the wild card character in a SQL to match string?

42. What's the key word used for string matching?

43. How to match all user names whose name contains `Lee`. like `Mary Lee. S`, `Lee Jhon`, `Wu Lee.`in a `char(15)` column?

45. What's the basci syntax of updating row(s) in a table?

46. What would happen if we omit the `WHERE` clause potion of our updating statement?

47. What's the basic syntax to delete row(s) in a table?

48. What would happen if we omit the `WHERE` clause potion of our deleting statement?

49. What is normalization of database?

50. Why we need normalization?

51. what's the mechanism for carrying out normalization?

52. How you understand entities and relationships in database design?

53. What is an Entity Relationship Diagram?

54. What is primary and foreign key, what are they used for?

55. What's the meaning of referential integrity?

56. Why we need `ON DELETE` clause, how it relates to referential integrity?

57. What a cross-reference table(join table) be used for?

58. What's the basic syntax of join tables?

59. What's the difference between `INNER JOIN`, `LEFT OUTER JOIN`, `RIGHT OUTER JOIN`, `FULL JOIN`, and `CROSS JOIN`, which two of them are less used?

60. What's the syntax of table name aliasing in SQL?(and shorthand form)

61. What's the syntax of column name aliasing in SQL?

62. What's subquery in SQL? Take the below example to explain:

```sql
SELECT u.full_name FROM users u
WHERE u.id NOT IN (SELECT c.user_id FROM checkouts c);
```

63. In some situations, can JOINs and subqueries interchangeable?

64. Does SQL only handle data in databases?

65. What is bit? What is byte?

67. What's the syntax to add multiple new columns to a table when creating a table?

68. How to extract a year number(as integer) from a timestamp/date column?

https://stackoverflow.com/questions/43397871/postgresql-getting-a-year-from-date-type-as-integer

69. How to split a string in PostgreSQL? How to get substring from a given string position in PostgreSQL?

https://www.postgresql.org/docs/11/functions-string.html

70. What would be the result if we perform any operator on `NULL` in postgresql?

71. What are the 3 aspects of restriction we can add to a column?

73. What is natural key and surrogate key?

74. What's the difference between `(id integer PRIMARY KEY)` and `(id serial)`

think of these:
- auto incrementing?
- allow null?
- enforce unique?
- type?

75. In SQL, is sequence independent to table?

https://www.postgresql.org/docs/11/sql-createsequence.html

https://www.ibm.com/support/knowledgecenter/ssw_ibm_i_71/sqlp/rbafysequence.htm

https://docs.oracle.com/cd/B19306_01/server.102/b14200/statements_6015.htm

76. If a column was originally set with a `DEFAULT` value, what would happen if we exclude the column name from the column list while performing inserting or updating?

https://www.postgresql.org/docs/11/ddl-default.html

77. If a column was originally set as `boolean` type and not added with a `NOT NULL` constraint. How to construct an expression to select all rows that are not `false` in this column?(notice the relationship between boolean values and `NULL`, what is the opposite(!=) of `true` or `false`)

79. How to distinguish relation and relationship?

80. What is cardinality of a relationship?

https://www.sqa.org.uk/e-learning/SoftDevRDS02CD/page_44.htm

81. What is modality within a relationship?

at least amount

82. What is crow's foot notation used for? Why it is named crow's foot?

83. Why we can't use aggregation functions in `WHERE` clause?(think of from what object(s) each them will perform on?)

https://stackoverflow.com/questions/42470849/why-are-aggregate-functions-not-allowed-in-where-clause

84. What are the two ways to create a foreign key constraint?

85. Does a foreign key constraint prevent NULL values from being stored in a column?What about primary key column

86. What is the two basic steps to perform a normalization?

87. What's the difference between `WHERE` and `HAVING`?

88. Does a newly added foreign key constraint will also enforce a  `NOT NULL` constraint to the column?

89. At which places we can put a subquery in SQL? What's the main difference?

90. Briefly describe the use of `EXISTS` `IN` `NOT IN` `ANY/SOME` `ALL` in `WHERE` clause?

91. How indexes work?

https://stackoverflow.com/questions/1108/how-does-database-indexing-work

92. How to create index on specified column(s) within a database? 
