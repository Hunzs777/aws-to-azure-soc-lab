# AWS to Azure SOC Lab

## Overview

This project shows a simple SOC lab using AWS and Azure.

A Windows Server was created in AWS EC2. Sysmon was installed to collect logs.  
These logs were sent to Azure and analyzed in Microsoft Sentinel.

The goal is to simulate real attack behavior and detect it using KQL queries.

---

## Architecture

![Architecture](screenshots/01-diagram.png)

This diagram shows the full data flow from AWS to Azure Sentinel.

---

## Lab Setup

### AWS EC2 Setup

![EC2 Created](screenshots/02-aws-ec2-created.png)

A Windows Server instance was created in AWS EC2.

---

### Sysmon Installation

![Sysmon Installed](screenshots/03-sysmon-installed.png)

Sysmon was installed to collect system activity logs.

---

### Sysmon Test

![Whoami Test](screenshots/04-whoami-test.png)

A test command (whoami) was executed to generate events.

---

### Event Viewer Check

![Sysmon Events](screenshots/05-eventviewer-sysmon.png)

Sysmon logs were verified in Event Viewer.

---

## Azure Integration

### Microsoft Sentinel Setup

![Sentinel Created](screenshots/06-sentinel-created.png)

Microsoft Sentinel was enabled on the workspace.

---

### Azure Arc Connection

![Azure Arc](screenshots/07-azure-arc-created.png)

The AWS EC2 machine was connected using Azure Arc.

---

### Azure Monitor Agent

![AMA Installed](screenshots/08-azure-monitor-agent-created.png)

Azure Monitor Agent was installed on the machine.

---

### Data Collection Rule

![DCR Setup](screenshots/09-azure-monitor-agent-dcr-deployed.png)

Data Collection Rules were configured to collect logs.

---

### Logs in Sentinel

![Logs](screenshots/10-azure-sentinel-logs-created.png)

Logs started to appear in Microsoft Sentinel.

---

## Detection & Analysis

### Analytics Rules

![Rules](screenshots/11-azure-analytics-rules-created.png)

Custom detection rules were created using KQL.

---

### Alerts

![Alerts](screenshots/12-azure-sentinel-alerts.png)

Alerts were generated based on custom analytics rules.

- Brute force detection identified multiple failed login attempts in a short time  
- Suspicious file download activity was detected using PowerShell with external URLs  
- Suspicious process execution detected commands like whoami and net user  
- Registry persistence activity was flagged when run keys were modified  

These alerts simulate real attacker behavior and show how detection works in a SOC environment.

---

## Results

### Incidents

![Incidents](screenshots/13-azure-sentinel-incidents.png)

Detected alerts were grouped into incidents.

---

## Conclusion

This project demonstrates a basic SOC workflow.

It includes:

- Log collection with Sysmon  
- Data ingestion to Azure  
- Threat detection using KQL  
- Alert and incident creation  

This lab helped me understand how real SOC environments work.
