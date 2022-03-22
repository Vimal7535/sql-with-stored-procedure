# sql-with-stored-procedure




-------------------------------------------CREATE DATABASE-----------------------------------------------

USE MYDATABASE

------------------------------------------CREATE STORED PROCEDURE OF DISPLAY OF TABLE---------------------------

ALTER proc FINDDATA
AS
BEGIN
select * from student
end


FINDDATA

-----------------------------------CREATE STORED PROCEDURE OF INSERT THE DATA WITHOUT VALIDATION--------------------------------

alter proc INSERTDATA
@rollno int,
@f_name varchar(20),
@l_name varchar(20),
@address varchar(100),
@course varchar(30)
AS
BEGIN
insert into student(rollno,f_name,L_Name,Address,Course)values
(@rollno,@f_name,@l_name,@address,@course)
end


INSERTDATA  13,'VIMAL','KUMAR','BIJNOR','MCA'

----------------------------------------CREATE STORE PROCEDURE OF INSERT THE DATA WITH VALIDATION------------------------------

alter proc INSERTDATA
@rollno int,
@f_name varchar(20),
@l_name varchar(20),
@address varchar(100),
@course varchar(30)
AS
BEGIN
declare @validrollno int,@validf_name varchar(20),
@validl_name varchar(20),
@validaddress varchar(100),
@validcourse varchar(30);
select @validrollno=rollno  from student  where  rollno=@rollno 
if @validrollno > 0
begin 
select  'Already Exist the Rollno !'
end
else
begin
insert into student(rollno,f_name,L_Name,Address,Course)values
(@rollno,@f_name,@l_name,@address,@course)
end
end
select @validf_name=F_Name from student  where  F_Name=@f_name
if @validf_name <> 'null'
begin 
select  'Already Exist the Value of F_Name !'
end
else
begin
insert into student(rollno,f_name,L_Name,Address,Course)values
(@rollno,@f_name,@l_name,@address,@course)
end
select @validl_name=L_Name from student  where  L_Name=@l_name
if @validl_name <> 'null'
begin 
select  'Already Exist the Value of L_Name !'
end
else
begin
insert into student(rollno,f_name,L_Name,Address,Course)values
(@rollno,@f_name,@l_name,@address,@course)
end
select @validaddress=address from student where  address=@address
if @validaddress <> 'null'
begin 
select  'Already Exist the Value of Address !'
end
else
begin
insert into student(rollno,f_name,L_Name,Address,Course)values
(@rollno,@f_name,@l_name,@address,@course)
end
select @validcourse=Course from student  where  Course=@course
if @validcourse <> 'null'
begin 
select  'Already Exist the Value of Course !'
end
else
begin
insert into student(rollno,f_name,L_Name,Address,Course)values
(@rollno,@f_name,@l_name,@address,@course)
end

-------------------------------------USING OF DISPLAY THE TABLE THROUGH THE STORED PROCEDURE (FINDDATA)------------------------

FINDDATA

----------------------------------INSERT THE DATA THROUGH THE STORED PROCEDURE(INSERTDATA)------------------------------------

INSERTDATA 15,'chintu','singh','noida','mba'

---------------------------------------CREATE A STORED PROCEDURE OF DELETE THE DATA --------------------------------------

alter proc DELETEDATA
AS
BEGIN
DELETE  FROM student WHERE F_Name='ram'
END

-----------------------------------USING OF DELETE THE DATA IN A TABLE THROUGH THE STORED PROCEDURE(DELETEDATA)------------------

DELETEDATA
