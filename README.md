 # **SQL Server Syntax**   :exclamation: 🚀
***
#  🚦  database and tables and column in SQL
## for print any value
```
$ print 5+7
$ print 'hello' + ' world'
```
## for print vlaue in new column 
```
$ select  'hello' + ' world' as 'new column'
```
## to create new database 
```
$ create database "test"
on primary
(Name= tt, fileName='F:\SQLTEST\tt.mdf')
log on 
(Name= ll, fileName='F:\SQLTEST\tt.ldf')
```
## for delete database
```
$ drop database test
```
## from add table in databes
```
$ use test
create table My_Table_1 (my_column_1 int)
```
## for change table name 
```
$ sp_rename 'My_Table_1' , 'table_1'
```
## for add new column in table
```
$ use test
create table my_table_1 (id int , my_Name nvarchar(50))
```
## for delete table from database
```
$ use test
drop table table_1
```
## for change column name
```
$ sp_rename 'my_table_1.my_Name' , 'Name_Jobs' , 'Column'
```

## for delete column 
```
$ use test
alter table my_table_1 drop column  my_date
```

## for change properties in column 
```
$ use test
alter table my_table_1 alter column id int  not null 
```
## how to set primary key and identity
```
$ use test
go
create table my_table_3( my_Id int primary key identity(1,1) ,Name nvarchar(50)) 
```
## to add primary key in old column 
```
$ use test
alter table my_table_4
add constraint PK_my_Id primary key(my_Id,myname)
```

## to delete primary key from column
```
$ use test
alter table my_table_4
drop constraint PK_my_Id 
```
***
#  🚦  Insert, update ,delete  in SQL

## insert into table
```
$ insert into Employees (LastName,FirstName,Title) values ('midoo','midoo','sales manager')
```

## update into table
```
$ update Employees set LastName= 'ahmed' ,Title= 'title name' where EmployeeID=11
```
## delete column from table
```
$ delete from  Employees where EmployeeID=11
```

#  🚦  Select in SQL

## select any column from table 
```
$ use Northwind
select EmployeeID,LastName,Title from Employees
```
## select all column from table
```
$ use Northwind
select * from Employees
```

## select only not match from column 
```
$ use Northwind
select distinct City from Employees
```
## select only not match from column 
```
$ use Northwind
select LastName from Employees where TitleOfCourtesy='Mr.' or City='London'
select LastName from Employees where TitleOfCourtesy='Mr.' and City='London'
```

## use order by 
```
$ select * from Employees order by LastName
```

## use descinding and asc
```
$ select * from Employees order by LastName  desc
$ select * from Employees order by LastName  asc
```
## select any rows without some rows
```
$ select [LastName],[Title] from Employees where [LastName] not in (select [LastName] from [Employees] where LastName='midoo' )
```
## use top in select
```
$ select top 5 * from Employees
$ select top 5 EmployeeID,LastName from Employees
$ select top 50 percent EmployeeID,LastName from Employees
```

## use alias in column 
```
$ select top 50 percent  EmployeeID as 'رقم الموظف',LastName as 'اسم الموظف' from Employees
```
## use * operator
```
$ select * , Discount* Quantity as 'الكميه' from [Order Details]
```
## select from table and make + to column
```
$ select Title,+ FirstName + ' ' +LastName as 'full name'  from Employees
```
## use in in where
```
$ select *  from Employees where BirthDate in ('8/12/1948', '8/12/1966')
```

## use like in select to search
```
$ select *  from Employees where FirstName like '%N%'
```

#  🚦  Select into in SQL

## this for copy all data from any table to new table 
```
$ select * into customersInto5
from Customers  
where CompanyName ='Alfreds Futterkiste'
```
## use join and where with select into 
```
$ select Orders.EmployeeID ,Employees.FirstName into	emp
from Orders inner join Employees on Orders.EmployeeID= Employees.EmployeeID
where Employees.EmployeeID=1  
```
