Create a table in SQL Server:

```
CREATE TABLE tblPersons

( PersonsId int,FirstName varchar(50),LastName varchar(50))

CREATE TABLE tblAdresses

( AdressesId int,PersonsId int,,City varchar(50),State varchar(50));
```



Select columns in a table:

```
SELECT FirstName,LastName,City,State 
from tblPersons
join tblAddresses 
on tblpersons.personsid=tblAddresses.tblpersonsid;
```



