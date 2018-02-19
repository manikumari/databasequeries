Write a SQL query to get the Second max highest salary from the `Employee` table.

```
+----+--------+
| Id | Salary |
+----+--------+
| 1  | 1000    |
| 2  | 2000    |
| 3  | 3000    |
| 4  | 2500    |
| 5  | 2000
+----+--------+

```

For example, given the above Employee table, the query should return `2500` as the second highest salary. If there is no second highest salary, then the query should return `null`.

```
+---------------------+
| SecondHighestSalary |
+---------------------+
| 2500                |
+---------------------+
```

**SOLUTION:**

```
CREATE TABLE 	Employee(Id int,Salary int)
```

```
INSERT INTO		Employee(Id,Salary) VALUES(1,1000)
INSERT INTO		Employee(Id,Salary) VALUES(2,2000)
INSERT INTo		Employee(Id,Salary) VALUES(3,3000)
INSERT INTo		Employee(Id,Salary) VALUES(4,2500)
INSERT INTo		Employee(Id,Salary) VALUES(5,2000)
```

We can get maximum highest salary in the table by using max function

```
SELECT	MAX(Salary)
FROM	Employee
```

To get the Second max highest salary  by **where** clause and **not in** (or) < then we can use the above query as sub query :

```
SELECT	MAX(Salary)AS SecondHighestSalary

FROM	Employee 

WHERE	Salary NOT IN (SELECT MAX(Salary)FROM Employee)


```

