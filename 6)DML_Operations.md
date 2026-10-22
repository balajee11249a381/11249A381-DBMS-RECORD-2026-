# Experiment 6 — INSERT, DELETE, ALTER, UPDATE and SELECT

## 1. AIM
To perform INSERT, UPDATE, DELETE, ALTER and SELECT operations on a table.

## 2. SOFTWARE REQUIRED
- Oracle Database or an Oracle-compatible SQL lab environment
- SQL*Plus or Oracle SQL Developer
- DBMS_OUTPUT enabled for PL/SQL exercises

## 3. ALGORITHM
1. Create a STUDENT table with ROLLNO, NAME and MARKS.
2. Insert three sample student records.
3. Display all records using SELECT.
4. Update a student mark and delete one student row.
5. Alter the table to add AGE, then display the remaining records.

## 4. PROGRAM / SQL COMMANDS
```sql
CREATE TABLE STUDENT (
  ROLLNO NUMBER(3),
  NAME VARCHAR2(20),
  MARKS NUMBER(3)
);

INSERT INTO STUDENT VALUES (101, 'RAVI', 85);
INSERT INTO STUDENT VALUES (102, 'RAJU', 75);
INSERT INTO STUDENT VALUES (103, 'SITA', 90);

SELECT * FROM STUDENT;

UPDATE STUDENT SET MARKS = 80 WHERE ROLLNO = 102;
DELETE FROM STUDENT WHERE ROLLNO = 103;
ALTER TABLE STUDENT ADD AGE NUMBER(2);

SELECT * FROM STUDENT;
```

## 5. OUTPUT
> The following is illustrative sample/expected output. It is not a screenshot or a claim that the SQL was executed in this repository. Run the program in your lab environment and capture your own result for submission.

```text
Expected initial rows:
ROLLNO  NAME  MARKS
101     RAVI  85
102     RAJU  75
103     SITA  90

Expected rows after UPDATE, DELETE and ALTER:
ROLLNO  NAME  MARKS  AGE
101     RAVI  85     (NULL)
102     RAJU  80     (NULL)
```

## 6. RESULT
Thus, INSERT, UPDATE, DELETE, ALTER and SELECT operations were performed successfully.

