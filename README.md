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


#  🚦  Stored Procedures in SQL
### ** dont use sp_ - with stored procedure because alot of sp_ in database after call performance not good , use any another keyword like (proc) :point_left:

## create first stored procedure
```
$ create procedure proc_test1
as
begin
select * from Employees
end

******* for use in sql server

 $ execute test1
 $ exec test1
```

## for run proc automatic
```
$ alter procedure proc_test1
as
begin
select * from Employees
end
go

******* for use in sql server
exec test1
```
## use insert with proc
```
$ alter procedure test1
as
begin
insert into  Employees (LastName,FirstName) values ('ahmed','midoo')
end
go

******* for use in sql server
exec test1
```
## use update with proc
```
$ alter proc test1
as
begin
update  Employees  set LastName= 'mohammed' ,FirstName='ali' where EmployeeID=14
end
go

******* for use in sql server
exec test1
```
## use delete with proc
```
$ alter proc test1
as
begin
delete from Employees  where EmployeeID=14
end
go

******* for use in sql server
exec test1
```
## use proc with parameters
```
$ alter proc test1 
@Num int 
as
begin
select * from Employees where EmployeeID = @Num
end
go

******** for use
	$ exec test1 2
```
## use proc for insert with parameter
```
$ alter proc test1 

@myName nvarchar(50),
@myCity nvarchar(50),
@myJobId int
as
begin
insert into Names(name,city,jobid) values (@myName,@myCity,@myJobId)
end
```
## use proc with if condition
```
$ alter proc test1 

@myName nvarchar(50),
@myCity nvarchar(50),
@myJobId int
as
begin
declare @Name2 nvarchar(50)
select @Name2 = Name from names where name=@myName

if not @Name2 is null
print 'Name is Not Valid'
else
insert into Names(name,city,jobid) values (@myName,@myCity,@myJobId)
end
go
```
## example 2 if with proc // check value from another table before insert data
```
$ alter proc test1 

@myName nvarchar(50),
@myCity nvarchar(50),
@myJobId int
as
begin
declare @Name2 int
select @Name2 = jobId from jobs where jobId=@myJobId

if @Name2 is null
print 'jobId is Not Valid'
else
insert into Names(name,city,jobid) values (@myName,@myCity,@myJobId)
end
go
```
## use proc with if another example
```
$ create proc testCalc
@my_Name int,
@my_Salary decimal(18,2),
@my_Bouns decimal(18,2),
@My_Dis decimal(18,2),
@MyNet decimal(18,2)
as
begin 
if @my_Salary < 1500 and  @my_Salary > 1000
set @my_Bouns = @my_Salary * 0.10 
else
if @my_Salary < 1000
set @my_Bouns = @my_Salary * 0.5

set @MyNet = @my_Salary+ @my_Bouns-@My_Dis

insert into salary (name, salary,bouns,dis,net)
 values (@my_Name,@my_Salary,@My_Dis,@MyNet)

***************** for use
	$ exec testCalc 2,1000,0,50,0 
```
## return value with proc -- return how many record in table
```
$ create proc testReturn
as
declare @Num as int
select * from Employees
set @Num= @@ROWCOUNT
return @Num
go

************** for use
	$ declare @count int
exec @count = testReturn
select @count
```
## use output param 
```
$ create proc testOutParam
@MyName nvarchar (50)
as
begin
select id from Names where Name=@MyName
end
************************* for use
	$ exec testOutParam 'ahmed'
```
## use output param and get param from stored procedure (static value)
```
$ create proc testOutParam
@MyName nvarchar (50),
@MyID int output
as
set @MyID=500
begin
select id from Names where Name=@MyName
end
************************* for use
	$ declare @NewId int
exec testOutParam 'ahmed' , @NewId output
select @NewId
```
## use output param and get param from stored procedure dynamic value)
```
$ create proc testOutParam
@MyName nvarchar (50),
@MyID int output
as
begin
select @MyID=id from Names where Name=@MyName
end
************************* for use
	$ declare @NewId int
exec testOutParam 'ahmed' , @NewId output
insert into salary (Name,salary,bouns,dis,net) vlaues
 (@NewId,1000,100,100,1000)
 select @NewId
select * from salary
```
## insert into 2 table by stored procedure
```
$ create proc testIdentity
@MyName nvarchar (50),
@MyCity nvarchar (50),
@MyJobId int ,
@MySalary decimal(18,2)

as
begin

declare @MyId int
declare @MyBouns decimal(18,2) = @MySalary * 0.05
declare @MyDis decimal(18,2) = @MySalary * 0.03
declare @MyNet decimal(18,2) = @MySalary + @MyBouns - @MyDis

insert into Names (name,city,jobID) values (@MyName,@MyCity,@MyJobId)

set @MyID = (select SCOPE_IDENTITY())
insert into salary (name,salary,bouns,dis ,net) values (@MyID,@MySalary,@MyBouns,@MyDis,@MyNet)

********************** for use
	$ exec testOutParam 'ahmed','cairo',1,10000

```
## transaction -update *in one time* from tabele to another table like 'Money between two acount in Bank' 
```
$ use Northwind
go
create proc testIdentity
@MyName nvarchar (50),
@MyCity nvarchar (50),
@MyJobId int ,
@MySalary decimal(18,2)
as
begin
declare @MyId int
declare @MyBouns decimal(18,2) = @MySalary * 0.05
declare @MyDis decimal(18,2) = @MySalary * 0.03
declare @MyNet decimal(18,2) = @MySalary + @MyBouns - @MyDis

begin try
	begin transaction

		insert into Names (name,city,jobID) values (@MyName,@MyCity,@MyJobId)
		set @MyID = (select SCOPE_IDENTITY())
		insert into salary (name,salary,bouns,dis ,net) values (@MyID,@MySalary,@MyBouns,@MyDis,@MyNet)

	commit transaction
end try

begin catch
	rollback tran
print error_message()
end catch
************************** for use
 $ exec testIdentity null ,'cairo',1,10000

```
#  🚦  Triggers in SQL
### *1* for (after) trigger  (tr_) -- for create,update,delete -- make after order only :point_left:

