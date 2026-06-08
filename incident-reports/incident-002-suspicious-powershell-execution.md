Suspicious Powershell Execution

Incident: 002-suspicious Powershell Execution

--

## 📌 1. Summary

Suspicious PowerShell activity was detected on the Windows client machine joined to the domain environment. The activity was identified through log analysis in Splunk after PowerShell commands were executed on the endpoint.

The investigation focused on determining what commands were run, which user executed them, and whether the behaviour indicated malicious activity.

--

## ⏱️ 2. Timeline of Events
- 13:48:14 PM — User logged into domain client machine successfully.
- 13:50:00 PM — PowerShell process execution detected on endpoint.
- 13:50:00 PM — Splunk alert triggered for suspicious PowerShell activity.
- 14:00:00 PM — Analyst initiated investigation via Splunk search.
- 14:25:00 PM — Investigation completed and results documented.


