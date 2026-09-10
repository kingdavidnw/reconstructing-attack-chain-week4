# Week 4 Service Map

## Authorized Lab Components

| Component | Purpose | Security Relevance |
|---|---|---|
| Web/application service | Application functionality | Input validation and authentication |
| OAuth-style service | Authorization/token workflow | Redirects, codes, tokens, client validation |
| PostgreSQL | Application database | SQL injection impact and privilege boundaries |
| Redis | Application data/cache service | Network exposure and administrative controls |
| Kali Linux | Security testing workstation | Authorized reconnaissance and testing |

## Attack-Chain Relationship

Reconnaissance → exposed services → authentication/token analysis → vulnerable application input → database access → exposed Redis functionality → privileged data exposure.

All testing was limited to the supplied laboratory environment.
