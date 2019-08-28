# Solution : Experiment-3

**AIM**: Demonstration of relational database creation EMPLOYEE and execution of simple queries.

---

1.  
``` 
	CREATE TABLE employee
    -> (
    -> enum numeric(4,0) not null unique primary key,
    -> fname varchar(15) not null,
    -> mname varchar(1),
    -> lname varchar(15) not null,
    -> birthdate date not null,
    -> gender enum( 'M', 'F'),
    -> ssn varchar(10) not null unique,
    -> job_title enum( 'Lecturer', 'Professor', 'Asst. Professor', 'Sr. Lecturer' ) not null,
    -> salary numeric(7,2) not null,
    -> hiredate date not null,
    -> tax numeric(6,2) not null,
    -> department enum('Biotechnology', 'Computer Science', 'Nano Technology', 'Information Technology' ) not null
    -> );
	
	
	<desc employee>
	+------------+-------------------------------------------------------------------------------------+------+-----+---------+-------+
	| Field      | Type                                                                                | Null | Key | Default | Extra |
	+------------+-------------------------------------------------------------------------------------+------+-----+---------+-------+
	| enum       | decimal(4,0)                                                                        | NO   | PRI | NULL    |       |
	| fname      | varchar(15)                                                                         | NO   |     | NULL    |       |
	| mname      | varchar(1)                                                                          | YES  |     | NULL    |       |
	| lname      | varchar(15)                                                                         | NO   |     | NULL    |       |
	| birthdate  | date                                                                                | NO   |     | NULL    |       |
	| gender     | enum('M','F')                                                                       | YES  |     | NULL    |       |
	| ssn        | varchar(10)                                                                         | NO   | UNI | NULL    |       |
	| job_title  | enum('Lecturer','Professor','Asst. Professor','Sr. Lecturer')                       | NO   |     | NULL    |       |
	| salary     | decimal(7,2)                                                                        | NO   |     | NULL    |       |
	| hiredate   | date                                                                                | NO   |     | NULL    |       |
	| tax        | decimal(6,2)                                                                        | NO   |     | NULL    |       |
	| department | enum('Biotechnology','Computer Science','Nano Technology','Information Technology') | NO   |     | NULL    |       |
	+------------+-------------------------------------------------------------------------------------+------+-----+---------+-------+
```
	
2.
```
	INSERT INTO employee VALUES ( '9201', 'Sangeet', 'R', 'Shrama', '1965-11-08', 'M', '11MH456633', 'Professor', 1200900.00, '1990-12-16', 120090.00, 'Computer Science' ) ;
```
	 
3. 
```
	SELECT * FROM employee WHERE job_title = 'Professor' ;
```
	
4.
```
	-> SELECT enum, fname, mname, lname, birthdate, salary, gender FROM employee ;
	-> SELECT enum, ssn, job_title, department, hiredate, tax FROM employee ;
```
5. 
```	
    	UPDATE employee SET job_title = 'Asst. Professor' WHERE enum = '9204' ;
```

6. 
```	
    	DELETE FROM employee WHERE fname = 'Jyotirmay' AND hiredate = '1999-04-25' AND job_title = 'Sr. Lecturer' ;
```
	
7. 
```
	START TRANSACTION ;
	<insert/update/delete/alter/drop query>
	ROLLBACK ;
```

8. 
```
	SELECT fname, ssn, job_title as designation, department FROM employee ;
```

9.
```
	-> INSERT INTO employee VALUES
	-> ( '9211', 'Deepak', 'M', 'Lakhanpal', '1978-02-28', 'M', '14OR333567', 'Lecturer', 120000.00, '1999-04-22', 12000.00, 'Biotechnology' ) ;
```	
	
---

	
