# Experiment 8 — Views, Sequences, Indexes and Savepoints

## 1. AIM
To create and use a view, sequence and index, and demonstrate a transaction savepoint.

## 2. SOFTWARE REQUIRED
- Oracle Database or an Oracle-compatible SQL lab environment
- SQL*Plus or Oracle SQL Developer
- DBMS_OUTPUT enabled for PL/SQL exercises

## 3. ALGORITHM
1. Create a STUDENT table and insert sample rows.
2. Create a view and query the view.
3. Create a sequence and retrieve its next value.
4. Create an index on the NAME column.
5. Update records around a savepoint, roll back to the savepoint and display final data.

## 4. PROGRAM / SQL COMMANDS
```sql
CREATE TABLE STUDENT (
  ROLLNO NUMBER(3), NAME VARCHAR2(20), MARKS NUMBER(3)
);
INSERT INTO STUDENT VALUES (101, 'RAVI', 85);
INSERT INTO STUDENT VALUES (102, 'RAJU', 75);
INSERT INTO STUDENT VALUES (103, 'SITA', 90);

-- VIEW
CREATE VIEW STUDENT_VIEW AS
SELECT ROLLNO, NAME, MARKS FROM STUDENT;
SELECT * FROM STUDENT_VIEW;

-- SEQUENCE
CREATE SEQUENCE STUDENT_SEQ START WITH 104 INCREMENT BY 1;
SELECT STUDENT_SEQ.NEXTVAL FROM DUAL;

-- INDEX
CREATE INDEX STUDENT_INDEX ON STUDENT(NAME);

-- SAVEPOINT
UPDATE STUDENT SET MARKS = 95 WHERE ROLLNO = 101;
SAVEPOINT S1;
UPDATE STUDENT SET MARKS = 70 WHERE ROLLNO = 102;
ROLLBACK TO S1;
SELECT * FROM STUDENT;
COMMIT;
```

## 5. OUTPUT
> The following is illustrative sample/expected output. It is not a screenshot or a claim that the SQL was executed in this repository. Run the program in your lab environment and capture your own result for submission.

```text
Expected sequence query result on first use:
NEXTVAL
104

Expected final marks after ROLLBACK TO S1:
ROLLNO  NAME  MARKS
101     RAVI  95
102     RAJU  75
103     SITA  90

The view returns the selected STUDENT columns. The index and sequence are schema objects and may not display result rows when created.
```

## 6. RESULT
Thus, the view, sequence and index were created and the savepoint/rollback behavior was demonstrated successfully.