## for create triggers in insert data to table to record events
```
$ alter trigger InsertEmployee
on EmplyeeForTrigger
for insert
as
begin
declare @MyID int
declare @MyName nvarchar(50)

select @MyID = EmployeeID ,@MyName = EmployeeName from inserted

insert into tbl_Events (My_Events,EventData,EmployeeID,EmployeeName) values ('Insert' ,GETDATE(),@MyID,@MyName)

end

```
## for create trigger for delete
```
$ alter trigger DeleteEmployee
on EmplyeeForTrigger
for delete
as
begin
declare @My_Id int
declare @My_Name nvarchar(50)
select @My_Id = EmployeeID ,@My_Name = EmployeeName from deleted
insert into tbl_Events(My_Events,EventData,EmployeeID,EmployeeName) values ('delete',GETDATE(),@My_Id,@My_Name)
end
```
## for update trigger
```
$ create trigger tr_UpdateEmployee
on EmplyeeForTrigger
for update
as
begin
declare @My_Id int
declare @My_NewName nvarchar(50)
declare @My_OldName nvarchar(50)

select @My_Id = EmployeeID ,@My_OldName = EmployeeName from deleted
select @My_NewName = EmployeeName from inserted

   insert into tbl_Events(My_Events,EventData,EmployeeID,EmployeeName) values
   ('update',GETDATE(),@My_Id,'From' + @My_OldName + 'TO' + @My_NewName)
end
```
## for update trigger (multi update) 
```
$ alter trigger tr_UpdateEmployee
on EmplyeeForTrigger
for update
as
begin
	declare @MyID int
	declare @MyNewName nvarchar(50)
	declare @MyOldName nvarchar(50)
	declare @MyOldCity nvarchar(50)
	declare @MyNewCity nvarchar(50)
	declare @MyOldJobID int 
	declare @MyNewJobID int 
	declare @State nvarchar(1000)

	select * into #tem from inserted

	while (exists (select EmployeeID from #tem))
	begin
	set @state = ' '
	select top 1 @MyID=EmployeeID , @MyNewName=EmployeeName ,@MyNewCity = city ,@MyNewJobID=JobId from #tem
	select @MyOldName =EmployeeName ,@MyOldCity=city ,@MyOldJobID=JobId  from deleted where EmployeeID=@MyID

	set @State= 'update '

	if (@MyOldName <> @MyNewName)
	set @State=@State + ' Name ' + 'To' + @MyNewName 

	if(@MyOldCity <> @MyNewCity)
	set @State =@State + ' city ' + 'To ' + @MyNewCity

	if(@MyOldJobID <> @MyNewJobID)
	set @State=@State + ' JobID ' + 'To ' + cast(@MyNewJobID as nvarchar(50))

	insert into tbl_Events (My_Events,EventData,EmployeeID,EmployeeName) 
	values (@State,GETDATE() ,@MyID,@MyOldName)
	delete from #tem where EmployeeID=@MyID
	end
end

```
### Instead of Trigger --make after order and new order in behind :point_left:
## Instead of Trigger (delete)---after you make delete any employee dont delete but add false in active
```
$ alter trigger instToDeleEmployee
on EmplyeeForTrigger
instead of delete
as 
begin

	declare @MyID int
	select @MyID=EmployeeID from deleted
	update EmplyeeForTrigger set Active='False' where EmployeeID=@MyID

end
```
## insert --after you make insert in view -insert in tabels not in view because view it is not updatable.
```
$ create trigger instToInsertEmployee
on empdet_View
instead of insert
as 
begin
	declare @MyID int
	select @MyID=jobID from jobs a join inserted b on a.jobName =b.JobName
	
	if(@MyID is null)
	begin
	print 'not avalid job'
	return 
	end

	insert into employees(EmployeeName,city,jobId) select employeeName,city,@MyID from inserted

end
```
## update --after you make update in view -insert in tabels not in view because view it is not updatable.
```
$  create trigger instOfUpdateEmployee
on empdet_View
instead of update
as 
begin
		if(UPDATE(employeeId))
		begin
		print 'you cannot change ID'
		rollback  
		end

		if(UPDATE(jobname))
		begin
			declare @MyJobID int
			select @MyJobID=jobId from Jobs a join inserted b
			on a.jobname = b.jobname
		end

		if(@MyJobID is null)
		begin
			print 'Invalid Job Name'
			rollback
		end
			update Employees set JobId = @MyJobID
			from inserted a join Employees b
			on a.employeeId=b.employeeId
		end

		if(update(emplyeename))
		begin
			update Employees set employeename =a.employeename
			from inserted a join Employees b
			on a.employeeId=b.employeeId
		end

		if(UPDATE(city))
		begin 
			update Employees set City =a.city
			from inserted a join Employees b
			on a.employeeId=b.employeeId
		end
end
```
## Generating MS SQL Server database scripts for backup 
```
$server = "myserver.mydomain.com"
$database = "my_database"
$schema = "dbo"

$username = "my_user"
$password = "my_super_secure_pw"

$output_path = ("D:\ServerFolders\Sites\brechtbaekelandt\data\" + (Get-Date -UFormat "%Y\%m\%d"))
$table_path = "$output_path\Tables\"
$storedProcs_path = "$output_path\StoredProcedures\"
$triggers_path = "$output_path\Triggers\"
$views_path = "$output_path\Views\"
$udfs_path = "$output_path\UserDefinedFunctions\"
$textCatalog_path = "$output_path\FullTextCatalogs\"
$udtts_path = "$output_path\UserDefinedTableTypes\"

$onedrive_output_path = ("E:\OneDrive\Blog Backup\data\" + (Get-Date -UFormat "%Y\%m\%d"))
$onedrive_table_path = "$onedrive_output_path\Tables\"
$onedrive_storedProcs_path = "$onedrive_output_path\StoredProcedures\"
$onedrive_triggers_path = "$onedrive_output_path\Triggers\"
$onedrive_views_path = "$onedrive_output_path\Views\"
$onedrive_udfs_path = "$onedrive_output_path\UserDefinedFunctions\"
$onedrive_textCatalog_path = "$onedrive_output_path\FullTextCatalogs\"
$onedrive_udtts_path = "$onedrive_output_path\UserDefinedTableTypes\"

[System.Reflection.Assembly]::LoadWithPartialName("Microsoft.SqlServer.SMO") | out-null

$connectionString = ("Server=" + $server + ";Initial Catalog=" + $database + ";User ID=" + $username + ";Password=" + $password + ";Persist Security Info=True;")

Write-Host ("Creating server object with connectionstring" + $connectionString)
$srv = New-Object "Microsoft.SqlServer.Management.SMO.Server"
$conContext = $srv.ConnectionContext
$conContext.ConnectionString = $connectionString
$srv = New-Object "Microsoft.SqlServer.Management.SMO.Server" $conContext
$db = New-Object ("Microsoft.SqlServer.Management.SMO.Database")
$tbl = New-Object ("Microsoft.SqlServer.Management.SMO.Table")
$scripter = New-Object ("Microsoft.SqlServer.Management.SMO.Scripter") $srv

# Get the database and database objects
Write-Host "Getting database"
$db = $srv.Databases[$database]

Write-Host "Getting tables"
$tbl = $db.tables | Where-object { $_.schema -eq $schema  -and -not $_.IsSystemObject }

Write-Host "Getting stored procedures"
$storedProcs = $db.StoredProcedures | Where-object { $_.schema -eq $schema -and -not $_.IsSystemObject }

Write-Host "Getting triggers"
$triggers = $db.Triggers + ($tbl | % { $_.Triggers })

Write-Host "Getting views"
$views = $db.Views | Where-object { $_.schema -eq $schema }

Write-Host "Getting user defined functions"
$udfs = $db.UserDefinedFunctions | Where-object { $_.schema -eq $schema -and -not $_.IsSystemObject }

Write-Host "Getting full text catalogs"
$catlog	= $db.FullTextCatalogs

Write-Host "Getting user defined table types"
$udtts = $db.UserDefinedTableTypes | Where-object { $_.schema -eq $schema }

# Set scripter options
Write-Host "Setting the options"
$scripter.Options.ScriptSchema = $true
$scripter.Options.ScriptData = $true
$scripter.Options.NoCommandTerminator = $false
$scripter.Options.ToFileOnly = $true
$scripter.Options.AllowSystemObjects = $false
$scripter.Options.Permissions = $true
$scripter.Options.DriAllConstraints = $true
$scripter.Options.SchemaQualify = $true
$scripter.Options.AnsiFile = $true
$scripter.Options.SchemaQualifyForeignKeysReferences = $true
$scripter.Options.Indexes = $true
$scripter.Options.DriIndexes = $true
$scripter.Options.DriClustered 	= $true
$scripter.Options.DriNonClustered = $true
$scripter.Options.NonClusteredIndexes = $true
$scripter.Options.ClusteredIndexes = $true
$scripter.Options.FullTextIndexes = $true
$scripter.Options.EnforceScriptingOptions = $true

function CopyObjectsToFiles($objects, $outDir) {
	if (-not (Test-Path $outDir)) {
		[System.IO.Directory]::CreateDirectory($outDir)
	}

	foreach ($o in $objects) { 
		if ($null -ne $o) {
		
			$schemaPrefix = ""			

			if ($null -ne $o.Schema -and $o.Schema -ne "") {
				$schemaPrefix = $o.Schema + "."
			}

			$scripter.Options.FileName = $outDir + $schemaPrefix + $o.Name + ".sql"

			Write-Host ("Writing " + $scripter.Options.FileName)

			$scripter.EnumScript($o)
		}
	}
}

# Output the scripts
Write-Host ("Starting backup script generation on server-brecht " + $output_path)
CopyObjectsToFiles $tbl $table_path
CopyObjectsToFiles $storedProcs $storedProcs_path
CopyObjectsToFiles $triggers $triggers_path
CopyObjectsToFiles $views $views_path
CopyObjectsToFiles $catlog $textCatalog_path
CopyObjectsToFiles $udtts $udtts_path
CopyObjectsToFiles $udfs $udfs_path
Write-Host ("Finished backup script generation on server-brecht at " + (Get-Date))

Write-Host ("Starting backup script generation on onedrive " + $onedrive_output_path)
CopyObjectsToFiles $tbl $onedrive_table_path
CopyObjectsToFiles $storedProcs $onedrive_storedProcs_path
CopyObjectsToFiles $triggers $onedrive_triggers_path
CopyObjectsToFiles $views $onedrive_views_path
CopyObjectsToFiles $catlog $onedrive_textCatalog_path
CopyObjectsToFiles $udtts $onedrive_udtts_path
CopyObjectsToFiles $udfs $onedrive_udfs_path
Write-Host ("Finished backup script generation on onedrive at " + (Get-Date))


******************* The output paths in this example will be:
D:\ServerFolders\Sites\brechtbaekelandt\data\2018\10\28
E:\OneDrive\Blog Backup\data\2018\10\28

******************* This script also generates the schema and data because I specified these two lines:
$scripter.Options.ScriptSchema = $true
$scripter.Options.ScriptData = $true

```
#  🚦   Tricks.
## show all database in your system
```
$ select * from master..sysdatabases
```
## check if database fond or not found
```
$ if exists(select * from master..sysdatabases where name='testDb')
print 'db exists'

else
create database testdb

```
## create random numbers
```
$ declare @Mynum int;
declare @Mymax int;
declare @Mymin int

set @Mymin=1
set @Mymax=1000000

select @Mynum =ROUND((@Mymin - @Mymax-1) * rand() *(-1) ,0)
print @Mynum

********* small method
$ SELECT Cast(RAND()*(100000-1)+1 as int);
```
## to reseed identity in table
```
$ dbcc checkident(table1 ,reseed ,0)
```
#  🚦   50 Important Queries In SQL Server.
## Query 1: Retrieve List of All Database
```
$ EXEC sp_helpdb  
```
## Query 1: Retrieve List of All Database
```
$ EXEC sp_helpdb  
```
## Query 2: Display Text of Stored Procedure, Trigger, View

