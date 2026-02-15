# Wazuh File Integrity Monitoring (FIM) – Windows 11 (Cloud SIEM)

## Overview
In this project, I used **Wazuh Cloud (Trial)** as the SIEM platform and installed the **Wazuh Agent on my personal Windows 11 system**.
The objective was to demonstrate how File Integrity Monitoring (FIM) detects real file activity performed on a Windows endpoint.

This repository is a **project showcase** of what I implemented, tested, and observed.

---

## Why Wazuh Cloud Trial
I used the Wazuh Cloud trial to simulate a real-world SOC environment where SIEM infrastructure is centrally managed. 
Using the cloud also reduced local system load by offloading SIEM processing and correlation, allowing my Windows 11 endpoint to maintain normal performance while focusing on monitoring and alert analysis.

---

## Environment
- SIEM : Wazuh Cloud (Trial)
- Endpoint : Windows 11 (Personal Machine)
- Agent : Wazuh Windows Agent
- Feature : File Integrity Monitoring (FIM)

---

## Setup Summary
- Created a Wazuh Cloud trial account
- Connected my Windows 11 machine using Wazuh Agent
- Configured FIM to monitor a custom folder on Local Disk (D:)
- Performed multiple file operations
- Verified alerts in Wazuh Cloud Dashboard
![Wazuh Agent Connected](screenshots/agent-connected.png)

---

## Monitored Folder
I created and monitored the following directory on my system:

D:\Jaswinder-FIM-Test

This folder was used to safely perform all file activity tests.


![FIM Configuration on Windows Agent](screenshots/fim-windows-config.png)

---

## Activities Performed

### File Creation
I created a new text file inside the monitored folder using Notepad.

Evidence:
![File Creation Alert](screenshots/file-created-alert.png)

---

### File Rename
I renamed the text file inside the monitored folder.

Evidence:
![File Rename Alert](screenshots/file-rename-alert.png)

---

### File Content Modification
I opened the file in Notepad, added content, and saved it.

Evidence:
![File Modification Alert](screenshots/file-modification-alert.png)

---


### Permission Change
I modified file permissions on a monitored file to test access control change detection.

Observation:
The permission change resulted in an integrity checksum change alert, which is expected behavior on Windows systems where permission metadata affects file integrity.

Evidence:
![File Permission Change Alert](screenshots/file-permission-change-alert.png)

---

### File Deletion
I deleted the file from the monitored folder.

Evidence:
![File Deletion Alert](screenshots/file-deletion-alert.png)

---

## Results
- All file activities were detected successfully
- Alerts were generated in near real time
- File path, event type, and timestamps were visible in the dashboard
- The alerts provided sufficient context for basic investigation, including file path, event type, rule level, and timestamps.
![FIM Dashboard Overview](screenshots/dashboard-overview.png)

---
## Screenshots Structure
All screenshots captured during this project are stored in the **screenshots** directory.

```
screenshots/
├── agent-connected.png
├── fim-windows-config.png
├── file-created-alert.png
├── file-rename-alert.png
├── file-modification-alert.png
├── file-permission-change-alert.png
├── file-deletion-alert.png
└── dashboard-overview.png
```

## Key Learnings
- This project helped me understand how small file changes on a Windows endpoint can trigger security alerts in a SIEM.
- I learned how File Integrity Monitoring works on Windows systems using a cloud-based SIEM.
- Analyzing real alerts in the Wazuh dashboard improved my understanding of endpoint monitoring from a SOC perspective.

---

## SOC Relevance
This project demonstrates how SOC teams can use FIM to:
- Monitor endpoint file activity
- Detect unauthorized file changes
- Support incident investigation
- Improve endpoint visibility
- Supports file integrity requirements commonly seen in compliance standards such as PCI-DSS and ISO 27001.

---

## Resume Statement
Implemented File Integrity Monitoring (FIM) using Wazuh Cloud SIEM by monitoring a Windows 11 endpoint and analyzing alerts generated from file creation, modification, renaming, deletion, and permission changes.

---

## Author
Name: Jaswinder Singh Rawat  
Role: SOC Analyst Intern

---

## Disclaimer
This project was performed on a personal Windows system in a controlled environment for learning and demonstration purposes only.
