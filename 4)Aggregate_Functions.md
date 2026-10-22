# Experiment 4 — Aggregate Functions, GROUP BY and HAVING

## 1. AIM
To execute aggregate functions and SQL queries using GROUP BY and HAVING.

## 2. SOFTWARE REQUIRED
- Oracle Database or an Oracle-compatible SQL lab environment
- SQL*Plus or Oracle SQL Developer
- DBMS_OUTPUT enabled for PL/SQL exercises

## 3. ALGORITHM
1. Start the SQL environment and create/populate a STUDENT table with ROLLNO and MARKS columns.
2. Execute COUNT, SUM, AVG, MAX and MIN aggregate functions.
3. Add a department column and populate it for each row.
4. Group the rows by department and count records in each group.
5. Use HAVING to filter groups and inspect the results.

## 4. PROGRAM / SQL COMMANDS
```sql
-- Example assumes STUDENT(ROLLNO, NAME, MARKS) has three sample rows:
-- (101, 'RAVI', 85), (102, 'RAJU', 75), (103, 'SITA', 90)
SELECT COUNT(*) AS TOTAL_STUDENTS FROM STUDENT;
SELECT SUM(MARKS) AS TOTAL_MARKS FROM STUDENT;
SELECT AVG(MARKS) AS AVERAGE_MARKS FROM STUDENT;
SELECT MAX(MARKS) AS HIGHEST_MARKS FROM STUDENT;
SELECT MIN(MARKS) AS LOWEST_MARKS FROM STUDENT;

ALTER TABLE STUDENT ADD DEPT VARCHAR2(10);
UPDATE STUDENT SET DEPT = 'CSE' WHERE ROLLNO = 101;
UPDATE STUDENT SET DEPT = 'CSE' WHERE ROLLNO = 102;
UPDATE STUDENT SET DEPT = 'ECE' WHERE ROLLNO = 103;

SELECT DEPT, COUNT(*) AS STUDENT_COUNT
FROM STUDENT
GROUP BY DEPT;

SELECT DEPT, COUNT(*) AS STUDENT_COUNT
FROM STUDENT
GROUP BY DEPT
HAVING COUNT(*) > 1;
```

## 5. OUTPUT
> The following is illustrative sample/expected output. It is not a screenshot or a claim that the SQL was executed in this repository. Run the program in your lab environment and capture your own result for submission.

```text
Expected aggregate values for the three sample marks 85, 75 and 90:
TOTAL_STUDENTS = 3
TOTAL_MARKS = 250
AVERAGE_MARKS = 83.333...
HIGHEST_MARKS = 90
LOWEST_MARKS = 75

Expected group counts:
DEPT  STUDENT_COUNT
CSE   2
ECE   1

Expected HAVING result (COUNT(*) > 1):
DEPT  STUDENT_COUNT
CSE   2
```

## 6. RESULT
Thus, aggregate functions, GROUP BY and HAVING were executed successfully.

