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
