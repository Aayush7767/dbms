Q1. Write a SQL statement to create a table Country with fields
Country_Id, Country_Name and Region_Id. Insert 2 records in the table
and display the table. Then delete one record from the table.
ANS.
create database practice;
Query OK, 1 row affected (0.01 sec)
mysql> use practice;
Database changed
mysql> create table Country(Country_Id int primary key ,Country_Name
varchar(50),Region_Id int);
Query OK, 0 rows affected (0.03 sec)
mysql> insert into Country values(101,"India",01);
Query OK, 1 row affected (0.01 sec)
mysql> insert into Country values(102,"Canada",02);
Query OK, 1 row affected (0.01 sec)
mysql> select * from Country;
+------------+--------------+-----------+
| Country_Id | Country_Name | Region_Id |
+------------+--------------+-----------+
| 101 | India | 1 |
| 102 | Canada | 2 |
+------------+--------------+-----------+
2 rows in set (0.00 sec)
mysql> delete from Country where Country_Id=102;
Query OK, 1 row affected (0.01 sec)
mysql> select * from Country;
+------------+--------------+-----------+
| Country_Id | Country_Name | Region_Id |
+------------+--------------+-----------+
| 101 | India | 1 |
+------------+--------------+-----------+
1 row in set (0.00 sec)
Q2. Write a SQL statement to create a table Student with fields
Roll-No, Name and Marks. Insert 3 records in the table and arrange the
records in ascending order. Display the table.
ANS.
mysql> create table Students (Roll_no int primary key,Name
varchar(50),Marks int);
Query OK, 0 rows affected (0.02 sec)
mysql> insert into Students
values(101,"Sachin",80),(102,"Virat",90),(103,"Virendra",70);
Query OK, 3 rows affected (0.01 sec)
Records: 3 Duplicates: 0 Warnings: 0
mysql> select * from Students order by Name asc;
+---------+----------+-------+
| Roll_no | Name | Marks |
+---------+----------+-------+
| 101 | Sachin | 80 |
| 102 | Virat | 90 |
| 103 | Virendra | 70 |
+---------+----------+-------+
3 rows in set (0.00 sec)
Q3. Write a SQL statement to create a table Department with fields
Deptid, Deptname, Location. Create a table Employee with fields
Emp_Id, Ename, Salary and Did as foreign key. Describe both tables and
insert one record in each table.
ANS.
mysql> create table employee(Emp_id int primary key , Ename
varchar(20),Salary int , Dept_id int);
Query OK, 0 rows affected (0.02 sec)
mysql> create table department(Location Varchar(20) , Dept_name
varchar(20), Dept_id int primary key);
Query OK, 0 rows affected (0.02 sec)
mysql> desc department;
+-----------+-------------+------+-----+---------+-------+
| Field | Type | Null | Key | Default | Extra |
+-----------+-------------+------+-----+---------+-------+
| Location | varchar(20) | YES | | NULL | |
| Dept_name | varchar(20) | YES | | NULL | |
| Dept_id | int | NO | PRI | NULL | |
+-----------+-------------+------+-----+---------+-------+
3 rows in set (0.00 sec)
mysql> alter table employee
 -> add foreign key(Dept_id)
 -> references department(Dept_id);
