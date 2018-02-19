

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

**SOLUTION**:

```
CREATE TABLE	Persons( PersonsId int,FirstName varchar(50),LastName varchar(50))

```

```
CREATE TABLE   	 Adresses ( AdressesId int,PersonsId int,,City varchar(50),State varchar(50))

```

This QUERY JOINS COLUMNS FROM 2 SEPERATE TABLES

```
SELECT 	FirstName,LastName,City,State

 FROM	 Persons

JOIN	 Addresses 

ON		 persons.personsid=Addresses.personsid
```

