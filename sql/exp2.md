# Solution : Experiment-2

**AIM**: Perform queries on given relations/tables.

---

1. 
	<TABLE: CLIENT_MASTER>
	
		CREATE TABLE client_master
		-> (
		-> client_no varchar(6) not null unique primary key,
		-> name varchar(20) not null,
		-> city varchar(15),
		-> pincode numeric(6),
		-> state varchar(10),
		-> bal_due numeric(10,2)
		-> ) ;
		
		<desc client_master>
		+-----------+---------------+------+-----+---------+-------+
		| Field     | Type          | Null | Key | Default | Extra |
		+-----------+---------------+------+-----+---------+-------+
		| client_no | varchar(6)    | NO   | PRI | NULL    |       |
		| name      | varchar(20)   | NO   |     | NULL    |       |
		| city      | varchar(15)   | YES  |     | NULL    |       |
		| pincode   | decimal(6,0)  | YES  |     | NULL    |       |
		| state     | varchar(10)   | YES  |     | NULL    |       |
		| bal_due   | decimal(10,2) | YES  |     | NULL    |       |
		+-----------+---------------+------+-----+---------+-------+
		
	
	<TABLE: PRODUCT_MASTER>
	
		CREATE TABLE product_master
		-> (
		-> product_no varchar(6) not null unique primary key,
		-> description varchar(20) not null,
		-> profit_percentage numeric(4,2),
		-> unit_measure varchar(10),
		-> qty_on_hand numeric(8),
		-> reorder_level numeric(8),
		-> sell_price numeric(8,2),
		-> cost_price numeric(8,2)
		-> ) ;
		
		<desc  product_master>
		+-------------------+--------------+------+-----+---------+-------+
		| Field             | Type         | Null | Key | Default | Extra |
		+-------------------+--------------+------+-----+---------+-------+
		| product_no        | varchar(6)   | NO   | PRI | NULL    |       |
		| description       | varchar(20)  | NO   |     | NULL    |       |
		| profit_percentage | decimal(4,2) | YES  |     | NULL    |       |
		| unit_measure      | varchar(10)  | YES  |     | NULL    |       |
		| qty_on_hand       | decimal(8,0) | YES  |     | NULL    |       |
		| reorder_level     | decimal(8,0) | YES  |     | NULL    |       |
		| sell_price        | decimal(8,2) | YES  |     | NULL    |       |
		| cost_price        | decimal(8,2) | YES  |     | NULL    |       |
		+-------------------+--------------+------+-----+---------+-------+
	
	<TABLE: SALESMAN_MASTER>
	
		CREATE TABLE salesman_master
		-> (
		-> salesman_no varchar(6) not null unique primary key,
		-> salesman_name varchar(35) not null,
		-> address1 varchar(15),
		-> address2 varchar(15),
		-> s_city varchar(15),
		-> pincode numeric(6),
		-> state varchar(15),
		-> sal_amt numeric(8,2),
		-> tgt_to_get numeric(6,2),
		-> ytd_sales numeric(8,2),
		-> remarks varchar(15)
		-> ) ;
	
		<desc salesman_master>
		+---------------+--------------+------+-----+---------+-------+
		| Field         | Type         | Null | Key | Default | Extra |
		+---------------+--------------+------+-----+---------+-------+
		| salesman_no   | varchar(6)   | NO   | PRI | NULL    |       |
		| salesman_name | varchar(35)  | NO   |     | NULL    |       |
		| address1      | varchar(15)  | YES  |     | NULL    |       |
		| address2      | varchar(15)  | YES  |     | NULL    |       |
		| s_city        | varchar(15)  | YES  |     | NULL    |       |
		| pincode       | decimal(6,0) | YES  |     | NULL    |       |
		| state         | varchar(15)  | YES  |     | NULL    |       |
		| sal_amt       | decimal(8,2) | YES  |     | NULL    |       |
		| tgt_to_get    | decimal(6,2) | YES  |     | NULL    |       |
		| ytd_sales     | decimal(8,2) | YES  |     | NULL    |       |
		| remarks       | varchar(15)  | YES  |     | NULL    |       |
		+---------------+--------------+------+-----+---------+-------+
	
	
