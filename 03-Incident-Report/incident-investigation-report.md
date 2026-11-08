# Security Incident Investigation Report

## 1. Incident Overview

**Incident Name:** Suspected Brute-Force Authentication Attack

**Investigation Type:** Authentication Analysis and Endpoint Investigation

**Role:** Security Operations Centre (SOC) Analyst

**Environment:** Simulated Windows Security Event Dataset

**Investigation Tool:** Azure Data Explorer / Kusto Query Language (KQL)

**Severity Assessment:** High – Suspected Account Compromise

**Investigation Date:** 6 November 2026

## 2. Executive Summary

A security investigation was conducted to identify suspicious authentication activity involving a simulated employee account

The analysis identified four consecutive failed authentication attempts against the account `j.mokoena`, originating from the source IP address `203.0.113.50`

A successful authentication event was subsequently recorded from the same source IP address

Further investigation identified PowerShell execution involving an encoded command on the workstation `WKSTN07`

The combination of repeated authentication failures, a subsequent successful login and suspicious PowerShell execution warrants further investigation

The available simulated evidence suggests a possible account compromise. However, additional telemetry would be required to confirm malicious activity.

## 3. Investigation Objectives

- Identify repeated failed authentication attempts
- Identify suspicious source IP addresses
- Correlate failed and successful login events
- Investigate suspicious PowerShell execution
- Assess the potential security impact
- Recommend appropriate incident response actions

## 4. Findings

### 4.1 Authentication Analysis

Windows Security Event ID 4625 was used to identify failed login attempts

Four failed authentication attempts were identified against:

- Account: j.mokoena
- Source IP: 203.0.113.50
- Target system: DC01

### 4.2 Successful Authentication

Windows Security Event ID 4624 was used to identify successful authentication activity

A successful login was recorded at 08:05 UTC, following four failed login attempts from the same source IP

This activity warrants further investigation because it could indicate that an attacker successfully authenticated after repeated password attempts

### 4.3 PowerShell Investigation

Windows Security Event ID 4688 represented process creation activity in the simulated dataset

The investigation identified:

- Computer: WKSTN07
- Account: j.mokoena
- Process: powershell.exe
- Command indicator: -EncodedCommand

Encoded PowerShell execution can be used to obscure commands and should be investigated in context

The available evidence does not independently establish malicious execution

## 5. Incident Timeline

| Time (UTC) | Activity |
|---|---|
| 08:00 | First failed login |
| 08:01 | Second failed login |
| 08:02 | Third failed login |
| 08:03 | Fourth failed login |
| 08:05 | Successful login |
| 08:10 | Encoded PowerShell execution |
 
## 6. Indicators of Compromise / Investigation Indicators

| Indicator | Value |
|---|---|
| Suspected account | j.mokoena |
| Source IP | 203.0.113.50 |
| Failed login count | 4 |
| Successful login | Yes |
| Endpoint | WKSTN07 |
| Suspicious process | powershell.exe |
| Command indicator | -EncodedCommand |

Note: The IP addresses used in this exercise belong to reserved documentation ranges and are not real attacker infrastructure

## 7. Recommended Response Actions

1. Validate the successful login with the account owner and authentication telemetry
2. Investigate the endpoint for suspicious process execution and child processes
3. Review additional authentication events associated with the source IP
4. Review MFA activity and identity sign-in logs
5. If compromise is confirmed, reset credentials and revoke active sessions according to organisational procedures
6. Preserve relevant logs and investigation evidence
7. Escalate the incident to the appropriate security team

## 8. Conclusion

The investigation successfully demonstrated how KQL can be used to identify repeated authentication failures, correlate successful logins and investigate potentially suspicious PowerShell activity

The findings indicate a potential brute-force attack followed by successful authentication

Further investigation would be required to determine whether the account was compromised and whether the PowerShell activity was malicious

## 9. Tools and Technologies

- Microsoft Azure Data Explorer
- Kusto Query Language (KQL)
- Windows Security Event IDs
- Microsoft Sentinel investigation concepts
- GitHub
