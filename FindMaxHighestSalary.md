Write a SQL query to get the max highest salary from the `Employee` table.

```
+----+--------+
| Id | Salary |
+----+--------+
| 1  | 1000    |
| 2  | 2000    |
| 3  | 3000    |
| 4  | 4000    |
| 5  | 2000
+----+--------+

```

For example, given the above Employee table, the query should return `3000` as the Max highest salary. 

```
+---------------------+
| MaxHighestSalary |
+---------------------+
| 3000                 |
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
SELECT	MAX(Salary)As MaxHighestsalary
FROM	Employee
```

