# Experiment 10 — PL/SQL Conditions, Exceptions, Procedures, Functions, Triggers and Cursors

## 1. AIM
To execute PL/SQL programs using conditional statements, exception handling, procedures, functions, database triggers, and implicit and explicit cursors.

## 2. SOFTWARE REQUIRED
- Oracle Database or an Oracle-compatible SQL lab environment
- SQL*Plus or Oracle SQL Developer
- DBMS_OUTPUT enabled for PL/SQL exercises

## 3. ALGORITHM
1. Enable server output in SQL*Plus or SQL Developer.
2. Write and execute a PL/SQL block with an IF conditional statement.
3. Handle the ZERO_DIVIDE exception in a PL/SQL block.
4. Create and call a stored procedure and create/query a stored function.
5. Create a table and triggers, then demonstrate implicit and explicit cursor processing.

## 4. PROGRAM / SQL COMMANDS
```sql
SET SERVEROUTPUT ON;

-- 10(a) Conditional statement
DECLARE
  N NUMBER := &N;
BEGIN
  IF N > 0 THEN
    DBMS_OUTPUT.PUT_LINE('Positive Number');
  ELSIF N = 0 THEN
    DBMS_OUTPUT.PUT_LINE('Zero');
  ELSE
    DBMS_OUTPUT.PUT_LINE('Negative Number');
  END IF;
END;
/

-- 10(b) Exception handling
DECLARE
  A NUMBER := 10;
  B NUMBER := 0;
  C NUMBER;
BEGIN
  C := A / B;
  DBMS_OUTPUT.PUT_LINE(C);
EXCEPTION
  WHEN ZERO_DIVIDE THEN
    DBMS_OUTPUT.PUT_LINE('Cannot divide by zero');
END;
/

-- 10(c) Procedure
CREATE OR REPLACE PROCEDURE GREET AS
BEGIN
  DBMS_OUTPUT.PUT_LINE('Hello Student');
END;
/
EXEC GREET;

-- Function
CREATE OR REPLACE FUNCTION ADD_NUM
RETURN NUMBER AS
BEGIN
  RETURN 10 + 20;
END;
/
SELECT ADD_NUM() AS RESULT FROM DUAL;

-- 10(d) Triggers: create table before compiling triggers
CREATE TABLE STUDENT (
  ROLLNO NUMBER(3), NAME VARCHAR2(20), MARKS NUMBER(3)
);
CREATE OR REPLACE TRIGGER STUDENT_INSERT
AFTER INSERT ON STUDENT
BEGIN
  DBMS_OUTPUT.PUT_LINE('Record Inserted');
END;
/
CREATE OR REPLACE TRIGGER STUDENT_UPDATE
AFTER UPDATE ON STUDENT
BEGIN
  DBMS_OUTPUT.PUT_LINE('Record Updated');
END;
/
CREATE OR REPLACE TRIGGER STUDENT_DELETE
AFTER DELETE ON STUDENT
BEGIN
  DBMS_OUTPUT.PUT_LINE('Record Deleted');
END;
/
INSERT INTO STUDENT VALUES (101, 'RAVI', 85);
UPDATE STUDENT SET MARKS = 90 WHERE ROLLNO = 101;
DELETE FROM STUDENT WHERE ROLLNO = 101;

-- 10(e) Implicit cursor
BEGIN
  UPDATE STUDENT SET MARKS = 90 WHERE ROLLNO = 101;
  DBMS_OUTPUT.PUT_LINE(SQL%ROWCOUNT || ' row(s) updated');
END;
/

-- Explicit cursor (insert rows before running this block if needed)
INSERT INTO STUDENT VALUES (101, 'RAVI', 85);
INSERT INTO STUDENT VALUES (102, 'RAJU', 75);

DECLARE
  CURSOR C1 IS SELECT NAME, MARKS FROM STUDENT ORDER BY ROLLNO;
  V_NAME STUDENT.NAME%TYPE;
  V_MARKS STUDENT.MARKS%TYPE;
BEGIN
  OPEN C1;
  LOOP
    FETCH C1 INTO V_NAME, V_MARKS;
    EXIT WHEN C1%NOTFOUND;
    DBMS_OUTPUT.PUT_LINE(V_NAME || ' ' || V_MARKS);
  END LOOP;
  CLOSE C1;
END;
/
```

## 5. OUTPUT
> The following is illustrative sample/expected output. It is not a screenshot or a claim that the SQL was executed in this repository. Run the program in your lab environment and capture your own result for submission.

```text
Expected sample output (individual commands/blocks produce output separately):
10(a), input N = 7:
Positive Number

10(b):
Cannot divide by zero

Procedure call:
Hello Student

Function query:
RESULT
------
30

Trigger messages when INSERT / UPDATE / DELETE statements are executed may be shown as DBMS_OUTPUT messages depending on the client and how output is enabled.

Implicit cursor example:
1 row(s) updated — only if a matching ROLLNO exists.

Explicit cursor example:
RAVI 85
RAJU 75

Important: the sample program is a teaching sequence. Since the delete occurs before the implicit-cursor update in this order, re-insert the row before running the implicit-cursor block, or run the cursor section independently. Do not treat illustrative output as a captured database screenshot.
```

## 6. RESULT
Thus, PL/SQL conditions, exception handling, procedures, functions, triggers, and implicit and explicit cursor concepts were demonstrated.