```
$ exec sp_helptext @objname = 'Object_Name'  

```
## Query 3: Get All Stored Procedure Relate To Database

```
$ SELECT DISTINCT o.name, o.xtype  
  
FROM syscomments c  
  
INNER JOIN sysobjects o ON c.id=o.id  
  
WHERE o.xtype='P'  
***************** 
To retrieve the View use “V” instead of “P” and for functions use “FN.

```
## Query 4: Get All Stored Procedure Relate To Table

```
$ SELECT DISTINCT o.name, o.xtype  
  
FROM syscomments c  
  
INNER JOIN sysobjects o ON c.id=o.id  
  
WHERE c.TEXT LIKE '%Table_Name%' AND o.xtype='P'  

```
## Query 5: Rebuild All Index of Database

```
$ EXEC sp_MSforeachtable @command1="print '?' DBCC DBREINDEX ('?', ' ', 80)"  
  
GO  
  
EXEC sp_updatestats  
  
GO

```
## Query 6: Retrieve All dependencies of Stored Procedure

```
******** This query return all objects name that are using into stored procedure like table, user define function, another stored procedure.

$ ;WITH stored_procedures AS (  
  
SELECT  
  
oo.name AS table_name,  
  
ROW_NUMBER() OVER(partition by o.name,oo.name ORDER BY o.name,oo.name) AS row  
  
FROM sysdepends d  
  
INNER JOIN sysobjects o ON o.id=d.id  
  
INNER JOIN sysobjects oo ON oo.id=d.depid  
  
WHERE o.xtype = 'P' AND o.name LIKE '%SP_NAme%' )  
  
SELECT Table_name FROM stored_procedures  
  
WHERE row = 1  
  
```
## Query 7: Find Byte Size Of All tables in database

