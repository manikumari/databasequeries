Write a SQL query to find and delete  duplicate emails  in a table named `Person`.

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
```

```
INSERT INTO Person(Id,Email)VALUES(1,'a@b.com')
INSERT INTO Person(Id,Email)VALUES(2,'c@d.com')
INSERT INTO Person(Id,Email)VALUES(3,'a@b.com')
```

By joining this table with itself on the *Email* column, we can get the following code.

```
SELECT	a.*
FROM	Person a, Person b
WHERE	a.Email=b.Email
```

Now  we need to find the bigger id having same email address with other records. So we can add a new condition to the `WHERE` clause like this.

```
SELECT	a.*
FROM 	Person a, Person b
WHERE 	a.Email=b.Email and a.id>b.id
```

As we already get the records to be deleted, we can alter this statement to `DELETE` in the end.

```
DELETE	a
FROM 	Person a, Person b
WHERE 	a.Email=b.Email and a.Id>b.Id
```

