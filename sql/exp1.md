# Solution : Experiment-1


**AIM**: The study of Data Definition Language and Data Manipulation Language.



------
### Part-A
------

1. 	```
	> CREATE TABLE CUSTOMER 
	> (
	> first_name varchar(15) not null unique,
	> last_name varchar(15) not null, 
	> address varchar(35) default 'NULL',
	> city varchar(15) default 'NULL', 
	> country varchar(15) default 'NULL', 
	> birth_date date,
	> primary key( first_name, last_name )
	> ) ;
	```

2. 	```
	> INSERT INTO CUSTOMER  VALUES ( "John", "Smith", "Western Road", "New York", "USA", '1969-12-12'  );
	> INSERT INTO CUSTOMER  VALUES ( "David", "Stonewall", "Park Avenue", "San Francisco", "USA", '1954-01-03'  );
	> INSERT INTO CUSTOMER  VALUES ( "Susan", "Grant", "Lord Park", "Los Angeles", "USA", '1970-03-03'  );
	> INSERT INTO CUSTOMER  VALUES ( "Paul", "O'Neil", "Red Cross", "New York", "USA", '1982-09-17'  );
	> INSERT INTO CUSTOMER  VALUES ( "Stephen", "Grant", "Carpet Road", "Los Angeles", "USA", '1974-03-03'  ) ;
	```


3. 	```
	> ALTER TABLE CUSTOMER ADD ( gender varchar(1) ) ;
	```

4. 	```
	> ALTER TABLE CUSTOMER ADD ( telephone varchar(11) COMMENT 'Tel. phone numbers may contain special characters' ) ;
	```

5. 	```
	> ALTER TABLE CUSTOMER MODIFY address varchar(80)  ;

	<desc CUSTOMER>
	+------------+-------------+------+-----+---------+-------+
	| Field      | Type        | Null | Key | Default | Extra |
	+------------+-------------+------+-----+---------+-------+
	| first_name | varchar(15) | NO   | PRI | NULL    |       |
	| last_name  | varchar(15) | NO   | PRI | NULL    |       |
	| address    | varchar(80) | YES  |     | NULL    |       |
	| city       | varchar(15) | YES  |     | NULL    |       |
	| country    | varchar(15) | YES  |     | NULL    |       |
	| birth_date | date        | YES  |     | NULL    |       |
	| gender     | varchar(1)  | YES  |     | NULL    |       |
	| email      | varchar(35) | NO   |     | NULL    |       |
	| telephone  | varchar(11) | YES  |     | NULL    |       |
	+------------+-------------+------+-----+---------+-------+
   	```




----
Part-B
----

1. 	```
	> CREATE TABLE STUDENT ( roll_no varchar(10) not null unique primary key, sname varchar(30) not null, maths numeric(4) not null, chem numeric(4) not null, phy numeric(4) not null );
	```

2. 	```
	> INSERT INTO STUDENT VALUES ( 'CSE022', 'Raj Malhotra', 70, 80, 90 ) ;
	> INSERT INTO STUDENT VALUES ( 'CSE012', 'Gopal Tyagi', 97, 62, 82 ) ;
	> INSERT INTO STUDENT VALUES ( 'CSE015', 'Gopal Tyagi', 97, 62, 82 );
	> INSERT INTO STUDENT VALUES ( 'CSE018', 'Ganesh Trivedi', 86, 82, 72 );
	> INSERT INTO STUDENT VALUES ( 'CSE028', 'Shivraj Ojha', 76, 87, 91 );
	```

3.	```
	> ALTER TABLE STUDENT ADD ( total numeric(5) not null ) ;
	```

4. ```
	> UPDATE STUDENT SET total = maths + phy + chem ;

	<desc STUDENT>
	+---------+--------------+------+-----+---------+-------+
	| Field   | Type         | Null | Key | Default | Extra |
	+---------+--------------+------+-----+---------+-------+
	| roll_no | varchar(10)  | NO   | PRI | NULL    |       |
	| sname   | varchar(30)  | NO   |     | NULL    |       |
	| maths   | decimal(4,0) | NO   |     | NULL    |       |
	| chem    | decimal(4,0) | NO   |     | NULL    |       |
	| phy     | decimal(4,0) | NO   |     | NULL    |       |
	| total   | decimal(5,0) | NO   |     | NULL    |       |
	+---------+--------------+------+-----+---------+-------+
   ```


5. ```
	> ALTER TABLE STUDENT ADD ( average numeric(5,2) not null ) ;
	<desc STUDENT>
	+---------+--------------+------+-----+---------+-------+
	| Field   | Type         | Null | Key | Default | Extra |
	+---------+--------------+------+-----+---------+-------+
	| roll_no | varchar(10)  | NO   | PRI | NULL    |       |
	| sname   | varchar(30)  | NO   |     | NULL    |       |
	| maths   | decimal(4,0) | NO   |     | NULL    |       |
	| chem    | decimal(4,0) | NO   |     | NULL    |       |
	| phy     | decimal(4,0) | NO   |     | NULL    |       |
	| total   | decimal(5,0) | NO   |     | NULL    |       |
	| average | decimal(5,2) | NO   |     | NULL    |       |
	+---------+--------------+------+-----+---------+-------+
    ```

6. ```
	> UPDATE STUDENT SET average = total/3 ;
   ```



---