```
$ SELECT sob.name AS Table_Name,  
  
SUM(sys.length) AS [Size_Table(Bytes)]  
  
FROM sysobjects sob, syscolumns sys  
  
WHERE sob.xtype='u' AND sys.id=sob.id  
  
GROUP BY sob.name

```
## Query 8: Get all table that don’t have identity column

```
$ SELECT  
  
TABLE_NAME FROM INFORMATION_SCHEMA.TABLES  
  
where  
  
Table_NAME NOT IN  
  
(  
  
SELECT DISTINCT c.TABLE_NAME FROM INFORMATION_SCHEMA.COLUMNS c  
  
INNER  
  
JOIN sys.identity_columns ic  
  
on  
  
(c.COLUMN_NAME=ic.NAME))  
  
AND  
  
TABLE_TYPE ='BASE TABLE'  

```
## Query 9: List of Primary Key and Foreign Key for Whole Database

```
$ SELECT  
  
DISTINCT  
  
Constraint_Name AS [Constraint],  
  
Table_Schema AS [Schema],  
  
Table_Name AS [TableName] FROM INFORMATION_SCHEMA.KEY_COLUMN_USAGE  
  
GO

```
## Query 10: List of Primary Key and Foreign Key for a particular table

```
$ SELECT  
  
DISTINCT  
  
Constraint_Name AS [Constraint],  
  
Table_Schema AS [Schema],  
  
Table_Name AS [TableName] FROM INFORMATION_SCHEMA.KEY_COLUMN_USAGE  
  
WHERE INFORMATION_SCHEMA.KEY_COLUMN_USAGE.TABLE_NAME='Table_Name'  
  
GO

```
## Query 11: RESEED Identity of all tables

