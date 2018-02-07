Create a table in SQL Server:

```
CREATE TABLE tblPerson(firstname nvarchar(50),lastname nvarchar(50),city nvarchar(50),state nvarchar(50))
```



Select columns in a table:

```
SELECT firstname,lastname,city,state from tblPerson
join tblAddress on tblperson.personid=tblAddress.personid
```



