### SQL Advanced:

**1) What is the Difference Between Unique and Distinct in SQL ?**

* **Unique** is a constraint in SQL that allows one or more fields or columns of a table to uniquely identify a record in a database table.
* **Distinct** is command used with �select� that helps to return distinct or different values in the result set.

**Usage :**

* Furthermore, unique is a constraint that prevents two records from having identical values in a column, while distinct helps to remove duplicate values when retrieving data.

**Conclusion :**

* In brief, SQL is a language that allows performing operations on data stored in the database. Unique and Distinct are two SQL  constraints. The main difference between Unique and Distinct in SQL is that Unique helps to ensure that all the values in a column are different while Distinct helps to remove all the duplicate records when retrieving the records from a table.   
 
 **2) What is the Difference Between truncate and delete OR When are we going to use truncate and delete?**

* TRUNCATE is a DDL command, whereas DELETE is a DML command.
* We can�t execute a trigger in case of TRUNCATE whilst with DELETE, we can accomplish a trigger.
* TRUNCATE is quicker than DELETE, for the reason that when we use DELETE to delete the data, at that time it store the whole statistics in the rollback gap on or after where we can get the data back after removal. In case of TRUNCATE, it will not store data in rollback gap and will unswervingly rub it out. TRUNCATE do not recover the deleted data.
* **We can use any condition in WHERE clause using DELETE but it is not possible with TRUNCATE.5.If a table is referenced by any foreign key constraints, then TRUNCATE won�t work.**

**DELETE** | **TRUNCATE**
------------ | -------------
Delete command is used to delete a row in a table	| Truncate is used to delete all the rows from a table
You can rollback data after using delete statement	| You cannot rollback data
It is a DML command	| It is a DDL command
