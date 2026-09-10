# Reconstructing an Attack Chain: From Unauthenticated Entry to Privileged Data Exfiltration

**Student:** KingDavid Nwachukwu  
**Course/Project:** Operation Secure Core — Week 4  
**Repository:** `reconstructing-attack-chain-week4`

## Project Overview

This project reconstructs an authorized cybersecurity attack chain in a controlled Week 4 laboratory environment. The investigation connects reconnaissance, authentication/token weaknesses, SQL injection, database access, and Redis misconfiguration into a single attack narrative.

The work was performed only against the instructor-provided/lab environment and synthetic lab data.

## Research Question

How can weaknesses across exposed services, authentication/token handling, application input validation, database queries, and Redis configuration be chained to move from initial access to privileged data exposure?

## Objectives

- Identify exposed services in the authorized lab environment.
- Investigate the authentication and OAuth-style workflow.
- Analyze application behavior and source code for security weaknesses.
- Demonstrate the impact of SQL injection using controlled lab data.
- Investigate insecure Redis configuration and exposed functionality.
- Reconstruct the attack chain and identify defensive controls.
- Document findings, limitations, risks, and recommendations.

## Scope

The investigation covered the services and application components provided for Week 4, including the web application, OAuth-style lab service, PostgreSQL, and Redis. Testing was limited to the authorized laboratory environment.

## Methodology

1. **Reconnaissance** — identify reachable services and exposed ports.
2. **Authentication analysis** — inspect the OAuth-style authorization/token flow and protected endpoint behavior.
3. **Application analysis** — review the supplied application code and identify unsafe input handling.
4. **SQL injection investigation** — test the search endpoint with controlled payloads and synthetic database records.
5. **Redis investigation** — inspect exposed Redis functionality and configuration.
6. **Attack-chain reconstruction** — correlate observations into a sequence and map each weakness to defensive controls.
7. **Documentation** — record evidence, findings, limitations, and recommendations.

## Technical Findings

### 1. Service Exposure

The lab reconnaissance identified multiple reachable services. The exposed attack surface provided the starting point for subsequent investigation.

### 2. Authentication and Token Handling

The OAuth-style lab workflow demonstrated authorization-code and token exchange behavior. The investigation showed why redirect URI validation, client authentication, short-lived authorization codes, secure token handling, and protected endpoints are important.

### 3. SQL Injection

The supplied search endpoint constructed a SQL query by directly concatenating the user-controlled `q` parameter. This created an injection condition in the lab application.

The investigation used controlled test input to establish the behavior and demonstrate extraction from synthetic lab tables. No production database or real user data was targeted.

### 4. Redis Exposure and Misconfiguration

The lab Redis service was reachable and accepted commands that should be restricted in a hardened deployment. The investigation demonstrated the security impact of unrestricted administrative functionality.

### 5. Privileged Data Exposure

The combined weaknesses showed how an attacker could progress from exposed services and application weaknesses toward privileged information in the controlled lab environment.

## Defensive Recommendations

- Require authentication and authorization on sensitive application endpoints.
- Use parameterized SQL queries/prepared statements instead of string concatenation.
- Validate and constrain all user-controlled input.
- Enforce strict OAuth redirect URI validation.
- Protect client secrets and access/refresh tokens.
- Use short-lived authorization codes and invalidate them after use.
- Restrict Redis network exposure to trusted application hosts.
- Require Redis authentication where appropriate and disable unnecessary administrative commands.
- Apply least privilege to database and application accounts.
- Monitor authentication, database, and Redis activity for anomalous behavior.
- Never commit credentials, tokens, private keys, or environment secrets to source control.

## Reproducibility and Safety

This repository is intended to document the authorized Week 4 laboratory exercise. It intentionally excludes real credentials, access tokens, private keys, `.env` files, production secrets, and unnecessary personal information.

Any command examples should be run only against an authorized lab environment.

## Evidence

The `evidence/` directory is reserved for **student-captured lab screenshots** and other safe evidence. Before publishing screenshots, redact passwords, API keys, client secrets, access tokens, refresh tokens, private keys, and other sensitive values.

No fabricated or AI-generated image should be represented as proof of work actually performed.

## AI Assistance Disclosure

AI tools were used to assist with organization, explanation, editing, and documentation of the project. Technical conclusions were based on the authorized Week 4 laboratory materials and observed lab results. AI-generated content is not presented as independent experimental evidence.

## References

- OWASP Foundation — Web application security guidance.
- OWASP SQL Injection Prevention Cheat Sheet.
- OWASP Authentication and OAuth-related guidance.
- Redis security documentation.
- Instructor-provided Operation Secure Core — Week 4 Class 1 and Class 2 materials.

## Project Status

**Documentation:** Complete  
**Repository safety:** No credentials or secrets intentionally included  
**Evidence:** Add only genuine student-captured screenshots before final publication