```
$ EXEC sp_MSForEachTable '  
  
IF OBJECTPROPERTY(object_id(''?''), ''TableHasIdentity'') = 1  
  
DBCC CHECKIDENT (''?'', RESEED, 0) 
  
```
## Query 12: List of tables with number of records

```
$ CREATE TABLE #Tab  
  
(  
  
Table_Name [varchar](max),  
  
Total_Records int  
  
);  
  
EXEC sp_MSForEachTable @command1=' Insert Into #Tab(Table_Name, Total_Records) SELECT ''?'', COUNT(*) FROM ?'  
  
SELECT * FROM #Tab t ORDER BY t.Total_Records DESC;  
  
DROP TABLE #Tab;  
  
```
## Query 13: Get the version name of SQL Server

```
$ SELECT @@VERSION AS Version_Name  
  
```
## Query 14: Get Current Language of SQL Server

```
$ SELECT @@LANGUAGE AS Current_Language;  
  
```
## Query 15: Disable all constraints of a table

```
$ ALTER TABLE Table_Name NOCHECK CONSTRAINT ALL  

```
## Query 16: Disable all constraints of all tables

```
$ EXEC sp_MSForEachTable 'ALTER TABLE ? NOCHECK CONSTRAINT ALL'  
  
```
## Query 17: Get Current Language Id

