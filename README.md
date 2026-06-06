# Splunk-SOC-Homelab
SOC home lab using Splunk Enterprise, Sysmon, and Active Directory for log analysis, security monitoring, and incident investigation
<img width="948" height="371" alt="image" src="https://github.com/user-attachments/assets/99ae12e0-7677-4026-8b02-bf4858ae9bb6" />
The Objective of this lab is to gain hands-on experience with:

* Security event monitoring
* Log analysis and alert investigation
* Windows Active Directory environments
* Endpoint telemetry using Sysmon
* SIEM operations using Splunk Enterprise
* SOC alert triage and incident investigation workflows

This environment was built to simulate a small enterprise network and provide practical exposure to the type of telementry and investigations performed by a Tier 1 SOC Analyst.
--

## Lab Architecture

The lab consists of:

### Infrastructure
- **Windows Server 2022** - Domain Controller
- **Windows 11 Enterprise** - Domain-joined endpoint
- **Splunk Enterprise** - Central SIEM platform
- **Sysmon** - Endpoint telementry and logging
- **Splunk Universal Forwarders** - Log forwarding from endpoints

### Environment Design
The Windows 11 enterprise endpoint is joined to an Active Directory domain hosted windows Server 2022 to simulate a realistic enterprise environment.

Security logs and endpoint telemetry are centrally collected into Splunk using Universal Forwarders enabling monitoring investigations and authentication activity, endpoint behaviour, and suspicious events.

--

## Architecture Design
<img width="2534" height="1316" alt="image" src="https://github.com/user-attachments/assets/4bd54de6-2148-4afc-8733-59e606889905" />


