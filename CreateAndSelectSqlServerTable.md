

Table: `Persons`

```
+-------------+---------+
| Column Name | Type    |
+-------------+---------+
| PersonId    | int     |
| FirstName   | varchar |
| LastName    | varchar |
+-------------+---------+
PersonsId is the primary key column for this table.

```

Table: `Addresses`

```
+-------------+---------+
| Column Name | Type    |
+-------------+---------+
| AddressId   | int     |
| PersonId    | int     |
| City        | varchar |
| State       | varchar |
+-------------+---------+
AddressesId is the primary key column for this table.

```

Write a SQL query for a report that provides the following information for each person in the Person table, regardless if there is an address for each of those people:

```
FirstName, LastName, City, State
```

SOLUTION:

```
CREATE TABLE	Persons( PersonsId int,FirstName varchar(50),LastName varchar(50))

```

```
CREATE TABLE   	 Adresses ( AdressesId int,PersonsId int,,City varchar(50),State varchar(50))

```

Since the *PersonId* in table **Addresses** is the foreign key of table **Persons**, we can join this two table to get the address information of a person.

This query JOINS columns from 2 seperate tables

```
SELECT	FirstName,LastName,City,State

FROM	Persons

JOIN	Addresses 

ON		persons.personsid=Addresses.personsid
```

