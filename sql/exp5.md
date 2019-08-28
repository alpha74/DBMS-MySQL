# Solution : Experiment-5


**AIM**: Implementation of the advanced ad-hoc query applications in a relational database is using SQL.

---

1.  ```
	SELECT enum, name, dnum, sal FROM emp GROUP BY dnum ASC, sal DESC ;
    ```
	
2.  ```
	SELECT emp.name AS name, dept.name AS department
    -> FROM emp, dept
    -> WHERE emp.dnum = dept.dnum
    -> AND emp.tax = 0 ;
    ```
	
3.  ```
	SELECT supplier.snum AS snum, supplier.name AS name, SUM( supply.qty ) AS tot_qty
    -> FROM supplier, supply
    -> WHERE supplier.snum = supply.snum
    -> GROUP BY snum ;
    ```
	
4.  ```
	SELECT * FROM emp WHERE name LIKE '%Jyoti%' AND sal > 900000.00 ;
    ```
	
5.  ```
	CREATE VIEW emp_dept AS ( SELECT emp.enum AS enum, emp.name AS name, dept.name AS dept_name, dept.area AS area
    -> FROM emp, dept WHERE emp.dnum = dept.dnum ) ;
    ```
	
6.  ```
	SELECT * FROM emp_Dept GROUP BY dnum ASC ;
    ```
	
7.  ```
	SELECT enum, name FROM emp
    -> WHERE sal BETWEEN  140000.00 AND 500000.00
    -> AND tax = 0 ;
    ```
	
8.  ```
	SELECT AVG( tax ) AS avg_tax FROM emp GROUP BY dnum ;
    ```
	
9.  ```
	INSERT INTO dept VALUES
    -> ( 25, 'Administration', 'S', 25 ) ;
	
	 INSERT INTO supplier VALUES
    -> ( 125, 'Eureka Solutions', 'DLH' ) ;
	
	INSERT INTO supply VALUES
    -> ( 'ST99', 125, 25, 800 ) ;
    ```
	
10. ```
	 -> SELECT * FROM emp ;
	 -> SELECT * FROM dept ;
	 -> SELECT * FROM supply ;
	 -> SELECT * FROM supplier ;
     ```
	
  ---
