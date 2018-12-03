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
#  🚦  Join in SQL

## use inner join in sql
```
$ select Categories.categoryID, Categories.CategoryName,Categories.Description ,Products.ProductName,Products.UnitPrice
 from Categories inner join Products on Categories.CategoryID=Products.ProductID
```

## use left join in sql
```
$ select Categories.categoryID, Categories.CategoryName,Categories.Description ,Products.ProductName,Products.UnitPrice
 from Categories left join Products on Categories.CategoryID=Products.ProductID
```

## use right join in sql
```
$ select Categories.categoryID, Categories.CategoryName,Categories.Description ,Products.ProductName,Products.UnitPrice
 from Categories right join Products on Categories.CategoryID=Products.ProductID
```
## use full join in sql
```
$ select Categories.categoryID, Categories.CategoryName,Categories.Description ,Products.ProductName,Products.UnitPrice
 from Categories full join Products on Categories.CategoryID=Products.ProductID
```

#  🚦  Sub Query in SQL

## from make subquery from one query with =
```
$ select ContactName , CompanyName from Customers
where CustomerID = (select top 1 CustomerID from Orders order by OrderID desc) 
```

## use subquery with in 
```
$ select ContactName , CompanyName from Customers
where CustomerID in (select  CustomerID from Orders )
```
## use subquery with where
```
$ select ContactName , CompanyName from Customers
where CustomerID in (select  CustomerID from Orders where OrderID=10550 )
```
#  🚦  Check in SQL

## use check in first time
```
$ create database test13
go
use test13
create table customers (customersID int not null, customerName nvarchar(50) , cridetlimit decimal(18,2)
,  constraint CK_limit check (cridetlimit <= 10000))
```

## use check after add table
```
$ alter table customers
add constraint CK_limit check (cridetlimit <= 10000)
```
## to delete check from column
```
$ use test
alter table customers
drop constraint CK_limit 
```

#  🚦  Union and Index in SQL

## use union in SQL
```
$ select Categories.CategoryName  from Categories
union
select Products.ProductName from Products
```

## use union all if want to show duplicate data in SQL
```
$ select Categories.CategoryName  from Categories
union all 
select Products.ProductName from Products
```
## use index in SQL
```
$ create index inx_Employee on employees(employeeid)
```
#  🚦  Views in SQL - use views only in report (To View Not Edit) because it is not updatable

## create new view 
```
$ use Northwind
go
create view test_product_view
as 
select * from Employees
```

## for show data from view
```
$ use Northwind
go
alter view  test_product_view
as
select * from [Order Details]
```
## for delete view 
```
$ drop view  test_product_view
```

#  🚦  Automatic Functions in MSQL

## to get datetime automatic in every rows
```
$ select GETDATE()
```

## to set default value 
```
$ ('Cairo')
```
## to get server name
```
$ select @@SERVERNAME
```

## to get service name
```
$ select @@VERSION
```

## to get version 
```
$ ('Cairo')
```
## to get how many connection to this server
```
$ select @@CONNECTIONS
```

## to get default language in server
```
$ select @@LANGUAGE
```

## use upper case 
```
$ select UPPER(FirstName) as 'FirstName', upper(LastName) as 'LastName' from Employees 

```
## use upper and lower case 
```
$ select UPPER(FirstName) + '' +LOWER (LastName) as fullName from Employees
```

## to get count of every character in column 
```
$ select len (firstname),firstname from Employees
```

## to take any charcher and make new column from left 
```
$ select left (firstname,3),firstname from Employees
```
## to take any charcher and make new column from right
```
$ select right(firstname,3),firstname from Employees
```

## to reverse characters from right to left
```
$  select stuff(firstname,1,3,LastName),firstname + ' ' + lastname from Employees

```
## use staff like union but in one table 
```
$ select UPPER(FirstName) + '' +LOWER (LastName) as fullName from Employees
```

## for count any recorders in table
```
$ select count (*)  from Orders 
$ select count (ShipAddress)  from Orders 
$ select count (ShipAddress)  from Orders where OrderID > 10525
```

## check what is max number in column 
```
$ select max(EmployeeID)from Orders
```
## check what is min number in column 
```
$ select min(EmployeeID)from Orders
```

## check what is avg number in column 
```
$ select avg(EmployeeID)from Orders
avg= total of numbers / count of all this numbers
```

## use sum in table
```
$ select sum(EmployeeID) from Employees
```
## sum quantity with product_id and discount in the same table
```
$ select sum(Quantity) ,ProductID ,Discount from [Order Details] group by ProductID ,Discount order by ProductID
```

