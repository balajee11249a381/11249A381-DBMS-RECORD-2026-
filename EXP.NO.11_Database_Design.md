# Experiment 11 — Database Design Case Studies

## 1. AIM
To create example database tables for Student Information, Hospital Management, Railway Reservation, Timetable Management and Hotel Management systems.

## 2. SOFTWARE REQUIRED
- Oracle Database or an Oracle-compatible SQL lab environment
- SQL*Plus or Oracle SQL Developer
- DBMS_OUTPUT enabled for PL/SQL exercises

## 3. ALGORITHM
1. Identify the main entity and attributes for each case study.
2. Choose an appropriate primary key for each table.
3. Create the tables using suitable Oracle data types.
4. Insert sample records into each table.
5. Execute SELECT queries to display the stored data.

## 4. PROGRAM / SQL COMMANDS
```sql
-- 11(a) Student Information System
CREATE TABLE STUDENT_INFO (
  SID NUMBER(3) PRIMARY KEY,
  NAME VARCHAR2(20),
  MARKS NUMBER(3)
);
INSERT INTO STUDENT_INFO VALUES (101, 'RAVI', 85);
INSERT INTO STUDENT_INFO VALUES (102, 'RAJU', 75);
INSERT INTO STUDENT_INFO VALUES (103, 'SITA', 90);
SELECT * FROM STUDENT_INFO;

-- 11(b) Hospital Management System
CREATE TABLE PATIENT (
  PID NUMBER(3) PRIMARY KEY,
  NAME VARCHAR2(20),
  DISEASE VARCHAR2(20)
);
INSERT INTO PATIENT VALUES (101, 'RAVI', 'FEVER');
INSERT INTO PATIENT VALUES (102, 'RAJU', 'COLD');
INSERT INTO PATIENT VALUES (103, 'SITA', 'MALARIA');
SELECT * FROM PATIENT;

-- 11(c) Railway Reservation System
CREATE TABLE RESERVATION (
  TICKET_NO NUMBER(3) PRIMARY KEY,
  NAME VARCHAR2(20),
  TRAIN VARCHAR2(20)
);
INSERT INTO RESERVATION VALUES (101, 'RAVI', 'CHENNAI');
INSERT INTO RESERVATION VALUES (102, 'RAJU', 'BANGALORE');
INSERT INTO RESERVATION VALUES (103, 'SITA', 'HYDERABAD');
SELECT * FROM RESERVATION;

-- 11(d) Timetable Management System
CREATE TABLE TIMETABLE (
  DAY VARCHAR2(10),
  SUBJECT VARCHAR2(20),
  ROOM NUMBER(3)
);
INSERT INTO TIMETABLE VALUES ('MONDAY', 'JAVA', 101);
INSERT INTO TIMETABLE VALUES ('TUESDAY', 'DBMS', 102);
INSERT INTO TIMETABLE VALUES ('WEDNESDAY', 'CN', 103);
SELECT * FROM TIMETABLE;

-- 11(e) Hotel Management System
CREATE TABLE HOTEL (
  ROOM_NO NUMBER(3) PRIMARY KEY,
  GUEST_NAME VARCHAR2(20),
  ROOM_TYPE VARCHAR2(20)
);
INSERT INTO HOTEL VALUES (101, 'RAVI', 'SINGLE');
INSERT INTO HOTEL VALUES (102, 'RAJU', 'DOUBLE');
INSERT INTO HOTEL VALUES (103, 'SITA', 'DELUXE');
SELECT * FROM HOTEL;
```

## 5. OUTPUT
> The following is illustrative sample/expected output. It is not a screenshot or a claim that the SQL was executed in this repository. Run the program in your lab environment and capture your own result for submission.

```text
Expected row counts if each script runs successfully in an empty schema:
STUDENT_INFO — 3 rows
PATIENT — 3 rows
RESERVATION — 3 rows
TIMETABLE — 3 rows
HOTEL — 3 rows

For each SELECT, the inserted sample records should be displayed.
```

## 6. RESULT
Thus, the five example database designs were created and sample records were inserted and retrieved successfully.

