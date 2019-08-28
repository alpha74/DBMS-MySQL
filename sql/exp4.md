# Solution : Experiment-4


**AIM**: Establishing an environment for relational database management and data retrieval from Oracle.

---

	<desc emp>
		+-------+--------------+------+-----+---------+-------+
		| Field | Type         | Null | Key | Default | Extra |
		+-------+--------------+------+-----+---------+-------+
		| enum  | decimal(4,0) | NO   | PRI | NULL    |       |
		| name  | varchar(15)  | NO   |     | NULL    |       |
		| sal   | decimal(9,2) | NO   |     | NULL    |       |
		| tax   | decimal(8,2) | YES  |     | NULL    |       |
		| dnum  | decimal(3,0) | NO   | MUL | NULL    |       |
		| mgr   | decimal(3,0) | NO   |     | NULL    |       |
		+-------+--------------+------+-----+---------+-------+		
        
	<desc dept>
		+-------+--------------+------+-----+---------+-------+
		| Field | Type         | Null | Key | Default | Extra |
		+-------+--------------+------+-----+---------+-------+
		| dnum  | decimal(3,0) | NO   | PRI | NULL    |       |
		| name  | varchar(20)  | NO   |     | NULL    |       |
		| area  | varchar(1)   | NO   |     | NULL    |       |
		| mgr   | decimal(3,0) | YES  | UNI | NULL    |       |
		+-------+--------------+------+-----+---------+-------+
		
	<desc supplier>
		+-------+--------------+------+-----+---------+-------+
		| Field | Type         | Null | Key | Default | Extra |
		+-------+--------------+------+-----+---------+-------+
		| snum  | decimal(3,0) | NO   | PRI | NULL    |       |
		| name  | varchar(25)  | NO   |     | NULL    |       |
		| city  | char(3)      | NO   |     | NULL    |       |
		+-------+--------------+------+-----+---------+-------+

	<desc supply>
		+-------+--------------+------+-----+---------+-------+
		| Field | Type         | Null | Key | Default | Extra |
		+-------+--------------+------+-----+---------+-------+
		| pnum  | char(4)      | NO   | PRI | NULL    |       |
		| snum  | decimal(3,0) | NO   | PRI | NULL    |       |
		| dnum  | decimal(3,0) | NO   | PRI | NULL    |       |
		| qty   | decimal(4,0) | YES  |     | NULL    |       |
		+-------+--------------+------+-----+---------+-------+
		
		
---

1.  ```
	SELECT name, sal FROM emp WHERE dnum = 26 ;
    ```
	
2.  ```
	 SELECT DISTINCT(supplier.name), dept.dnum, dept.name
    -> FROM supplier, dept, supply
    -> WHERE supplier.snum = supply.snum AND
    -> dept.dnum = supply.dnum
    -> AND dept.name = 'Personnel' ;
    ```
	
3.  ```
	 SELECT DISTINCT(supplier.name)
    -> FROM supplier, dept, supply
    -> WHERE supplier.snum = supply.snum AND
    -> dept.dnum = supply.dnum
    -> AND supplier.city = 'UMR'
    -> AND dept.area = 'N' ;
	```
   
4.  ```
	SELECT emp.name, dept.name
    -> FROM emp, dept
    -> WHERE emp.dnum = dept.dnum
    -> AND
    -> emp.name LIKE 'A%' ;
    ```
	
5.  ```
	SELECT supplier.name, supply.qty, dept.name
    -> FROM supplier, supply, dept
    -> WHERE supplier.snum = supply.snum
    -> AND supply.dnum = dept.dnum
    -> AND supply.pnum = 'KK78' ;
    ```
	
6.  ```
	CREATE TABLE emp_admn AS ( SELECT enum, name, dnum, mgr FROM emp ) ;

	<desc emp_admn>
		+-------+--------------+------+-----+---------+-------+
		| Field | Type         | Null | Key | Default | Extra |
		+-------+--------------+------+-----+---------+-------+
		| enum  | decimal(4,0) | NO   |     | NULL    |       |
		| name  | varchar(15)  | NO   |     | NULL    |       |
		| dnum  | decimal(3,0) | NO   |     | NULL    |       |
		| mgr   | decimal(3,0) | NO   |     | NULL    |       |
		+-------+--------------+------+-----+---------+-------+
	
	CREATE TABLE emp_pay AS ( SELECT enum, name, sal, tax FROM emp ) ;
	
	<desc emp_pay>
		+-------+--------------+------+-----+---------+-------+
		| Field | Type         | Null | Key | Default | Extra |
		+-------+--------------+------+-----+---------+-------+
		| enum  | decimal(4,0) | NO   |     | NULL    |       |
		| name  | varchar(15)  | NO   |     | NULL    |       |
		| sal   | decimal(9,2) | NO   |     | NULL    |       |
		| tax   | decimal(8,2) | YES  |     | NULL    |       |
		+-------+--------------+------+-----+---------+-------+
     ```
	
7.  ```
	SELECT enum, name, sal AS grs_pay, (sal-tax) AS net_pay FROM emp ;
    ```
	
8.  ```
	INSERT INTO dept VALUES
    -> ( 988, 'Inventory&Purchase', 'S', 23 ) ;
	
	INSERT INTO emp VALUES
    -> ( 9218, 'Jyotika', 890270.00, 89000.00, 988, 23 ) ;
    ```
	
9.  ```
	SELECT emp.enum, emp.name
    -> FROM emp, dept
    -> WHERE emp.dnum = dept.dnum
    -> AND dept.area = 'S'
    -> AND emp.sal > 800000 ;
    ```
	
10. ```
	SELECT dept.name AS dep_name, supplier.name AS supplier_name
    -> FROM dept, supply, supplier
    -> WHERE supplier.snum = supply.snum
    -> AND dept.dnum = supply.dnum
    -> AND supply.pnum = 'PD33' ;
    ```
	

---
