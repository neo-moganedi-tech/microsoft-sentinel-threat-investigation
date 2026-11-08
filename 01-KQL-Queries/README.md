# KQL Investigation Queries

## Overview

This directory contains the Kusto Query Language (KQL) scripts developed during my Microsoft SC-200 Security Operations Analyst preparation lab

The queries demonstrate practical security investigation techniques using simulated Windows security events

## Query Files

| Filename | Description |
|---|---|
| `01-security-event-analysis.kql` | Analyses Windows security events and identifies authentication activity |
| `02-brute-force-detection.kql` | Identifies repeated failed authentication attempts grouped by account and source IP |
| `03-successful-login-correlation.kql` | Correlates failed authentication attempts with subsequent successful logins |
| `04-suspicious-powershell-investigation.kql` | Identifies potentially suspicious PowerShell execution involving encoded commands |

## Skills Demonstrated

- Kusto Query Language (KQL)
- Filtering and sorting security events
- Aggregating authentication events using `summarize`
- Correlating security events using `join`
- Identifying suspicious authentication patterns
- Investigating potentially suspicious endpoint activity

## Execution Environment

- Platform: Azure Data Explorer
- Cluster: `help`
- Database context: `Samples`
- Data: Custom simulated security events using KQL `datatable()`

---

**Project:** Microsoft Sentinel Threat Investigation Lab

**Author:** Neo Moganedi
