## Question 1

```
SELECT Courses.CourseName, Courses.Credits FROM Courses;
```
![[Pasted image 20250912091950.png]]

## Question 2

```
SELECT Instructors.FirstName, Instructors.LastName FROM Instructors
WHERE Instructors.HireDate >= '2015-01-01';
```
![[Pasted image 20250912092027.png]]

## Question 3

```
SELECT Courses.CourseID FROM Courses
UNION 
SELECT Enrollments.CourseID FROM Enrollments;
```
![[Pasted image 20250912092121.png]]

## Question 4

```
SELECT Courses.CourseName
FROM Courses
WHERE NOT EXISTS (
    SELECT 1
    FROM Enrollments
    WHERE Enrollments.CourseID = Courses.CourseID
);
```
![[Pasted image 20250912093749.png]]

## Question 5

```
SELECT Instructors.FirstName,
       Instructors.LastName,
       Courses.CourseName
FROM Instructors
NATURAL JOIN Courses;
```
![[Pasted image 20250912093822.png]]

## Question 6
```
SELECT Courses.CourseName, Departments.DepartmentName
FROM Courses, Departments
WHERE Courses.Department = Departments.DepartmentName;
```
![[Pasted image 20250912093853.png]]

## Question 7

```
SELECT Departments.DepartmentID, Departments.DepartmentName, Courses.CourseID, Courses.CourseName
FROM Departments LEFT JOIN Courses
ON Courses.Department = Departments.DepartmentName;
```
![[Pasted image 20250912093938.png]]

## Question 8

```
SELECT Enrollments.CourseID AS 'enrollments course ID', Courses.CourseID, Courses.CourseName
FROM Enrollments RIGHT JOIN Courses
ON Courses.CourseID = Enrollments.CourseID;
```
![[Pasted image 20250912094109.png]]

## Question 9

```
SELECT Instructors.InstructorID, Instructors.FirstName, Instructors.LastName
FROM Instructors
WHERE Instructors.InstructorID IN (
	SELECT Courses.InstructorID FROM Courses
);
```
![[Pasted image 20250912094205.png]]

## Question 10

>Is this a trick question? I believe so...

```
SELECT Courses.CourseID, Courses.CourseName
FROM Courses
WHERE Courses.Department NOT IN (
    SELECT Departments.DepartmentName
    FROM Departments
    WHERE Departments.DepartmentName IS NOT NULL
);
```
![[Pasted image 20250912094400.png]]