## use sum quantity of product from another table
```
$ select sum(Quantity) ,a.ProductID ,a.Discount ,b.ProductName from [Order Details] a inner join Products b on a.ProductID = b.ProductID
 group by a.ProductID ,Discount ,ProductName order by a.ProductID
```
## use having like where but where dont use with group by
```
$ select sum(Quantity) ,a.ProductID ,a.Discount ,b.ProductName from [Order Details] a inner join Products b on a.ProductID = b.ProductID
 group by a.ProductID ,Discount ,ProductName having a.productid=1
```

## get what is company name biggest name in table use Max
```
$  select max(len(CompanyName)),CompanyName from Customers
```

## get what is company name biggest name in table 
```
$  select CompanyName from Customers order by len(companyName) desc
```
## get day function
```
$ select day('2018/11/29')
$ select day('getdate())
```

## get month function
```
$ select month('2018/11/29')
$ select month(getdate())
```
## get year function
```
$ select year('2018/11/29')
$ select year(getdate())
```

## to get what is day 
```
$ select datepart(WEEKDAY,GETDATE())  // number
$ select datepart(WEEKDAY,'2018/11/29')  // number	
$ select datename(WEEKDAY,GETDATE())  // text
```

## to increase any dayes to your date
```
$ select DATEADD(day,5, GETDATE())
$ select DATEADD(MONTH,5, GETDATE())
$ select DATEADD(MONTH,-1, GETDATE())
$ select DATEADD(YEAR,-1, GETDATE())
$ select DATENAME(weekday,dateadd(year,-1,getdate()))
```
## functions to get diffrents of date by convert.
```
$ select convert(nvarchar(10),getdate(),103)
$ select convert(nvarchar(8),getdate(),3)
$ select convert(nvarchar(20),getdate(),100)
$ select convert(nvarchar(10),getdate(),1)
$ select convert(nvarchar(10),getdate(),111)
$ select convert(nvarchar(8),getdate(),11)
```
## functions to get diffrents of date by cast
```
$ select cast (DAY(getdate()) as nvarchar(2)) + '/'+ cast( MONTH(GETDATE()) as nvarchar(2)) + '/'+ cast( year(GETDATE()) as nvarchar(4)) 
```

#  🚦  Loops in SQL

## to create loop
```
$ declare @Num int
set @Num =0

while @Num <=5
begin
print @Num
set @Num+=1
end

```
#  🚦  Custome Function in SQL
### Scalar-valued Function :point_left:

## create new function !!! if need to edit use  **   (alter)
```
$ use Northwind
go 
create function myfuncion()
returns int 
as
begin
return 7+12
end
```
## for get your function (dbo. 'this is call schima')
```
$ select dbo.myfuncion()
```
## use parameters in function
```
$ use Northwind
go 
alter function myfuncion(@num1 int, @num2 int)
returns int 
as
begin
return @num1+@num2
end

```

## use default value in parameters
```
$ alter function myfuncion(@num1 int =4, @num2 int)
returns int 
as
begin
return @num1+@num2
end
```

## to create function to select data
```
$ create function my_test()
returns int
begin
declare @myNum1 int
set @myNum1 =5

declare @my_Num2 int
select @my_Num2 =4

return @myNum1 + @my_Num2 

end
```

## get data from databse
```
$ alter function my_test()
returns int
begin
declare @myNum1 int
select @myNum1 = EmployeeID from Employees

return  @myNum1 
end
```
## to get data string
```
$ alter function my_test(@myid int)
returns nvarchar(50)
begin
declare @myNum1 nvarchar(50)
select @myNum1 = firstname +' '+ lastname from Employees where EmployeeID=@myid

return  @myNum1 
end
```
## use function (if condition ) in select table
```
$ alter function testif (@myCountry nvarchar(50) ,@myRegion nvarchar(50))
returns nvarchar (255)
begin
if (@myCountry is null )
return 'UNK'
else
if (@myCountry= 'usa' or @myCountry= 'canada' or @myCountry= 'mexico' )
return 'america'
else
return 'other country'
return @myCountry+ ''+ @myRegion
end
******************  and use like this
select  companyname , contactname ,dbo.testif(country,Region) from Customers 
```
## use function (case condition ) in select table
```
$ create function tesCase(@title nvarchar(15))
returns nvarchar (15)
begin
set @title =
case @title
when 'mr.'  then 'mester'
when 'ms.' then 'miss'
when 'dr.' then 'doctor'
else 'other'
end
return @title
end

************** and use like this
select  firstname , lastname ,TitleOfCourtesy,dbo.tesCase(TitleOfCourtesy) from Employees 
```

### table-valued Function :point_left:
## to make function to return table
```
$ create function testtable(@myname nvarchar(50) )
returns @TblTest table
(id int ,Name nvarchar(50) ,city nvarchar(50))
as
begin
insert into @TblTest select * from Names where city=@myname
return ;
end

************** and use like this

select * from dbo.@TblTest('ahmed')
```
