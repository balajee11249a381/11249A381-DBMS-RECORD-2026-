# Experiment 3 — DCL and TCL Commands

## 1. AIM
To demonstrate Data Control Language (DCL) and Transaction Control Language (TCL) commands.

## 2. SOFTWARE REQUIRED
- Oracle Database or an Oracle-compatible SQL lab environment
- SQL*Plus or Oracle SQL Developer
- DBMS_OUTPUT enabled for PL/SQL exercises

## 3. ALGORITHM
1. Create or select the example STUDENT table and ensure the required user/privileges exist.
2. Use GRANT to provide a privilege to a database user.
3. Use REVOKE to remove that privilege.
4. Make a data change and set a savepoint within a transaction.
5. Demonstrate rollback and commit, then verify the final state.

## 4. PROGRAM / SQL COMMANDS
```sql
-- DCL: run using an account that owns STUDENT and can grant privileges.
GRANT SELECT ON STUDENT TO SYSTEM;
REVOKE SELECT ON STUDENT FROM SYSTEM;

-- TCL: demonstrate savepoint and rollback on a sample row.
UPDATE STUDENT SET MARKS = 95 WHERE ROLLNO = 101;
SAVEPOINT A;
UPDATE STUDENT SET MARKS = 80 WHERE ROLLNO = 101;
ROLLBACK TO A;
SELECT ROLLNO, MARKS FROM STUDENT WHERE ROLLNO = 101;
COMMIT;
```

## 5. OUTPUT
> The following is illustrative sample/expected output. It is not a screenshot or a claim that the SQL was executed in this repository. Run the program in your lab environment and capture your own result for submission.

```text
Expected behavior:
- GRANT gives the SELECT privilege to the named user, if permitted by the database.
- REVOKE removes the privilege.
- After ROLLBACK TO A, the MARKS value for ROLLNO 101 is 95 (assuming the first UPDATE affected one row).
- COMMIT makes the remaining transaction changes permanent.

Note: In managed or school accounts, granting/revoking privileges on SYSTEM may be disallowed.
Use a lab-provided user if your instructor specifies one.
```

## 6. RESULT
Thus, DCL and TCL commands were demonstrated successfully.

## Notes
Oracle privileges often require administrative authorization. Follow the lab account policy; avoid granting unnecessary privileges to SYSTEM in real databases.

