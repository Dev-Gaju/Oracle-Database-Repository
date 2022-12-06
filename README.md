## All about Oracle Database
- **Download Oracle Software :** <a href="https://www.oracle.com/database/technologies/oracle-database-software-downloads.html">Oracle Database Software</a> and <a href="https://www.oracle.com/database/sqldeveloper/technologies/download/">SQL Developer</a>
- **Online Compiler :** <a href="https://livesql.oracle.com/apex/f?p=590:1:10773625984900::NO:RP::">Official </a> or <a href="https://www.programiz.com/sql/online-compiler/">Other</a>

Oracle supplies the following built-in datatypes:
<table>
  <tr>
    <th>Data Types</th>
    <th>Sub Types & Defination </th>
  </tr>
  <tr>
    <td>CHARACTER</td>
    <td>(i) <b>CHAR :</b> Fixed-length character data and Not more than 2000 bytes.<br>  (ii) <b>VARCHAR2 and VARCHAR :</b> Variable-length character data but not more than 4000 bytes <br> (iii) <b>NCHAR :</b> Fixed length but depending on the national character set. <br> (iv) <b>NVARCHAR2 :</b> Variable-length but depending on the national character set. <br> (v) <b>CLOB :</b> Single-byte character data.<br> (vi) <b>NCLOB :</b> ingle-byte or fixed-length multibyte national character set <br> (vii) <b>LONG :</b> Variable-length character data.  </td>
  </tr>
  <tr>
    <td>LONG</td>
    <td>Mixed up Number and character and hold upto 2GB data</td>
  </tr>
  <tr>
    <td>DATE</td>
    <td>Fixed-length date and time data</td>
  </tr>
  <tr>
    <td>BINARY</td>
    <td>(i) <b>BLOB :</b> Unstructured binary data.  <br>  (ii) <b>BFILE :</b> 	
      Binary data stored in an external file(like picture). <br> (iii) <b>RAW :</b> Variable-length raw binary data.   <br> (iv) <b>LONG RAW :</b> 	
Variable-length raw binary data.  </td>
  </tr>
</table>

#### Oracle works into several steps:
- **DDL: Data Defination**
     (i) Create  (ii) Alter   (ii) Drop  (iv) Rename   (v) Truncate
- **DML : Data ManiPulation** (i) Insert  (ii) Update  (iii) Delete
- **DCL : Data Control** (i) Grant (ii) Revoke
- **TCL : Transaction Conrol** (i) Commit  (ii) RollBack  (iii) SavePoint
- **DRL/DQL: Data Query Language** Select Stament

#### Lets Have Some Basic Queries
  - Create Table :  `Create Table Employee ( Emp_name varchar2(10), gender char(10),Salary Number(10), DOB Date )`
  - View All From Table : `Select * from  Employee`
  - Modify dataType, (Adding, Rename, Remove) * (Column) used Alter : 
      - Add Column `Alter table Employee add emp_id number(10)`
      - Modify dataType `Alter table Employee modify emp_id varchar2(10)`
      - Rename Coulmn `Alter table Employee rename emp_id to emoployee_id` 
      - Drop Column `Alter table Employee drop column emoployee_id`
  - Rename : `ALTER TABLE Employee RENAME TO employeess`
  - Drop Table: `drop table employeess`
  - Truncate: `truncate table employeess`
  PS: Truncate delete data from one show and delete delete data in row_wise and also used where condition
  - Insert Data: `Insert into Employee(Emp_name,gender,Salary,DOB) values ( 'Abdullah', 'male', 10000, TO_DATE ('062619', 'MMDDYY')`
  - Update Data: `UPDATE Employee  SET Emp_name = 'Jacob', Salary = 15000  WHERE emp_id = 1`
  - Delete Data: `DELETE FROM Employee WHERE Emp_name = 'Jacob' AND emp_id = 1`

#### Agrregation/Condition Queries
 - Min Max Mode, SUM:
     - `SELECT MIN(Salary) FROM Employee WHERE employee_age > 20`
     - `SELECT MAX(Salary) FROM Employee WHERE employee_age < 20`
     - `Select MEDIAN(Salary) from Employee where section = 'Junior'`
     - `SELECT SUM(Salary) AS "SUM Salary" FROM Employee WHERE Salary > 10000`
 - Group, Order,Having, Like :
     - `SELECT age FROM Employee WHERE  Salary > 10000  GROUP BY Salary`
     - `SELECT Emp_name, Salary FROM Employee WHERE Salary > 10000  ORDER BY id ASC`
     - `SELECT Salary FROM Employee GROUP BY Salary HAVING Salary > 10000`
     - `Select * from Employee where Emp_name Like "%st%"`
     - `SELECT DISTINCT emp_name, Salary FROM Employee  WHERE student_id >= 2`
 - Trigger:Enable,Disable,After,Before : All code are same Just change the Syntax
      ```
        CREATE OR REPLACE TRIGGER  "Employee_T"   
        AFTER INSERT or UPDATE or DELETE    #change based on After or before 
        ON "Employee"   
        FOR EACH ROW
        BEGIN  
        WHEN the person performs insert/update/delete operations into the table.  
        END;  
        /  
        ALTER TRIGGER  "STUDENTS_T" ENABLE  ## change based on enable or disable 
        /
        ```
 - Join(Several Types):
     - Inner : `SELECT students.student_id, students.student_name,teachers.teacher_id FROM students INNER JOIN teachers ON students.student_name=teachers.teacher_name`
     - Outer :`SELECT students.student_id,students.student_name, teachers.teacher_id FROM students LEFT JOIN teachers ON students.student_name = teachers.teacher_name`
     - Equi : `SELECT students.student_id, students.student_name, teachers.teacher_id  FROM students, teachers  WHERE students.student_name = teachers.teacher_name`
     - Self : `SELECT A.student_id, A.student_name, B.student_age  FROM students A, students B WHERE A.student_age = B.student_age;`
     - Cross or Cartesian: `SELECT * FROM students CROSS JOIN teachers;`
     - Semi:`SELECT students.student_id, students.student_name FROM students WHERE EXISTS (SELECT 25 FROM teachers WHERE teachers.teacher_age = students.student_age);`
  

#### About Join
![image](https://user-images.githubusercontent.com/50872508/205989940-fa9b497c-a692-45e0-9b30-bcc81f930f53.png)
