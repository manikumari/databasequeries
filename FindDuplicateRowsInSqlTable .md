Write a SQL query to find all duplicate emails in a table named `Person`.

```
+----+---------+
| Id | Email   |
+----+---------+
| 1  | a@b.com |
| 2  | c@d.com |
| 3  | a@b.com |
+----+---------+

```

For example, your query should return the following for the above table:

```
+---------+
| Email   |
+---------+
| a@b.com |
+---------+

```

**SOLUTION:**



```
CREATE TABLE Person(Id int,Email nvarchar(50))

INSERT INTO Person(Id,Email) VALUES(1,'a@b.com')

INSERT INTO Person(Id,Email) VALUES(2,'c@d.com')

INSERT INTO Person(Id,Email) VALUES(3,'a@b.com')

```

Duplicated emails existed more than one time.To find duplicate rows here which contains emails we can use GROUP BY and HAVING conditions.

```

SELECT  Email 
FROM    Person GROUP BY Email HAVING count(Email)>1


```