```
$ SELECT @@LANGID AS 'Language ID'  
  
```
## Query 18: Get precision level used by decimal and numeric as current set in Server

```
$ SELECT @@MAX_PRECISION AS 'MAX_PRECISION'  
  
```
## Query 19: Return Server Name of SQL Server

```
$ SELECT @@SERVERNAME AS 'Server_Name'  
  
```
## Query 20: Get name of register key under which SQL Server is running

```
$ SELECT @@SERVICENAME AS 'Service_Name'

```
## Query 21: Get Session Id of current user process

```
$ SELECT @@SPID AS 'Session_Id'
  
```
## Query 22: Get Current Value of TEXTSIZE option

```
$ SELECT @@TEXTSIZE AS 'Text_Size'  
  
```
## Query 23: Retrieve Free Space of Hard Disk

```
$ EXEC master..xp_fixeddrives  
  
```
## Query 24: Disable a Particular Trigger

```
$ ALTER TABLE Table_Name DISABLE TRIGGER Trigger_Name  

Example
 
ALTER TABLE Employee DISABLE TRIGGER TR_Insert_Salary  

  
```
## Query 25: Enable a Particular Trigger

```
$ ALTER TABLE Table_Name ENABLE TRIGGER Trigger_Name  

Example
 
ALTER TABLE Employee ENABLE TRIGGER TR_Insert_Salary  

  
```
## Query 26: Disable All Trigger of a table

