# SQL-mini-projects
DROP TABLE IF EXISTS students;

CREATE TABLE students(
	roll_number INTEGER PRIMARY KEY,
    name TEXT,
    age INTEGER,
    gender CHAR(1),
    marks INTEGER
);

INSERT INTO students(roll_number, name, age, gender, marks) VALUES
(101, 'Amit', 18, 'M', 450),
(102, 'Sneha', 19, 'F', 480),
(103, 'Ravi', 20, 'M', 395),
(104, 'Priya', 18, 'F', 410),
(105, 'Vikram', 21, 'M', 350),
(106, 'Neha', 20, 'F', 465),
(107, 'Niran', 21, 'M', 442),
(108, 'Anika', 22, 'F', 330),
(109, 'Ekansh', 18, 'M', 410),
(110, 'Mishka', 19, 'F', 390);

--Select all records
SELECT * FROM students;

--Get the names of all students.
SELECT name FROM students;

--List all female students.
SELECT * FROM students
WHERE gender = 'F';

--Find students with marks greater than 400.
SELECT name, marks FROM students
WHERE marks > 400;

--Count total number of students.
SELECT COUNT (*) FROM students;

--Find the average marks of all students
SELECT AVG(marks) AS average_marks
FROM students;

--List students who are 20 years old.
SELECT * FROM students
WHERE age=20;

--Display students in order of highest marks.
SELECT name, marks FROM students
ORDER BY marks DESC;

--Get student names and their marks only.
SELECT name, marks
FROM students;

--Show distinct ages of students.
SELECT DISTINCT age FROM students;

--Find the top 3 students with the highest marks.
SELECT * FROM students
ORDER BY marks DESC
LIMIT 3;

--Retrieve the names of students whose marks are above the average marks.
SELECT name, marks FROM students
WHERE marks > (SELECT AVG(marks)FROM students);

--Show the student with the highest and lowest marks.(Using case function)
SELECT name, marks,
	CASE
		WHEN marks > 400 THEN 'Highest'
		ELSE 'Lowest'
	END AS student_marks_status
FROM students;

--Show the student with the highest and lowest marks.(Without Using case function)
-- Highest
SELECT * FROM students
WHERE marks = (SELECT MAX(marks) FROM students);

-- Lowest
SELECT * FROM students
WHERE marks = (SELECT MIN(marks) FROM students);
