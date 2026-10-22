# Experiment 7 — ANY, ALL, IN, EXISTS, NOT EXISTS, UNION and INTERSECT

## 1. AIM
To execute SQL queries using IN, ANY, ALL, EXISTS, NOT EXISTS, UNION and INTERSECT.

## 2. SOFTWARE REQUIRED
- Oracle Database or an Oracle-compatible SQL lab environment
- SQL*Plus or Oracle SQL Developer
- DBMS_OUTPUT enabled for PL/SQL exercises

## 3. ALGORITHM
1. Create and populate STUDENT and STUDENT2 tables.
2. Use IN to select rows matching a list of marks.
3. Use ANY and ALL to compare a value with the results of a subquery.
4. Use EXISTS and NOT EXISTS to test matching keys in the other table.
5. Use UNION and INTERSECT to combine or compare names from both tables.

## 4. PROGRAM / SQL COMMANDS
```sql
CREATE TABLE STUDENT (
  ROLLNO NUMBER(3), NAME VARCHAR2(20), MARKS NUMBER(3)
);
INSERT INTO STUDENT VALUES (101, 'RAVI', 85);
INSERT INTO STUDENT VALUES (102, 'RAJU', 75);
INSERT INTO STUDENT VALUES (103, 'SITA', 90);

CREATE TABLE STUDENT2 (
  ROLLNO NUMBER(3), NAME VARCHAR2(20), MARKS NUMBER(3)
);
INSERT INTO STUDENT2 VALUES (101, 'RAVI', 85);
INSERT INTO STUDENT2 VALUES (104, 'RAM', 80);
INSERT INTO STUDENT2 VALUES (105, 'KIRAN', 70);

-- IN
SELECT * FROM STUDENT WHERE MARKS IN (75, 90);

-- ANY
SELECT * FROM STUDENT
WHERE MARKS > ANY (SELECT MARKS FROM STUDENT2);

-- ALL
SELECT * FROM STUDENT
WHERE MARKS > ALL (SELECT MARKS FROM STUDENT2);

-- EXISTS
SELECT * FROM STUDENT S
WHERE EXISTS (SELECT 1 FROM STUDENT2 S2 WHERE S.ROLLNO = S2.ROLLNO);

-- NOT EXISTS
SELECT * FROM STUDENT S
WHERE NOT EXISTS (SELECT 1 FROM STUDENT2 S2 WHERE S.ROLLNO = S2.ROLLNO);

-- UNION
SELECT NAME FROM STUDENT
UNION
SELECT NAME FROM STUDENT2;

-- INTERSECT
SELECT NAME FROM STUDENT
INTERSECT
SELECT NAME FROM STUDENT2;
```

## 5. OUTPUT
> The following is illustrative sample/expected output. It is not a screenshot or a claim that the SQL was executed in this repository. Run the program in your lab environment and capture your own result for submission.

```text
Expected key results:
IN (75, 90): RAJU (75), SITA (90)
ANY: all three STUDENT rows qualify because each mark exceeds at least one mark in STUDENT2 (minimum 70).
ALL: RAVI (85) and SITA (90) qualify because both marks exceed the maximum mark in STUDENT2 (80).
EXISTS: RAVI (ROLLNO 101)
NOT EXISTS: RAJU (102), SITA (103)
UNION: distinct names across both tables — KIRAN, RAVI, RAJU, RAM, SITA (order may vary)
INTERSECT: RAVI
```

## 6. RESULT
Thus, the specified comparison, existence and set operators were demonstrated successfully.