Query OK, 0 rows affected (0.05 sec)
Records: 0 Duplicates: 0 Warnings: 0
mysql> desc employee;
+---------+-------------+------+-----+---------+-------+
| Field | Type | Null | Key | Default | Extra |
+---------+-------------+------+-----+---------+-------+
| Emp_id | int | NO | PRI | NULL | |
| Ename | varchar(20) | YES | | NULL | |
| Salary | int | YES | | NULL | |
| Dept_id | int | YES | MUL | NULL | |
+---------+-------------+------+-----+---------+-------+
4 rows in set (0.00 sec)
mysql> insert into department values("1st Floor","Admin",01);
Query OK, 1 row affected (0.01 sec)
mysql> insert into employee values(101,"Sachin",50000,01);
Query OK, 1 row affected (0.00 sec)
mysql> select * from department;
+-----------+-----------+---------+
| Location | Dept_name | Dept_id |
+-----------+-----------+---------+
| 1st Floor | Admin | 1 |
+-----------+-----------+---------+
1 row in set (0.00 sec)
mysql> select * from employee;
+--------+--------+--------+---------+
| Emp_id | Ename | Salary | Dept_id |
+--------+--------+--------+---------+
| 101 | Sachin | 50000 | 1 |
+--------+--------+--------+---------+
1 row in set (0.00 sec)
Q4. Write a SQL statement to create a table Employee with fields
Emp_Id, Ename, Deptname and Salary.Insert two records in a table.
Write an SQL query to display details of Employees with department
name as “Admin”.
ANS.
NOTE: Same as above query instruction for creating table and insertion
of values.
mysql> select * from employee;
+--------+-----------------+-----------+--------+
| Emp_id | Ename | Dept_name | Salary |
+--------+-----------------+-----------+--------+
| 101 | M.S Dhoni | Software | 50000 |
| 108 | Rohit Sharma | Admin | 75000 |
+--------+-----------------+-----------+--------+
4 rows in set (0.00 sec)
mysql> select * from employee where Dept_name = "Admin";
+--------+--------------+-----------+--------+
| Emp_id | Ename | Dept_name | Salary |
+--------+--------------+-----------+--------+
| 108 | Rohit Sharma | Admin | 75000 |
+--------+--------------+-----------+--------+
1 row in set (0.00 sec)
Q5.Write a SQL statement to create a table Book with fields
Book_Id as a primary key, Book_Name, Author and Publisher.
Insert 2 records in the table and display the table. Display those
book details whose Book_Name starts with letter D.
ANS.
mysql> create table Book (Book_id int primary key , Book_Name
varchar(20),Author varchar(20),Publisher varchar(20));
Query OK, 0 rows affected (0.02 sec)
mysql> insert into Book values(101,"DBMS","RG","Basic of
DBMS"),(102,"OS","SD","Operating System");
Query OK, 2 rows affected (0.01 sec)
Records: 2 Duplicates: 0 Warnings: 0
mysql> select * from Book;
+---------+-----------+--------+------------------+
| Book_id | Book_Name | Author | Publisher |
+---------+-----------+--------+------------------+
| 101 | DBMS | RG | Basic of DBMS |
| 102 | OS | SD | Operating System |
+---------+-----------+--------+------------------+
2 rows in set (0.00 sec)
mysql> select * from Book where Book_Name like "D%";
+---------+-----------+--------+---------------+
| Book_id | Book_Name | Author | Publisher |
+---------+-----------+--------+---------------+
| 101 | DBMS | RG | Basic of DBMS |
+---------+-----------+--------+---------------+
1 row in set (0.00 sec)
Q6. Write a SQL statement to create a table Book with fields
Book_Id, Book_Name, Author and Publisher. Insert 2 records in the
table and display the table.Write an SQL query to display book names
in ascending order.
ANS.
NOTE: Same as above query instruction for creating table and insertion
of values.
mysql> select * from Book order by Book_Name asc;
+---------+-----------+--------+------------------+
| Book_id | Book_Name | Author | Publisher |
+---------+-----------+--------+------------------+
| 101 | DBMS | RG | Basic of DBMS |
| 102 | OS | SD | Operating System |
+---------+-----------+--------+------------------+
2 rows in set (0.00 sec)
ANS.
mysql> desc employee;
+---------+-------------+------+-----+---------+-------+
| Field | Type | Null | Key | Default | Extra |
+---------+-------------+------+-----+---------+-------+
| Emp_id | int | NO | PRI | NULL | |
| Ename | varchar(20) | YES | | NULL | |
| Salary | int | YES | | NULL | |
| Dept_id | int | YES | MUL | NULL | |
| job | varchar(30) | YES | | NULL | |
+---------+-------------+------+-----+---------+-------+
5 rows in set (0.00 sec)
mysql> alter table employee
 -> add experience int;
Query OK, 0 rows affected (0.02 sec)
Records: 0 Duplicates: 0 Warnings: 0
mysql> desc employee;
+------------+-------------+------+-----+---------+-------+
| Field | Type | Null | Key | Default | Extra |
+------------+-------------+------+-----+---------+-------+
| Emp_id | int | NO | PRI | NULL | |
| Ename | varchar(20) | YES | | NULL | |
| Salary | int | YES | | NULL | |
| Dept_id | int | YES | MUL | NULL | |
| job | varchar(30) | YES | | NULL | |
| experience | int | YES | | NULL | |
+------------+-------------+------+-----+---------+-------+
6 rows in set (0.00 sec)
ANS.
mysql> alter table employee
 -> modify job varchar(20);
Query OK, 1 row affected (0.06 sec)
Records: 1 Duplicates: 0 Warnings: 0
mysql> desc employee;
+------------+-------------+------+-----+---------+-------+
| Field | Type | Null | Key | Default | Extra |
+------------+-------------+------+-----+---------+-------+
| Emp_id | int | NO | PRI | NULL | |
| Ename | varchar(20) | YES | | NULL | |
| Salary | int | YES | | NULL | |
| Dept_id | int | YES | MUL | NULL | |
| job | varchar(20) | YES | | NULL | |
| experience | int | YES | | NULL | |
+------------+-------------+------+-----+---------+-------+
6 rows in set (0.00 sec)
Q9. Write a SQL statement to create a table Student with fields
Roll-No, Name and Marks.
Insert 2 records in the table.
Update student marks as 70 whose Roll_No is 102.
Display the table.
ANS.
Note: Same as Q2
mysql> select * from students;
+---------+----------+-------+
| Roll_no | Name | Marks |
+---------+----------+-------+
| 101 | Sachin | 80 |
| 102 | Virat | 90 |
| 103 | Virendra | 70 |
+---------+----------+-------+
3 rows in set (0.00 sec)
mysql> update students set Marks=70 where Roll_no=102;
Query OK, 1 row affected (0.01 sec)
Rows matched: 1 Changed: 1 Warnings: 0
mysql> select * from students;
+---------+----------+-------+
| Roll_no | Name | Marks |
+---------+----------+-------+
| 101 | Sachin | 80 |
| 102 | Virat | 70 |
| 103 | Virendra | 70 |
+---------+----------+-------+
3 rows in set (0.00 sec)
Q10.Write a SQL statement to create a table Student with fields
Roll_No, Name and marks of sub1, sub2 and sub3. Insert 3 records in
the table.Display roll no and average marks of subjects for each
student.
ANS.
mysql> CREATE TABLE Student (Roll_No INT PRIMARY KEY,Name
VARCHAR(50),Sub1 INT,Sub2 INT,Sub3 INT);
Query OK, 0 rows affected (0.02 sec)
mysql> INSERT INTO Student (Roll_No, Name, Sub1, Sub2, Sub3) VALUES(1,
'Alice', 80, 75, 85), (2, 'Bob', 90, 85, 80), (3, 'Charlie', 75, 70,
80);
Query OK, 3 rows affected (0.01 sec)
Records: 3 Duplicates: 0 Warnings: 0
mysql> SELECT * FROM Student;
+---------+---------+------+------+------+
| Roll_No | Name | Sub1 | Sub2 | Sub3 |
+---------+---------+------+------+------+
| 1 | Alice | 80 | 75 | 85 |
| 2 | Bob | 90 | 85 | 80 |
| 3 | Charlie | 75 | 70 | 80 |
+---------+---------+------+------+------+
3 rows in set (0.00 sec)
mysql> SELECT Roll_No, Name, (Sub1 + Sub2 + Sub3) / 3 AS Average_Marks
 -> FROM Student;
+---------+---------+---------------+
| Roll_No | Name | Average_Marks |
+---------+---------+---------------+
| 1 | Alice | 80.0000 |
| 2 | Bob | 85.0000 |
| 3 | Charlie | 75.0000 |
+---------+---------+---------------+
3 rows in set (0.00 sec)
Q11. Write a SQL statement to create a table Student with fields
Roll_No, Name and marks of sub1, sub2 and sub3.
Insert 3 records in the table.
Display roll no and maximum marks of subject for each student.
ANS.
mysql> SELECT Roll_No, Name, MAX(Sub1) AS Max_Sub1, MAX(Sub2) AS
Max_Sub2, MAX(Sub3) AS Max_Sub3 FROM Student GROUP BY Roll_No, Name;
+---------+---------+----------+----------+----------+
| Roll_No | Name | Max_Sub1 | Max_Sub2 | Max_Sub3 |
+---------+---------+----------+----------+----------+
| 1 | Alice | 80 | 75 | 85 |
| 2 | Bob | 90 | 85 | 80 |
| 3 | Charlie | 75 | 70 | 80 |
+---------+---------+----------+----------+----------+
3 rows in set (0.00 sec)
Q12. For bank database, create table Borrower with fields
Customer_Name, Loan_No and Loan_Amt. Insert 2 records in each table.
Display Customer details who are having loan amount more than ₹100000.
ANS.
mysql> create table borrower (Customer_Name varchar(30),Loan_No
int,Loan_Amt int );
Query OK, 0 rows affected (0.02 sec)
mysql> insert into borrower
values("Sachin",201,100000),("Rahul",290,99999);
Query OK, 2 rows affected (0.01 sec)
Records: 2 Duplicates: 0 Warnings: 0
mysql> insert into borrower values("Virendra",210,110000);
Query OK, 1 row affected (0.00 sec)
mysql> select * from borrower where Loan_Amt >100000;
+---------------+---------+----------+
| Customer_Name | Loan_No | Loan_Amt |
+---------------+---------+----------+
| Virendra | 210 | 110000 |
+---------------+---------+----------+
1 row in set (0.00 sec)
Q13For bank database Create table Depositor with fields Customer_Name
and Account_No. Create table Borrower with fields Customer_name and
Loan_no. Insert 2 records in each table. Execute natural join
operation and display the result.
ANS.
mysql> create table borrower (Customer_Name varchar(30),Loan_No int);
Query OK, 0 rows affected (0.02 sec)
mysql> insert into borrower values("Sachin",201),("Rahul",290);
Query OK, 2 rows affected (0.01 sec)
Records: 2 Duplicates: 0 Warnings: 0
mysql> insert into borrower values("Virendra",210);
Query OK, 1 row affected (0.00 sec)
mysql> create table depositor (Customer_Name varchar(20),Account_No
int);
Query OK, 0 rows affected (0.02 sec)
mysql> insert into depositor values ("Sachin",11111);
Query OK, 1 row affected (0.01 sec)
mysql> insert into depositor values
("Rahul",12121),("Virendra",134526);
Query OK, 2 rows affected (0.01 sec)
Records: 2 Duplicates: 0 Warnings: 0
mysql> select * from depositor natural join borrower;
+---------------+------------+---------+
| Customer_Name | Account_No | Loan_No |
+---------------+------------+---------+
| Sachin | 11111 | 201 |
| Rahul | 12121 | 290 |
| Virendra | 134526 | 210 |
+---------------+------------+---------+
3 rows in set (0.00 sec)
Q14. For bank database
Create table Depositor with fields Customer_name and Account_no.
Insert 2 records in each table. Write an SQL query to fetch unique
values of Customer names from depositor table.
ANS.
mysql> insert into depositor values ("Sachin",16789);
Query OK, 1 row affected (0.01 sec)
mysql> select * from depositor;
+---------------+------------+
| Customer_Name | Account_No |
+---------------+------------+
| Sachin | 11111 |
| Rahul | 12121 |
| Virendra | 134526 |
| Sachin | 16789 |
+---------------+------------+
4 rows in set (0.00 sec)
mysql> select distinct(Customer_Name) from depositor;
+---------------+
| Customer_Name |
+---------------+
| Sachin |
| Rahul |
| Virendra |
+---------------+
3 rows in set (0.00 sec)
Q. Write a SQL statement to create a table Employee with fields
Emp_Id, Ename, Deptname and Salary. Insert two records in a table.
Write an SQL query to fetch Employee names with salaries >= 50000 and
<= 100000.
ANS.
mysql> select * from employee;
+--------+-----------------+-----------+--------+
| Emp_id | Ename | Dept_name | Salary |
+--------+-----------------+-----------+--------+
| 101 | M.S Dhoni | Software | 50000 |
| 102 | Yuvraj Singh | Accounts | 60000 |
| 103 | Virendra Sehwag | Software | 70000 |
| 108 | Rohit Sharma | Admin | 75000 |
+--------+-----------------+-----------+--------+
4 rows in set (0.00 sec)
mysql> select Ename from employee where Salary between 50000 and
100000;
+-----------------+
| Ename |
+-----------------+
| M.S Dhoni |
| Yuvraj Singh |
| Virendra Sehwag |
| Rohit Sharma |
+-----------------+
4 rows in set (0.00 sec)
Q15. Write a SQL statement to create a table Employee with fields
Emp_Id, Ename, Deptname and Salary. Insert two records in a table.
Write an SQL query to fetch Employee names having highest salary in
department.
ANS.
mysql> select * from employee;
+--------+-----------------+-----------+--------+
| Emp_id | Ename | Dept_name | Salary |
+--------+-----------------+-----------+--------+
| 101 | M.S Dhoni | Software | 50000 |
| 102 | Yuvraj Singh | Accounts | 60000 |
| 103 | Virendra Sehwag | Software | 70000 |
| 108 | Rohit Sharma | Admin | 75000 |
+--------+-----------------+-----------+--------+
4 rows in set (0.00 sec)
mysql> SELECT Ename, Dept_name, Salary
 -> FROM Employee e1
 -> WHERE Salary = (
 -> SELECT MAX(Salary)
 -> FROM Employee e2
 -> WHERE e1.Dept_name = e2.Dept_name);
+-----------------+-----------+--------+
| Ename | Dept_name | Salary |
+-----------------+-----------+--------+
| Yuvraj Singh | Accounts | 60000 |
| Virendra Sehwag | Software | 70000 |
| Rohit Sharma | Admin | 75000 |
+-----------------+-----------+--------+
3 rows in set (0.00 sec)
Q16. Write a SQL statement to create a table Book with fields
Book (Book_Id, Title, Author, Cost) Insert two records in a table.
Write an SQL queries to modify the cost of DBMS books by 12%.
ANS.
mysql> select * from book;
+---------+-----------+--------+------------------+------+
| Book_id | Book_Name | Author | Publisher | cost |
+---------+-----------+--------+------------------+------+
| 101 | DBMS | RG | Basic of DBMS | 100 |
| 102 | OS | SD | Operating System | 800 |
+---------+-----------+--------+------------------+------+
2 rows in set (0.00 sec)
mysql> update book set cost=cost*1.12 where Book_id=101;
Query OK, 1 row affected (0.01 sec)
Rows matched: 1 Changed: 1 Warnings: 0
mysql> select * from book;
+---------+-----------+--------+------------------+------+
| Book_id | Book_Name | Author | Publisher | cost |
+---------+-----------+--------+------------------+------+
| 101 | DBMS | RG | Basic of DBMS | 112 |
| 102 | OS | SD | Operating System | 800 |
+---------+-----------+--------+------------------+------+
2 rows in set (0.00 sec)
Q17. Write a SQL statement to create a table Employee with fields
Emp_Id, Ename, Deptname and Salary. Insert two records in a table.
Write an SQL queries to modify the salary of all employees with 15%
rise in salary.
ANS.
mysql> select * from employee;
+--------+-----------------+-----------+--------+
| Emp_id | Ename | Dept_name | Salary |
+--------+-----------------+-----------+--------+
| 101 | M.S Dhoni | Software | 50000 |
| 102 | Yuvraj Singh | Accounts | 60000 |
| 103 | Virendra Sehwag | Software | 70000 |
| 108 | Rohit Sharma | Admin | 75000 |
+--------+-----------------+-----------+--------+
4 rows in set (0.00 sec)
mysql> update employee set salary = salary*1.15;
Query OK, 4 rows affected (0.01 sec)
Rows matched: 4 Changed: 4 Warnings: 0
mysql> select * from employee;
+--------+-----------------+-----------+--------+
| Emp_id | Ename | Dept_name | Salary |
+--------+-----------------+-----------+--------+
| 101 | M.S Dhoni | Software | 57500 |
| 102 | Yuvraj Singh | Accounts | 69000 |
| 103 | Virendra Sehwag | Software | 80500 |
| 108 | Rohit Sharma | Admin | 86250 |
+--------+-----------------+-----------+--------+
4 rows in set (0.00 sec)
Q18. Write a SQL statement to create a table Employee with fields
EmpId, EName, Address, City Insert two records in a table. Write an
SQL queries to modify database so that Rohit now lives in Mumbai,
assuming the database entry was Rohit staying in Delhi.
ANS.
mysql> create table Emp_Deatils(Emp_Id int primary key,Ename
varchar(50),Address varchar(50),City varchar(50));
Query OK, 0 rows affected (0.03 sec)
mysql> insert into Emp_Deatils
values(101,"Rohit","Agra","Delhi"),(102,"Sach
in","Ghansoli","Navi Mumbai");
Query OK, 2 rows affected (0.01 sec)
Records: 2 Duplicates: 0 Warnings: 0
mysql> select * from Emp_Deatils;
+--------+--------+----------+-------------+
| Emp_Id | Ename | Address | City |
+--------+--------+----------+-------------+
| 101 | Rohit | Agra | Delhi |
| 102 | Sachin | Ghansoli | Navi Mumbai |
+--------+--------+----------+-------------+
2 rows in set (0.00 sec)
mysql> update Emp_Deatils set City ="Mumbai" ,Address="Bhandup" where
Emp_Id
=101;
Query OK, 1 row affected (0.01 sec)
Rows matched: 1 Changed: 1 Warnings: 0
mysql> select * from Emp_Deatils;
+--------+--------+----------+-------------+
| Emp_Id | Ename | Address | City |
+--------+--------+----------+-------------+
| 101 | Rohit | Bhandup | Mumbai |
| 102 | Sachin | Ghansoli | Navi Mumbai |
+--------+--------+----------+-------------+
2 rows in set (0.00 sec) 
