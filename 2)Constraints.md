# Experiment 2 — Creating a Table with Constraints

## 1. AIM
To create a table using PRIMARY KEY, NOT NULL, CHECK and UNIQUE constraints.

## 2. SOFTWARE REQUIRED
- Oracle Database or an Oracle-compatible SQL lab environment
- SQL*Plus or Oracle SQL Developer
- DBMS_OUTPUT enabled for PL/SQL exercises

## 3. ALGORITHM
1. Start the Oracle SQL environment.
2. Create the STUDENT1 table with the required constraints.
3. Insert records that satisfy each constraint.
4. Display the inserted records using SELECT.
5. Confirm that the table enforces the defined constraints.

## 4. PROGRAM / SQL COMMANDS
```sql
CREATE TABLE STUDENT1 (
  ROLLNO NUMBER(3) PRIMARY KEY,
  NAME VARCHAR2(20) NOT NULL,
  MARKS NUMBER(3) CHECK (MARKS >= 0),
  EMAIL VARCHAR2(30) UNIQUE
);

INSERT INTO STUDENT1 VALUES (101, 'RAVI', 85, 'ravi@gmail.com');
INSERT INTO STUDENT1 VALUES (102, 'RAJU', 75, 'raju@gmail.com');
INSERT INTO STUDENT1 VALUES (103, 'SITA', 90, 'sita@gmail.com');

SELECT * FROM STUDENT1;
```

## 5. OUTPUT
> The following is illustrative sample/expected output. It is not a screenshot or a claim that the SQL was executed in this repository. Run the program in your lab environment and capture your own result for submission.

```text
Expected result set:

ROLLNO  NAME  MARKS  EMAIL
101     RAVI  85     ravi@gmail.com
102     RAJU  75     raju@gmail.com
103     SITA  90     sita@gmail.com

The CREATE TABLE statement should complete successfully. Duplicate primary-key values,
duplicate non-NULL email values, NULL names, or negative marks violate the defined constraints.
```

## 6. RESULT
Thus, the STUDENT1 table was created and records were inserted using the specified constraints.

