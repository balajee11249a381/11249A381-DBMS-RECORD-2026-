# Experiment 1 — Creation of Student, Employee and Library Databases

## 1. AIM
To create Student, Employee and Library tables, insert records, and retrieve the stored information.

## 2. SOFTWARE REQUIRED
- Oracle Database or an Oracle-compatible SQL lab environment
- SQL*Plus or Oracle SQL Developer
- DBMS_OUTPUT enabled for PL/SQL exercises

## 3. ALGORITHM
1. Start the SQL environment and select the working schema.
2. Create the required table with suitable columns and data types.
3. Insert sample records into each table.
4. Execute SELECT queries to display the stored records.
5. Verify the displayed rows and finish.

## 4. PROGRAM / SQL COMMANDS
```sql
-- 1(a) Student database
CREATE TABLE STUDENT (
  SID NUMBER(3),
  NAME VARCHAR2(20),
  MARKS NUMBER(3)
);
INSERT INTO STUDENT VALUES (101, 'RAVI', 85);
INSERT INTO STUDENT VALUES (102, 'RAJU', 75);
INSERT INTO STUDENT VALUES (103, 'SITA', 90);
SELECT * FROM STUDENT;

-- 1(b) Employee database
CREATE TABLE EMPLOYEE (
  EID NUMBER(3),
  NAME VARCHAR2(20),
  SALARY NUMBER(6)
);
INSERT INTO EMPLOYEE VALUES (101, 'RAVI', 25000);
INSERT INTO EMPLOYEE VALUES (102, 'RAJU', 30000);
INSERT INTO EMPLOYEE VALUES (103, 'SITA', 28000);
SELECT * FROM EMPLOYEE;

-- 1(c) Library database
CREATE TABLE LIBRARY (
  BOOKID NUMBER(3),
  TITLE VARCHAR2(20),
  PRICE NUMBER(5)
);
INSERT INTO LIBRARY VALUES (101, 'DBMS', 300);
INSERT INTO LIBRARY VALUES (102, 'JAVA', 250);
INSERT INTO LIBRARY VALUES (103, 'CN', 280);
SELECT * FROM LIBRARY;
```

## 5. OUTPUT
> The following is illustrative sample/expected output. It is not a screenshot or a claim that the SQL was executed in this repository. Run the program in your lab environment and capture your own result for submission.

```text
Expected result sets (SQL*Plus/SQL Developer formatting may differ):

STUDENT
SID  NAME  MARKS
101  RAVI  85
102  RAJU  75
103  SITA  90

EMPLOYEE
EID  NAME  SALARY
101  RAVI  25000
102  RAJU  30000
103  SITA  28000

LIBRARY
BOOKID  TITLE  PRICE
101     DBMS   300
102     JAVA   250
103     CN     280
```

## 6. RESULT
Thus, the Student, Employee and Library tables were created, populated, and queried successfully.

## Notes
No primary keys were added because this is a basic table-creation experiment based on the current record.

