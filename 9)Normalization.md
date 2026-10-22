# Experiment 9 — Database Normalization from 1NF to 5NF

## 1. AIM
To study database normalization and decompose relations to reduce redundancy and update anomalies, up to 1NF, 2NF, 3NF, 4NF and 5NF.

## 2. SOFTWARE REQUIRED
- Oracle Database or an Oracle-compatible SQL lab environment
- SQL*Plus or Oracle SQL Developer
- DBMS_OUTPUT enabled for PL/SQL exercises

## 3. ALGORITHM
1. Identify the relation attributes, candidate keys and dependencies from the given scenario.
2. Convert the unnormalized relation to 1NF by storing atomic values only.
3. Convert to 2NF by removing partial dependencies on part of a composite candidate key.
4. Convert to 3NF by removing transitive dependencies of non-key attributes.
5. Check for non-trivial multivalued dependencies (4NF) and join dependencies (5NF), decomposing only where justified.

## 4. PROGRAM / SQL COMMANDS
```sql
Illustrative relation:
STUDENT_COURSE_PHONE(SID, SNAME, COURSE, PHONE)

Example functional dependency:
SID -> SNAME

If each student may take many courses and have many phone numbers independently,
the combined rows can repeat student details and create update anomalies.

Possible decomposition:
STUDENT(SID, SNAME)
STUDENT_COURSE(SID, COURSE)
STUDENT_PHONE(SID, PHONE)

1NF: every attribute value is atomic.
2NF: every non-prime attribute is fully functionally dependent on each candidate key.
3NF: for every non-trivial FD X -> A, X is a superkey or A is prime (standard 3NF test).
4NF: every non-trivial multivalued dependency has a superkey determinant.
5NF: every non-trivial join dependency is implied by candidate keys.
```

## 5. OUTPUT
> The following is illustrative sample/expected output. It is not a screenshot or a claim that the SQL was executed in this repository. Run the program in your lab environment and capture your own result for submission.

```text
Concept summary:
1NF — atomic values; no repeating groups.
2NF — no partial dependency of a non-prime attribute on a candidate key.
3NF — no disallowed transitive/non-key dependency; use the formal 3NF test.
4NF — no non-trivial multivalued dependency unless its determinant is a superkey.
5NF — no non-trivial join dependency except those implied by candidate keys.

The exact decompositions depend on the real functional, multivalued and join dependencies of the problem.
```

## 6. RESULT
Thus, the principles and dependency tests used for normalization through 5NF were studied.

