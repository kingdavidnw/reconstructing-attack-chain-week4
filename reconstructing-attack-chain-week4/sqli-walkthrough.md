# SQL Injection Investigation

## Purpose

The Week 4 lab included a search endpoint that accepted a user-controlled query parameter.

The supplied source code constructed a SQL statement by concatenating the input directly into the query. This is unsafe because SQL syntax supplied through the parameter can alter the intended statement.

## Lab Observation

The investigation first established normal endpoint behavior and then used controlled malformed input to observe database error behavior. Subsequent controlled tests established the number of columns required for a compatible `UNION` result and demonstrated that lab records could be returned through the vulnerable query.

## Impact

In a real application, this class of vulnerability could allow unauthorized reading or modification of database information, depending on database permissions and query context.

In this lab, the impact was limited to synthetic/instructor-provided data.

## Defensive Control

Use parameterized queries/prepared statements. User input should be passed as a parameter rather than concatenated into SQL syntax.

Additional controls include least-privilege database accounts, input validation, error handling that does not expose database details, and monitoring for injection patterns.
