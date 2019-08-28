# Solution : Experiment-6

**AIM**: Establishing an environment for relational database management and data retrieval for the given database. Also, implementation of the ad-hoc query applications in a relational database using SQL.

---
	
	<CREATING TABLE: pilot>
	
		 CREATE TABLE pilot
		-> (
		-> enum numeric(3) not null unique,
		-> license varchar(5),
		-> rating varchar(25),
		-> med_type char(1),
		-> med_date date,
		-> pt135_date date,
		-> constraint pk_id primary key( enum ),
		-> constraint enum_ck check( enum > 100 )
		-> ) ;

		
	<CREATING TABLE: employee>
		 CREATE TABLE employee
		-> (
		-> enum numeric(3) not null unique,
		-> title char(3),
		-> lname varchar(15),
		-> fname varchar(15),
		-> initial char(1),
		-> dob date,
		-> hire_date date,
		-> constraint pk_id primary key( enum ),
		-> constraint enum_ck check( enum > 100 )
		-> ) ;

	<CREATING TABLE: aircraft>
		CREATE TABLE aircraft
		-> (
		-> ac_number char(5) not null unique,
		-> mod_code varchar(10),
		-> ac_ttaf numeric(7,1),
		-> ac_ttel numeric(7,1),
		-> ac_tier numeric(7,1),
		-> constraint pk_id primary key( ac_number)
		-> ) ;
		
	<CREATING TABLE : charter>
	
		CREATE TABLE charter
		-> (
		-> ctr_trip numeric(5,0) not null unique,
		-> ctr_date date not null,
		-> ctr_pilot numeric(3,0),
		-> ctr_copilot numeric(3),
		-> ac_number char(5),
		-> ctr_destination char(5),
		-> ctr_distance numeric(4),
		-> hrs_flown numeric(4,1),
		-> hrs_wait numeric(4,1),
		-> fuel_gallons numeric(6,1),
		-> ctr_oil_qts numeric(1),
		-> code numeric(5),
		-> constraint pk_id primary key( ctr_trip ),
		-> constraint ctr_trip_ck check( ctr_trip > 10000 AND ctr_trip < 10100 )
		-> ) ;
		
		ALTER TABLE charter
		-> ADD constraint fk_id1 foreign key( ac_number ) references aircraft( ac_number ) ;
		
	<CREATING TABLE: customer>
		CREATE TABLE customer
		-> (
		-> code numeric(5) not null unique,
		-> clname varchar(15),
		-> cfname varchar(15),
		-> cinitial char(1),
		-> careacode numeric(3),
		-> cphone char(8),
		-> cbalance numeric(9,2),
		-> constraint pk_id primary key( code ),
		-> constraint code_ck check( code >= 10010 )
		-> ) ;
		
	<CREATING TABLE: model>
		CREATE TABLE model
		-> (
		-> mcode varchar(10) not null unique,
		-> m_mfgr varchar(15),
		-> m_name varchar(20),
		-> m_seats numeric(2),
		-> m_chg_mile numeric(6,2),
		-> constraint pk_id primary key( mcode )
		-> ) ;
		
-----------------

1.  ```
	SELECT ctr_date, ac_number, ctr_destination, ctr_distance, hrs_flown
    -> FROM charter
    -> WHERE ac_number = '2278V' ;
    ```
	
2.  ```
	CREATE VIEW AC778V
    -> AS
    -> SELECT ctr_date, ac_number, ctr_destination, ctr_distance, hrs_flown
    -> FROM charter
    -> WHERE ac_number = '2278V' ;
    ```
	
3.  ```
	SELECT charter.ctr_date, customer.cphone, charter.ac_number, customer.careacode, charter.ctr_destination, charter.code
    -> FROM charter, customer
    -> WHERE charter.code = customer.code ;
	```
    
4.  ```
	SELECT charter.ctr_Date, charter.ac_number, customer.cfname, customer.clname
    -> FROM charter, customer
    -> WHERE charter.code = customer.code AND charter.ac_number = '2278V';
    ```
	
5.  ```
	SELECT clname, cfname, cbalance
    -> FROM customer
    -> WHERE cbalance > 0 GROUP BY cbalance DESC ;
	```
    
6.  ```
	SELECT AVG(cbalance) as avg_bal, MIN(cbalance) as min_bal, MAX(cbalance) as max_bal, SUM(cbalance) as total_bal
    -> FROM customer ;
	```
    
7.  ```
	SELECT ac_number, COUNT(ac_number) as num_of_trips, SUM(ctr_distance) as total_distance, AVG(ctr_distance) as avg_distance,
    -> SUM(hrs_flown) as total_hrs, AVG(hrs_flown) as avg_hrs
    -> FROM charter
    -> GROUP BY ac_number ;
	```
    
8.  ```
	SELECT charter.ctr_Date, charter.ac_number, employee.initial as mname, charter.ctr_pilot, employee.lname, charter.hrs_flown
    -> FROM charter, employee
    -> WHERE charter.ctr_pilot = employee.enum
    -> AND charter.ctr_pilot = '' ;
	```
    
9.  ```
	UPDATE aircraft SET aircraft.ac_ttaf = sum_hrs.sum_flown
    -> AND aircraft.ac_ttel = sum_hrs.sum_total
    -> WHERE aircraft.ac_number = sum_hrs.ac_number ;
	```
    
10. ```
	CREATE TRIGGER trg_ctr_hrs
    -> AFTER INSERT ON aircraft
    -> REFERENCING NEW ROW AS nrow
    -> for each row
    -> begin
    -> UPDATE aircraft SET aircraft.ac_ttaf = sum_hrs.sum_flown
    -> AND aircraft.ac_ttel = sum_hrs.sum_total
    -> WHERE aircraft.ac_number = sum_hrs.ac_number ;
	-> end ;
	```
	
---
