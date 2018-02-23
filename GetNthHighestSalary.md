Write a SQL query to get the *n*th highest salary from the `Employee` table.

```
+----+--------+
| Id | Salary |
+----+--------+
| 1  | 1000   |
| 2  | 2000   |
| 3  | 3000   |
| 4  | 2500   |
| 5  | 2000   |
+----+--------+

```

For example, given the above Employee table, the *n*th highest salary where *n* = 2 is `2500`or n=3 is `2000`  . If there is no *n*th highest salary, then the query should return `null`.

```
+------------------------+
| getNthHighestSalary(2) |
+------------------------+
| 2500                   |
+------------------------+

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

To get Nth highest salary Dense rank function is  one way of solution.

```
SELECT 		salary, DENSE_RANK() over (ORDER BY salary DESC) AS DenseRank 

FROM		Employee
```

| Salary | DenseRank |
| :----: | :-------: |
|  3000  |     1     |
|  2500  |     2     |
|  2000  |     3     |
|  2000  |     3     |
|  1000  |     4     |

Now  we've  create CTE with named RESULT  for this result set:

```
WITH		RESULT as

(SELECT 	salary, DENSE_RANK() over (ORDER BY salary DESC) AS DenseRank FROM	Employee)

SELECT		TOP 1 Salary 

FROM		RESULT 

WHERE		RESULT.DenseRank=2    --we can choose DenseRank=?
```

