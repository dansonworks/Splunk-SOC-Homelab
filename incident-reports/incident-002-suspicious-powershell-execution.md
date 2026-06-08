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

---

## 🔍 3. Investigation Steps
The investigation began after the Splunk alert flagged PowerShell execution activity on the endpoint.
The following steps were taken to investigate the alert:

- Searched for PowerShell-related events in Splunk.
- Reviewed process execution logs to identify the parent process and execution context.
- Confirmed which user account executed the commands.
- Checked whether PowerShell activity was expected or potentially suspicious.
- Reviewed nearby authentication logs to determine whether account compromise indicators were present.