2. 

<INSERT: CLIENT_MASTER> 
```	
INSERT INTO client_master VALUES ( 'C00001', 'Ivan Bayross', 'Bombay', 400054, 'Maharashtra', 15000 ) ;
```
<INSERT: PRODUCT_MASTER> 
```
INSERT INTO product_master VALUES ( 'P00001', '1.44 Floppies', 5, 'Piece', 100, 20, 525, 500 ) ;
```
<INSERT: SALESMAN_MASTER> 
```		
INSERT INTO salesman_master VALUES ( 'S00001', 'Kiran', 'A/14', 'Worli', 'Bombay', 400002, 'Maharashtra', 3000, 100, 50, 'Good' ) ;
```  

		
		
3. 	```
	a) SELECT name FROM client_master ;
	b) SELECT * FROM client_master ;
	c) SELECT name, city FROM client_master ;
	d) SELECT description FROM product_master ;
	e) SELECT name FROM client_master WHERE city = 'Bombay' ;
	f) SELECT salesman_name FROM salesman_master WHERE sal_amt = 3000.00 ;
    ```


4.  ```
	a) UPDATE client_master SET city = 'Bombay' WHERE client_no = 'C00005' ;
	b) UPDATE client_master SET bal_due = 1000.00 WHERE client_no = 'C00001' ;
	c) UPDATE product_master SET cost_price = 950.00 WHERE product_no = 'P07865' ;
	d) UPDATE salesman_master SET s_city = 'Bombay' ;
    ```
	
5.  ```
	a) DELETE FROM salesman_master WHERE sal_amt = '3500' ;
	b) DELETE FROM product_master WHERE qty_on_hand = 100 ;
	c) DELETE FROM client_master WHERE state = 'Tamil Nadu' ;
	```
    
6.  ```
	a) ALTER TABLE client_master ADD telephone numeric(10) ;
		<desc client_master>
		+-----------+---------------+------+-----+---------+-------+
		| Field     | Type          | Null | Key | Default | Extra |
		+-----------+---------------+------+-----+---------+-------+
		| client_no | varchar(6)    | NO   | PRI | NULL    |       |
		| name      | varchar(20)   | NO   |     | NULL    |       |
		| city      | varchar(15)   | YES  |     | NULL    |       |
		| pincode   | decimal(6,0)  | YES  |     | NULL    |       |
		| state     | varchar(15)   | YES  |     | NULL    |       |
		| bal_due   | decimal(10,2) | YES  |     | NULL    |       |
		| telephone | decimal(10,0) | YES  |     | NULL    |       |
		+-----------+---------------+------+-----+---------+-------+

	b) ALTER TABLE product_master MODIFY sell_price numeric(10,2) ;
		<desc product_master>
		+-------------------+---------------+------+-----+---------+-------+
		| Field             | Type          | Null | Key | Default | Extra |
		+-------------------+---------------+------+-----+---------+-------+
		| product_no        | varchar(6)    | NO   | PRI | NULL    |       |
		| description       | varchar(25)   | NO   |     | NULL    |       |
		| profit_percentage | decimal(4,2)  | YES  |     | NULL    |       |
		| unit_measure      | varchar(10)   | YES  |     | NULL    |       |
		| qty_on_hand       | decimal(8,0)  | YES  |     | NULL    |       |
		| reorder_level     | decimal(8,0)  | YES  |     | NULL    |       |
		| sell_price        | decimal(10,2) | YES  |     | NULL    |       |
		| cost_price        | decimal(8,2)  | YES  |     | NULL    |       |
		+-------------------+---------------+------+-----+---------+-------+
     ```
	
7. ```
	a) DROP TABLE client_master ;
   ```

8. ```
	a)  ALTER TABLE salesman_master RENAME TO sman_master ;
   ``` 	
	
	
---
