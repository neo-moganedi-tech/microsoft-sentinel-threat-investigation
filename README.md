Microsoft Sentinel Threat Investigation Lab

![Security](https://img.shields.io/badge/Domain-Cybersecurity-blue)
![KQL](https://img.shields.io/badge/Language-KQL-orange)
![Microsoft](https://img.shields.io/badge/Platform-Microsoft%20Security-blue)
![Status](https://img.shields.io/badge/Project-Completed-success)

## Project Overview

This project demonstrates practical Security Operations Centre (SOC) investigation techniques in preparation for the Microsoft SC-200: Security Operations Analyst certification

The investigation focuses on identifying suspicious authentication activity, detecting potential brute-force attacks, correlating failed and successful login events, and analysing potentially suspicious PowerShell execution

The lab uses simulated Windows security events and Kusto Query Language (KQL) in the public Azure Data Explorer environment

## Objectives

- Understand Windows Security Event IDs
- Analyse authentication events using KQL
- Detect repeated failed login attempts
- Identify suspicious source IP addresses
- Correlate failed and successful authentication events
- Investigate suspicious PowerShell command execution
- Develop incident investigation and response recommendations
- Practise technical documentation and security reporting

## Technologies Used

| Technology | Purpose |
|---|---|
| Azure Data Explorer | KQL query environment |
| Kusto Query Language | Security event analysis |
| Windows Security Events | Simulated investigation data |
| Microsoft Sentinel concepts | SIEM investigation techniques |
| GitHub | Project documentation and version control |

## Lab Environment

**Environment:** Public Azure Data Explorer help cluster

**Database:** Samples (query context)

**Data Source:** Custom simulated Windows security events using KQL `datatable()`

**Cost:** Free public environment. No Azure subscription or paid Sentinel workspace was deployed

## Investigation Scenario

A simulated organisation detects suspicious authentication activity involving an employee account

The SOC analyst is assigned to investigate possible brute-force activity and determine whether a successful login occurred following repeated authentication failures

Further investigation is conducted to identify potentially suspicious PowerShell execution

## Investigation Exercises

### 1. Security Event Analysis

Analysed Windows Security Event IDs:

- 4624 – Successful logon
- 4625 – Failed logon
- 4688 – Process creation

**Query:** `01-security-event-analysis.kql`

### 2. Brute-Force Detection

Identified repeated failed authentication attempts and grouped events by account and source IP

**Key finding:** Four failed login attempts against `j.mokoena` from `203.0.113.50`

**Query:** `02-brute-force-detection.kql`

### 3. Authentication Correlation

Correlated repeated failed authentication events with a subsequent successful login

**Key finding:** A successful login occurred at 08:05 UTC after four failed attempts

**Query:** `03-successful-login-correlation.kql`

### 4. Suspicious PowerShell Investigation

Investigated PowerShell process execution and identified an encoded command indicator

**Key finding:** An encoded PowerShell command was identified on workstation `WKSTN07`

**Query:** `04-suspicious-powershell-investigation.kql`

## Incident Investigation Findings

| Investigation | Result |
|---|---|
| Suspicious account | j.mokoena |
| Failed login attempts | 4 |
| Source IP | 203.0.113.50 |
| Successful login | Identified |
| Suspicious endpoint | WKSTN07 |
| Process investigated | powershell.exe |
| Encoded command indicator | Identified |

## Recommended Incident Response

1. Validate the successful login with the account owner
2. Investigate the source IP and related authentication activity
3. Review MFA and identity sign-in telemetry
4. Investigate PowerShell execution and related processes
5. Reset credentials and revoke sessions if compromise is confirmed
6. Preserve investigation evidence
7. Escalate confirmed incidents according to organisational procedures

## Evidence and Screenshots

Screenshots of the investigation are stored in the `02-Screenshots` directory

- `01-Azure-Data-Explorer-Environment.png`
- `02-Security-Event-Analysis.png`
- `03-Brute-Force-Detection.png`
- `04-Successful-Login-Correlation.png`
- `05-Suspicious-PowerShell-Investigation.png`

## Skills Demonstrated

- Kusto Query Language (KQL)
- Security event analysis
- Authentication monitoring
- Brute-force detection
- Log correlation
- Threat hunting fundamentals
- Endpoint investigation
- Incident analysis
- Security documentation
- SOC investigation methodology

## SC-200 Relevance

This lab supports preparation for the Microsoft Security Operations Analyst certification through practical exposure to:

- KQL-based threat detection
- Security event analysis
- Authentication investigation
- Threat hunting
- Incident investigation
- Security operations reporting

## Learning Outcomes

Through this project, I practised how to:

- Build and execute KQL queries
- Filter and aggregate security events
- Identify suspicious authentication patterns
- Correlate security events using common entities
- Investigate potentially suspicious endpoint activity
- Interpret security findings and recommend appropriate response actions

## References

- [Microsoft SC-200 Certification](https://learn.microsoft.com/en-us/credentials/certifications/exams/sc-200)
- [Microsoft SC-200 Study Guide](https://learn.microsoft.com/en-us/credentials/certifications/resources/study-guides/SC-200)
- [Azure Data Explorer](https://dataexplorer.azure.com/)
- [Azure Data Explorer KQL Documentation](https://learn.microsoft.com/en-us/azure/data-explorer/kusto/query/)
- [Microsoft Sentinel Documentation](https://learn.microsoft.com/en-us/azure/sentinel/)

---

**Project Type:** Personal Cybersecurity Lab

**Focus:** Security Operations / Threat Hunting / KQL

**Certification Preparation:** Microsoft SC-200

**Author:** Neo Moganedi

