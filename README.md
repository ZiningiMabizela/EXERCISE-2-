# EXERCISE-2-
--Create database / catalog 
CREATE CATALOG IF NOT EXISTS brightlearn_exc2;

--Create schema 
Create schema if not exists brightlearn_exc2.academy;

--Create a table 
CREATE TABLE IF NOT EXISTS brightlearn_exc2.academy.courses (
  student_id INT,
  name STRING,
  age INT,
  department STRING);

  --Insert the information into the table
  INSERT INTO brightlearn_exc2.academy.courses VALUES 
  (1, 'Alice', 20, 'IT'), 
  (2, 'Bob', 22, 'HR'), 
  (3, 'Charlie', 21, 'IT'), 
  (4, 'Diana', 23, 'Finance'), 
  (5, 'Eve', 22, 'HR');

  -- Display Informationa from the table
  SELECT * 
  FROM brightlearn_exc2.academy.courses;

  --01 List all distinct departments in the students table.
SELECT DISTINCT department
From brightlearn_exc2.academy.courses;

--02 Get the average age of students per department.
SELECT department, AVG(age) as avg_age
FROM brightlearn_exc2.academy.courses
GROUP BY department;

--03 Show departments with more than 1 student
SELECT department, COUNT(*) as num_students
FROM brightlearn_exc2.academy.courses
GROUP BY department
HAVING num_students > 1;

--04 Get all students whose age is between 21 and 23.
SELECT *
FROM brightlearn_exc2.academy.courses
WHERE age BETWEEN 21 AND 23;

-- 05 List all students in the IT or HR department who are older than 21.
SELECT *
FROM brightlearn_exc2.academy.courses
WHERE (department = 'IT' OR department = 'HR') AND age > 21;



-- Create a database / catalog
Create catalog if not exists brightlearn;

--Create schema 
Create schema if not exists brightlearn.default;

--Create a table 
CREATE TABLE IF NOT EXISTS brightlearn.default.courses (
  course_id INT,
  course_name STRING,
  department STRING,
  credits INT);

-- Insert the information into the table
INSERT INTO brightlearn.default.courses VALUES 
(101, 'SQL Basics ', 'IT', 3), 
(102, 'Python', 'IT', 4), 
(103, 'Data Science ', 'IT', 4), 
(104, 'Excel', 'Finance', 2), 
(105, 'Statistics ', 'HR', 3);

-- Create a table
CREATE TABLE IF NOT EXISTS brightlearn.default.courses(
  course_id INT,
  course_name STRING,
  department STRING,
  credits INT);

-- Display Informationa from the table
SELECT * 
FROM brightlearn.default.courses;


--06 Show total credits per department, only for departments with more than 5 total credits.
SELECT department AS department, SUM(credits) AS total_credits
FROM brightlearn.default.courses
GROUP BY department
HAVING total_credits > 5;

--07 List all courses that do not have 4 credits.
SELECT* 
FROM brightlearn.default.courses
WHERE credits != 4;

--08 Show the top 3 courses by credits in descending order.
SELECT course_id, course_name, credits 
FROM brightlearn.default.courses
ORDER BY credits DESC
LIMIT 3;



--Create database / catalog 
CREATE CATALOG IF NOT EXISTS UJ;

--Create schema
Create schema if not exists UJ.student;

--Create a table 
CREATE TABLE IF NOT EXISTS UJ.student.enrollments (
  enrollment_id INT,
  student_id INT,
  course_id INT,
  grade INT);


--Insert the information into the table
INSERT INTO UJ.student.enrollments VALUES 
(1, 1, 101, 85), 
(2, 2, 102, 78), 
(3, 3, 103, 90),
(4, 4, 104, 88),
(5, 5, 105, 82);

-- Display Informationa from the table
SELECT * 
FROM UJ.student.enrollments;

--09 Get the maximum, minimum, and average grade across all enrollments.
SELECT MAX(grade) AS max_grade, 
MIN(grade) AS min_grade, 
AVG(grade) AS avg_grade
FROM UJ.student.enrollments;

--10 Count how many enrollments exist per course.
SELECT course_id, COUNT(*) AS num_enrollments
FROM UJ.student.enrollments
GROUP BY course_id;

--Create database / catalog
Create catalog if not exists FNB;

--Create schema 
CREATE SCHEMA IF NOT EXISTS FNB.EMPLOYEES;

--Create a table 
CREATE TABLE IF NOT EXISTS FNB.EMPLOYEES.SALARIES (
  employee_id INT,
  name STRING,
  department STRING,
  salary INT,
  bonus INT);

-- Insert information into the table
Insert into FNB.EMPLOYEES.SALARIES values (
  1, 'Tom', 'IT', 60000, 5000), 
  (2, 'Jerry', 'HR', 55000, 4000), 
  (3, 'Spike', 'Finance', 70000, 6000), 
  (4, 'Tyke', 'IT', 62000, 5500), 
  (5, 'Butch', 'HR', 54000, 3500);

-- Display Informationa from the table
SELECT * 
FROM FNB.EMPLOYEES.SALARIES;

--11 Find total salary and total bonus per department.
SELECT department, 
SUM(salary) AS total_salary, 
SUM(bonus) AS total_bonus
FROM FNB.EMPLOYEES.SALARIES
GROUP BY department;

-- 12 Show departments where average salary is above 55,000.
SELECT department, AVG(salary) AS avg_salary
FROM FNB.EMPLOYEES.SALARIES
GROUP BY department
HAVING AVG(salary) > 55000;

--Q13 List employees whose salary plus bonus is greater than 60,000.
Select employee_id,
name,
salary,
bonus,
salary + bonus AS total_compensation
FROM FNB.EMPLOYEES.SALARIES
WHERE salary + bonus > 60000;


--Create database / catalog
Create catalog if not exists african;

-- Create schema
Create schema if not exists african.bank;

-- Create table
CREATE TABLE IF NOT EXISTS african.bank.projects (
  project_id INT,
  project_name STRING,
  department STRING,
  budget INT);

-- Insert information into the table
INSERT INTO african.bank.projects VALUES 
(1, 'AI App', 'IT', 120000), 
(2, 'Payroll System', 'Finance', 80000), 
(3, 'Dashboard', 'IT', 150000), 
(4, 'Website', 'Marketing ', 60000), 
(5, 'HR Portal', 'HR', 50000);

-- Display Informationa from the table
SELECT * 
FROM african.bank.projects;

Q14 Show total and average budget per department. Only include departments with average budget
above 70,000.
SELECT department, 
SUM(budget) AS total_budget, 
AVG(budget) AS avg_budget
FROM african.bank.projects
GROUP BY department
HAVING avg_budget > 70000;

--Q15 List all projects with budgets between 50,000 and 120,000, excluding the Marketing department.
SELECT *
FROM african.bank.projects
WHERE budget BETWEEN 50000 AND 120000 AND TRIM(department) != 'Marketing';
