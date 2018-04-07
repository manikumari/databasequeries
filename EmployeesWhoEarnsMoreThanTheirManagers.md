The `Employee` table holds all employees including their managers. Every employee has an Id, and there is also a column for the manager Id.

```
+----+-------+--------+-----------+
| Id | Name  | Salary | ManagerId |
+----+-------+--------+-----------+
| 1  | John   | 70000  | 3         |
| 2  | Helen  | 80000  | 4         |
| 3  | Sid    | 60000  | NULL      |
| 4  | Mike   | 90000  | NULL      |
+----+-------+--------+-----------+

```

Given the `Employee` table, write a SQL query that finds out employees who earn more than their managers. For the above table, John is the only employee who earns more than his manager.

```
+----------+
| Employee |
+----------+
| John      |
+----------+

```

SOLUTION:

```
CREATE TABLE	Employee(ID int, Name varchar(50), Salary int, ManagerId int)
```

```
INSERT INTO		Employee(ID,Name,Salary,ManagerID) Values(1,John,70000,3)

INSERT INTO		Employee(ID,Name,Salary,ManagerID) Values(2,Helen,80000,4)

INSERT INTO		Employee(ID,Name,Salary,ManagerID) Values(3,sid,60000,NULL)

INSERT INTO		Employee(ID,Name,Salary,ManagerID) Values(4,Mike,90000,NULL)
```

As this table has the employee's and manager's information, we probably need to select information from it twice.By joining the table itself will get the information twice.

```
SELEC	*
FROM    Employee AS E1
JOIN    Employee AS E2;
```

| Id   | Name  | Salary | ManagerId | Id   | Name  | Salary | ManagerId |
| ---- | ----- | ------ | --------- | ---- | ----- | ------ | --------- |
| 1    | John  | 70000  | 3         | 1    | John  | 70000  | 3         |
| 2    | Helen | 80000  | 4         | 1    | John  | 70000  | 3         |
| 3    | Sid   | 60000  |           | 1    | John  | 70000  | 3         |
| 4    | Mike  | 90000  |           | 1    | John  | 70000  | 3         |
| 1    | John  | 70000  | 3         | 2    | Helen | 80000  | 4         |
| 2    | Helen | 80000  | 4         | 2    | Helen | 80000  | 4         |
| 3    | Sid   | 60000  |           | 2    | Helen | 80000  | 4         |
| 4    | Mike  | 90000  |           | 2    | Helen | 80000  | 4         |
| 1    | John  | 70000  | 3         | 3    | Sid   | 60000  |           |
| 2    | Helen | 80000  | 4         | 3    | Sid   | 60000  |           |
| 3    | Sid   | 60000  |           | 3    | Sid   | 60000  |           |
| 4    | Mike  | 90000  |           | 3    | Sid   | 60000  |           |
| 1    | John  | 70000  | 3         | 4    | Mike  | 90000  |           |
| 2    | Helen | 80000  | 4         | 4    | Mike  | 90000  |           |
| 3    | Sid   | 60000  |           | 4    | Mike  | 90000  |           |
| 4    | Mike  | 90000  |           | 4    | Mike  | 90000  |           |

The first 3 columns are from table E1 and the last 3 columns are from table E2.

Select from two tables will get the [Cartesian product](https://en.wikipedia.org/wiki/Cartesian_product) of these two tables. In this case, the output will be 4*4 = 16 records. However, what we interest is the employee's salary higher than  their manager. So we should add two conditions in a `WHERE` clause like below.  

```
SELET    E1.Name as Employee
FROM     Employee  E1
JOIN     Employee  E2
ON       E1.ManagerId = E2.Id
AND      E1.Salary > E2.Salary;

```


