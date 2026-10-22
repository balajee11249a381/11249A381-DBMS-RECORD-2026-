# Experiment 5 — Relationships, Joins and Subqueries

## 1. AIM
To define a relationship between STUDENT and COURSE tables and execute JOIN and subquery operations.

## 2. SOFTWARE REQUIRED
- Oracle Database or an Oracle-compatible SQL lab environment
- SQL*Plus or Oracle SQL Developer
- DBMS_OUTPUT enabled for PL/SQL exercises

## 3. ALGORITHM
1. Create the COURSE table with CID as its primary key.
2. Create the STUDENT table and use CID to reference COURSE.
3. Insert sample course and student records.
4. Execute INNER JOIN and LEFT JOIN queries to combine related data.
5. Execute a subquery to retrieve students enrolled in the CSE course.

## 4. PROGRAM / SQL COMMANDS
```sql
CREATE TABLE COURSE (
  CID NUMBER(3) PRIMARY KEY,
  CNAME VARCHAR2(20)
);

CREATE TABLE STUDENT (
  SID NUMBER(3) PRIMARY KEY,
  NAME VARCHAR2(20),
  CID NUMBER(3),
  CONSTRAINT FK_STUDENT_COURSE FOREIGN KEY (CID) REFERENCES COURSE(CID)
);

INSERT INTO COURSE VALUES (1, 'CSE');
INSERT INTO COURSE VALUES (2, 'ECE');
INSERT INTO COURSE VALUES (3, 'AI');

INSERT INTO STUDENT VALUES (101, 'RAVI', 1);
INSERT INTO STUDENT VALUES (102, 'RAJU', 2);
INSERT INTO STUDENT VALUES (103, 'SITA', 1);

-- INNER JOIN
SELECT S.NAME, C.CNAME
FROM STUDENT S
INNER JOIN COURSE C ON S.CID = C.CID;

-- LEFT JOIN
SELECT S.NAME, C.CNAME
FROM STUDENT S
LEFT JOIN COURSE C ON S.CID = C.CID;

-- SUBQUERY: students in CSE
SELECT NAME
FROM STUDENT
WHERE CID = (SELECT CID FROM COURSE WHERE CNAME = 'CSE');
```

## 5. OUTPUT
> The following is illustrative sample/expected output. It is not a screenshot or a claim that the SQL was executed in this repository. Run the program in your lab environment and capture your own result for submission.

```text
Expected INNER JOIN / LEFT JOIN rows:
NAME  CNAME
RAVI  CSE
RAJU  ECE
SITA  CSE

Expected subquery output:
NAME
RAVI
SITA
```

## 6. RESULT
Thus, the relationship, JOIN operations and subquery were demonstrated successfully.

