# Mysql-Database-ex
create table, insert data and query
/*Ex 2.1
 1.Create a test_db database */
create database test_db; 
use test_db;

-- 2.create student table
create table student(
rollno int,
name varchar(30),
result varchar(20));

-- 3. show table
show tables;

-- 4.desc the structure of student table
desc student;

-- 5.add primary key to rollno 
alter table student add primary key(rollno);

-- 6.add a new column name address
alter table student add address varchar(20);

-- 7. drop a new column name address
alter table student drop column address;

-- 8. modify data type
alter table student modify result varchar(30);
desc student;

alter table student modify rollno int not null auto_increment;
-- 9. insert values
INSERT INTO student (name,result) VALUES('Aung Aung','Pass');
INSERT INTO student (name,result) VALUES('Ma Ma','Fail');
INSERT INTO student (name,result) VALUES('Su Su','Fail');
INSERT INTO student (name,result) VALUES('Yu Yu','Fail');
INSERT INTO student (name,result) VALUES('Su Su','Pass');

-- 10.retrieve all information
select* from student;

-- 11.retrieve distinct name
select distinct name from student;

-- 12. retrieve name and result
select distinct name, result from student;

-- 13.retrieve a student name is Ma Ma
select* from student where name='Ma Ma';

-- 14. retrieve a row that a student rollno 1
select* from student where rollno= 1;

-- 15.retrieve a row that student rollno is 5 and their result is pass
select * from student where rollno=5 and result='Pass';

-- 16.update the result of rollno 4 to pass
update student set result='Pass' where rollno=4;
select* from student;

-- 17.delete rollno 3 
delete from student where rollno=3;

-- 18.drop student table
drop table student;
show tables;

-- 19.drop test_db database
drop database test_db;
show databases;

/* Ex 2.2
1. create a university_db*/
create database university_db;
use university_db;

-- 2. create students table
create table students(
sid int primary key,
name varchar(30),
login varchar(30),
age int,
gpa float);
desc students;

 -- 3. create courses table
 create table courses(
cid varchar(20),
cname varchar(30),
credits int,
primary key(cid));
desc courses;


-- 4.create enrolled table
create table enrolled(
cid varchar(30),
grade varchar(10),
studid int,
primary key(cid,studid),
foreign key(cid) references courses(cid),
foreign key(studid) references students(sid));
 show tables;
 desc enrolled;

/* Ex2.3
1. insert students information */
INSERT INTO students (sid,name,login,age,gpa) VALUES(53666,'Jones','jones@cs',18,3.3);
INSERT INTO students (sid,name,login,age,gpa) VALUES(53668,'Smith','johne@ee',19,3.5);
INSERT INTO students (sid,name,login,age,gpa) VALUES(53831,'Madaya','maday@is',17,3.4);
INSERT INTO students (sid,name,login,age,gpa) VALUES(53832,'Guldu','guldu@ee',12,1.8);
INSERT INTO students (sid,name,login,age,gpa) VALUES(53833,'Smith','smith@cs',13,2);
select * from students;

-- insert data to course table
INSERT INTO courses (cid,cname,Credits) VALUES('Carnatic101','Carnatic',3);
INSERT INTO courses (cid,cname,Credits) VALUES('History105','History',3);
INSERT INTO courses (cid,cname,Credits) VALUES('Reggae203','Reggage',3);
INSERT INTO courses (cid,cname,Credits) VALUES('Topology112','Topology',2);
select * from courses;
 
-- insert data to enrolled table
INSERT INTO enrolled (cid,grade,studid) VALUES('Carnatic101','C',53666);
INSERT INTO enrolled (cid,grade,studid) VALUES('History105','B',53666);
INSERT INTO enrolled (cid,grade,studid) VALUES('Reggae203','B',53666);
INSERT INTO enrolled (cid,grade,studid) VALUES('Topology112','A',53668);
select * from enrolled;
