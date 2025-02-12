CREATE DATABASE ORG123;
SHOW DATABASES;
USE ORG123;

CREATE TABLE Worker (
	WORKER_ID INT NOT NULL PRIMARY KEY AUTO_INCREMENT,
	FIRST_NAME CHAR(25),
	LAST_NAME CHAR(25),
	SALARY INT(15),
	JOINING_DATE DATETIME,
	DEPARTMENT CHAR(25)
);

INSERT INTO Worker 
	(WORKER_ID, FIRST_NAME, LAST_NAME, SALARY, JOINING_DATE, DEPARTMENT) VALUES
		(001, 'Monika', 'Arora', 100000, '14-02-20 09.00.00', 'HR'),
		(002, 'Niharika', 'Verma', 80000, '14-06-11 09.00.00', 'Admin'),
		(003, 'Vishal', 'Singhal', 300000, '14-02-20 09.00.00', 'HR'),
		(004, 'Amitabh', 'Singh', 500000, '14-02-20 09.00.00', 'Admin'),
		(005, 'Vivek', 'Bhati', 500000, '14-06-11 09.00.00', 'Admin'),
		(006, 'Vipul', 'Diwan', 200000, '14-06-11 09.00.00', 'Account'),
		(007, 'Satish', 'Kumar', 75000, '14-01-20 09.00.00', 'Account'),
		(008, 'Geetika', 'Chauhan', 90000, '14-04-11 09.00.00', 'Admin');
        
SELECT * FROM worker
WHERE salary not BETWEEN 100000 AND 200000;


SELECT * FROM worker
WHERE salary BETWEEN 200000 AND 400000
AND worker_id IN (1,2,3,4,5);

SELECT MIN(salary)
FROM worker;


use org123;

select * from worker;

select distinct (department) from worker;

#alias - help u to give some temp name for a coloumn

select worker_id as emp_code from worker;

SELECT worker_id FROM worker
UNION all
SELECT first_name FROM worker;

SELECT department, worker_id FROM worker
WHERE department='HR'
UNION ALL
SELECT department, worker_id FROM worker
WHERE department='account'
ORDER BY worker_id;

SELECT worker_id, first_name,department,
CASE
    WHEN salary > 300000 THEN 'Rich people'
    WHEN salary <=300000 && salary >=100000 THEN 'Middle stage'
    ELSE 'Poor people'
END 
AS People_stage_wise
FROM worker;

select * from worker where department='Admin' order by salary desc limit 3;

select department, count(department) as total_employees from worker
where department = 'HR' or department='account' group by department;


#
