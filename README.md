## SOC Tier 1 Lab — Brute Force Detection (Windows Event ID 4625)

# Overview
This project demonstrates SOC Tier 1 security operations using Microsoft Sentinel (SIEM) and Microsoft Defender to detect, investigate, and resolve brute-force authentication attempts based on Windows Security Event ID 4625 (Failed Logon).

The lab follows a real-world SOC workflow, covering log ingestion, detection engineering, incident triage, false positive analysis, and incident resolution.

# Architecture
Data Flow

Windows 11 VM
   ↓
Azure Monitor Agent (AMA)
   ↓
Log Analytics Workspace
   ↓
Microsoft Sentinel (SIEM)
   ↓
Microsoft Defender (XDR)
   ↓
SOC Tier 1 Incident Triage & Resolution

# Environment Setup

# Resource Group
All resources were deployed inside a dedicated Azure resource group for isolation and management.

# Screenshot  
01-resource-group.png`

# Log Analytics Workspace
A Log Analytics workspace was created to collect and store Windows security telemetry.

# Screenshot  
02-log-analytics-workspace.png`

# Microsoft Sentinel (SIEM)
Microsoft Sentinel was enabled on the Log Analytics workspace to provide SIEM capabilities such as analytics rules, incidents, and investigations.

# Screenshot  
03-sentinel-enabled.png`

# Windows Endpoint
A Windows 11 virtual machine was deployed to generate authentication activity and security logs.

# Screenshot  
04-windows-vm.png`

# Log Ingestion & Telemetry

# Windows Security Events via Azure Monitor Agent (AMA)
Windows Security Events were connected using Azure Monitor Agent (AMA) to ensure supported and reliable log ingestion.

# Screenshot  
05-windows-logs-connected.png`

# Endpoint Verification (Event Viewer)
Failed logon attempts were intentionally generated on the Windows VM to validate local logging.

# Screenshot  
06-eventviewer-4625.png`

# SIEM Detection & Analysis

# Sentinel Log Query
Windows Event ID 4625 logs were successfully ingested into Sentinel and validated using log queries.

# Screenshot  
`07-sentinel-4625.png

# Analytics Rule — Brute Force Detection
A scheduled analytics rule was created to detect multiple failed logon attempts within a short time window.

# Screenshot  
08-analytics-rule.png`

# Rule Logic (Summary):
- Filter Windows Security Event ID 4625
- Aggregate failed attempts by account and endpoint
- Trigger an incident when thresholds are exceeded

# Incident Response (SOC Tier 1 Workflow)

# Incident Creation
The analytics rule automatically generated incidents when brute-force patterns were detected.

# Incident Triage & Resolution
One incident was selected and fully investigated following SOC Tier 1 procedures.

# Screenshot  
`09-incident-triage-bruteforce-4625.png`

# Triage Findings:
- Multiple failed logons detected
- Single endpoint and single user account involved
- No successful authentication observed
- No lateral movement or additional malicious indicators

# Disposition:
- Classification: Benign Positive  
- Determination: False Positive (user password entry errors)  
- Severity: Medium  
- Status: Resolved  