```
**  We can disable and enable all triggers of a table using previous query, but replacing the "ALL" instead of trigger name.

$ ALTER TABLE Table_Name DISABLE TRIGGER ALL  

Example
 
ALTER TABLE Demo DISABLE TRIGGER ALL  
```
## Query 27: Enable All Trigger of a table

```
** Using sp_msforeachtable system stored procedure we enable and disable all triggers for a database.

$ ALTER TABLE Table_Name ENABLE TRIGGER ALL  
  
  Example
 
ALTER TABLE Demo ENABLE TRIGGER ALL  

```
## Query 28: Disable All Trigger for database

```
** Using sp_msforeachtable system stored procedure we enable and disable all triggers for a database.

$ Use Database_Name  
  
Exec sp_msforeachtable "ALTER TABLE ? DISABLE TRIGGER all"  
  
```
## Query 29: Enable All Trigger for database

```
$ Use Demo  
  
Exec sp_msforeachtable "ALTER TABLE ? ENABLE TRIGGER all"  
  
```
## Query 30: List of Stored procedure modified in last N days

```
$ SELECT name,modify_date  
  
FROM sys.objects  
  
WHERE type='P'  
  
AND DATEDIFF(D,modify_date,GETDATE())< N  
  
```
## Query 31: List of Stored procedure created in last N days

```
$ SELECT name,sys.objects.create_date  
  
FROM sys.objects  
  
WHERE type='P'  
  
AND DATEDIFF(D,sys.objects.create_date,GETDATE())< N  
  
```
## Query 32: Recompile a stored procedure

```
$ EXEC sp_recompile'Procedure_Name';  
  
GO  

```
## Query 33: Recompile all stored procedure on a table

```
$ EXEC sp_recompile N'Table_Name';  
  
GO  
  
```
## Query 34: Get all columns of a specific data type

```
$ SELECT OBJECT_NAME(c.OBJECT_ID) as Table_Name, c.name as Column_Name  
  
FROM sys.columns AS c  
  
JOIN sys.types AS t ON c.user_type_id=t.user_type_id  
  
WHERE t.name = 'Data_Type'  
 
```
## Query 35: Get all Nullable columns of a table

```
$ SELECT OBJECT_NAME(c.OBJECT_ID) as Table_Name, c.name as Column_Name  
  
FROM sys.columns AS c  
  
JOIN sys.types AS t ON c.user_type_id=t.user_type_id  
  
WHERE c.is_nullable=0 AND OBJECT_NAME(c.OBJECT_ID)='Table_Name'  

```
## Query 36: Get All table that don’t have primary key

```
$ SELECT name AS Table_Name  
  
FROM sys.tables  
  
WHERE OBJECTPROPERTY(OBJECT_ID,'TableHasPrimaryKey') = 0  
  
ORDER BY Table_Name;  

```
## Query 37: Get All table that don’t have foreign key

