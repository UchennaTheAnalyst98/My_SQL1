# My_SQL1
My first project on MySQL



DROP DATABASE IF EXISTS `Jcendesk`;
CREATE DATABASE `Jcendesk`;
USE `jcendesk`;


CREATE TABLE employees (
  employee_id INT NOT NULL,
  first_name VARCHAR(50),
  last_name VARCHAR(50),
  age INT,
  gender VARCHAR(10),
  birth_date DATE,
  PRIMARY KEY (employee_id)
);

CREATE TABLE salary (
  employee_id INT NOT NULL,
  first_name VARCHAR(50) NOT NULL,
  last_name VARCHAR(50) NOT NULL,
  occupation VARCHAR(50),
  salary INT,
  dept_id INT
);


INSERT INTO employees (employee_id, first_name, last_name, age, gender, birth_date)
VALUES
(1,'David', 'Sandra', 44, 'Female','1979-09-25'),
(3,'Akpan', 'John', 36, 'Male', '1987-03-04'),
(4, 'Favour', 'Samuel', 29, 'Female', '1994-03-27'),
(5, 'Anthony', 'Kelechi', 61, 'Male', '1962-08-28'),
(6, 'Vivian', 'Victor', 46, 'Female', '1977-07-30'),
(7, 'Glory', 'Egwu', 35, 'Female', '1988-12-01'),
(8, 'Hassan', 'Ahmed', 43, 'Male', '1980-11-11'),
(9, 'Olabanji', 'Olumide', 38, 'Male', '1985-07-26'),
(10, 'Christopher', 'Onyekachi', 34, 'Male', '1989-03-25'),
(11, 'Mark', 'Esom', 40, 'Male', '1983-06-14'),
(12, 'Paul', 'Sunday', 37, 'Male', '1986-07-27');


INSERT INTO salary (employee_id, first_name, last_name, occupation, salary, dept_id)
VALUES
(1, 'David', 'Sandra', 'Deputy Director of Parks and Recreation', 75000,1),
(2, 'Ronald', 'Simeon', 'Director of Parks and Recreation', 70000,1),
(3, 'Akpan', 'John', 'Entrepreneur', 50000,1),
(4, 'Favour', 'Samuel', 'Assistant to the Director of Parks and Recreation', 25000,1),
(5, 'Anthony', 'Kelechi', 'Office Manager', 50000,1),
(6, 'Vivian', 'Victor', 'Office Manager', 60000,1),
(7, 'Glory', 'Egwu', 'Nurse', 55000,4),
(8, 'Hassan', 'Ahmed', 'City Manager', 90000,3),
(9, 'Olabanji', 'Olumide', 'State Auditor', 70000,6),
(10,'Christopher', 'Onyekachi', 'Shoe Shiner and Musician', 20000, NULL),
(11, 'Mark', 'Esom', 'City Planner', 57000, 3),
(12, 'Paul', 'Sunday', 'Parks Director', 65000,1);



CREATE TABLE jcen_departments (
  department_id INT NOT NULL AUTO_INCREMENT,
  department_name varchar(50) NOT NULL,
  PRIMARY KEY (department_id)
);

INSERT INTO jcen_departments (department_name)
VALUES
('Information and technology'),
('Sales analyst'),
('Human resource'),
('Healthcare'),
('Library'),
('Finance');


#----------------------------TASK-------------------------


# 1. Retrieve all employee details from the employees table.

SELECT *
FROM employees;


# 2. Get only the first names and last names of all employees.

SELECT first_name, last_name
FROM employees;

SELECT first_name, last_name, CONCAT(first_name, " ", last_name) full_name 
FROM employees;


# 3. Find all female employees.

SELECT * 
FROM employees
WHERE gender = "Female";


# 4. Retrieve employees who are older than 40.

SELECT *
FROM employees
WHERE age > 40;


# 5. Get employees sorted by age in ascending order.

SELECT *
FROM employees
ORDER BY age ASC;


# 6. Find employees born before the year 1985.

SELECT *
FROM employees
WHERE birth_date < "1985-01-01";


# 7. Show employees whose first names start with 'A'.

SELECT *
FROM employees
WHERE first_name LIKE "A%";


# 8. Retrieve employees with the last name containing 'o'.

SELECT *
FROM employees
WHERE last_name LIKE "%o%";


# 9. Get the full names and salaries of employees earning more than $50,000.

SELECT CONCAT(first_name, " " ,last_name) Full_name, salary
FROM salary
WHERE salary > 50000;


# 10. List employees who earn between $40,000 and $70,000.

SELECT *
FROM salary
WHERE salary BETWEEN 40000 AND 70000;


# 11. Retrieve employees with the occupation 'Office Manager'.

SELECT *
FROM salary
WHERE occupation = "Office Manager";


# 12. Find the highest salary in the company.

SELECT MAX(salary)
FROM salary;


# 13. Get the average salary of all employees.

SELECT AVG(salary)  Avg_salary
FROM salary;


# 14. Count how many employees earn more than $60,000.

SELECT COUNT(salary) number_of_salary_earners_above_50k
FROM salary
WHERE salary > 50000;


# 15. Display all unique occupations in the salary table.

SELECT DISTINCT (occupation)
FROM salary;
