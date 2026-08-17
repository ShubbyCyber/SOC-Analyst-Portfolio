# SOC Analyst Portfolio

Welcome to my defensive security portfolio. Here, I will document my hands-on SOC lab writeups, SIEM detection rules, incident response reports, and threat analysis playbooks as I complete them.

## 🛠️ Tools & Technologies
* **SIEM:** Wazuh
* **Endpoint Telemetry:** Sysmon, Windows Event Logs
* **Analysis:** Wireshark, CyberChef, VirusTotal


## 📁 Projects
### 1. Wazuh SIEM & Windows Telemetry Home Lab (In Progress)
* **Goal:** Build a dedicated SOC lab to ingest, analyze, and detect endpoint threat activity using Wazuh SIEM.
* ![VirtualBox Setup](Virtual%20Box.jpeg)
* **Current Progress:** 
  * Configured Oracle VirtualBox environment and successfully booted the Wazuh v4.14.7 OVA server. ![Wazuh Server Terminal](Wazuh.jpeg)
  * Solved hypervisor resource allocation limits and configured NAT port forwarding for dashboard access.
  * Initiated fresh target Windows VM installation.
 
 
#### Phase 1: Environment Setup & Infrastructure
* Configured Oracle VirtualBox NAT Network (`ShubbyCyber-SOC-Lab-Network`) on subnet `10.0.2.0/24`.
* Imported and deployed Wazuh v4.14.7 OVA server instance (`10.0.2.3`).
* Bypassed guest OS rendering constraints by establishing host-to-guest NAT port forwarding (`127.0.0.1:8443` -> `10.0.2.3:443`), enabling dashboard access via host browser.

![VirtualBox Port Forwarding Setup](port-forwarding.png)

#### Phase 2: Telemetry Verification & Log Ingestion
* Connected `csec-target` Ubuntu endpoint (`10.0.2.15`) running Wazuh Agent v4.9.0.
* Verified active connection and tested log ingestion pipeline by firing a custom test payload (`sudo logger -t SOC_LAB_TEST "Wazuh SIEM ingestion test success"`).
* Confirmed real-time log parsing in Wazuh **Discover**, matching Rule ID `5402` and mapping to MITRE ATT&CK Technique **T1548.003** (*Privilege Escalation*).

![Wazuh SIEM Log Ingestion Test](wazuh-ingestion-test.jpg)

#### Current Status
* ⏳ Deploying Windows 10 target endpoint (`Win10-Target`) to configure Sysmon and Windows Event Log forwarding.