```
$ SELECT name AS Table_Name  
  
FROM sys.tables  
  
WHERE OBJECTPROPERTY(OBJECT_ID,'TableHasForeignKey') = 0  
  
ORDER BY Table_Name;  

```
## Query 38: Get All table that don’t have identity column

```
$ SELECT name AS Table_Name  
  
FROM sys.tables  
  
WHERE OBJECTPROPERTY(OBJECT_ID,'TableHasIdentity') = 0  
  
ORDER BY Table_Name;  
  
```
## Query 39: Get First Date of Current Month

```
$ SELECT CONVERT(VARCHAR(25),DATEADD(DAY,-(DAY(GETDATE()))+1,GETDATE()),105) First_Date_Current_Month;  
  
```
## Query 40: Get last date of previous month

```
$ SELECT CONVERT(VARCHAR(25),DATEADD(DAY,-(DAY(GETDATE())),GETDATE()),105) Last_Date_Previous_Month;  
  
```
## Query 41: Get last date of current month

```
$ SELECT CONVERT(VARCHAR(25),DATEADD(DAY,-(DAY(GETDATE())), DATEADD(MONTH,1,GETDATE())),105) Last_Date_Current_Month;  
  
```
## Query 42: Get first date of next month

```
$ SELECT CONVERT(VARCHAR(25),DATEADD(DAY,-(DAY(GETDATE())), DATEADD(MONTH,1,GETDATE())+1),105) First_Date_Next_Month;  
  
```
## Query 43: Swap the values of two columns

```
$ UPDATE Table_Name SET Column1=Column2, Column2=Column1  

```
## Query 44: Remove all stored procedure from database

```
$ Declare @Drop_SP Nvarchar(MAX)  
  
Declare My_Cursor Cursor For Select [name] From sys.objects where type = 'p'  
  
Open My_Cursor  
  
Fetch Next From My_Cursor Into @Drop_SP  
  
While @@FETCH_STATUS= 0  
  
Begin  
  
Exec('DROP PROCEDURE ' + @Drop_SP)  
  
Fetch Next From My_Cursor Into @Drop_SP  
  
End  
  
Close My_Cursor  
  
Deallocate My_Cursor  
  
```
## Query 45: Remove all views from database

```
$ Declare @Drop_View Nvarchar(MAX)  
  
Declare My_Cursor Cursor For Select [name] From sys.objects where type = 'v'  
  
Open My_Cursor  
  
Fetch Next From My_Cursor Into @Drop_View  
  
While @@FETCH_STATUS = 0  
  
Begin  
  
Exec('DROP VIEW ' + @Drop_View)  
  
Fetch Next From My_Cursor Into @Drop_View  
  
End  
  
Close My_Cursor  
  
Deallocate My_Cursor  
 
  
```
## Query 46: Drop all tables

```
$ EXEC sys.sp_MSforeachtable @command1 = 'Drop Table ?'  

```
## Query 47: Get information of tables’ columns

```
$ SELECT * FROM INFORMATION_SCHEMA.COLUMNS  
  
WHERE INFORMATION_SCHEMA.COLUMNS.TABLE_NAME=’Table_Name’  

```
## Query 48: Get all columns contain any constraints

```
$ SELECT TABLE_NAME,COLUMN_NAME,CONSTRAINT_NAME FROM INFORMATION_SCHEMA.CONSTRAINT_COLUMN_USAGE  

```
## Query 49: Get all tables that contain a view

```
$ SELECT * FROM INFORMATION_SCHEMA.VIEW_TABLE_USAGE  

```
## Query 50: Get all columns of table that using in views

```
$ SELECT * FROM INFORMATION_SCHEMA.VIEW_COLUMN_USAGE  
  
```

## for Contact

``
agmghazi@hotmail.com
``
``
https://www.facebook.com/agmghazi/
``
``
https://www.linkedin.com/in/agmghazi/
``
