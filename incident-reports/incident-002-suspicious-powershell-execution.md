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

---

## 🖥️ 4. Evidence Collected

The following evidence was collected during the investigation:

Splunk Alert Output

The alert indicated unusual PowerShell execution on the client machine under a domain user session.

- Log Sources Reviewed
- Windows Security Event Logs
- PowerShell Operational Logs (if enabled)
- Process Execution Logs (Sysmon if configured)
- Splunk Alert Event Data

### Screenshots:
<img width="1500" height="760" alt="image" src="https://github.com/user-attachments/assets/cab7e043-77a0-4344-8cde-9a869049cada" />
Figure 1: Splunk alert list showing multiple triggered PowerShell activity detections

Splunk scheduled correlation search triggered multiple alerts for PowerShell process creation on the monitored host. Alerts were generated at regular intervals based on detection logic for suspicious PowerShell execution activity.


<img width="1500" height="778" alt="image" src="https://github.com/user-attachments/assets/921b690b-bc32-4473-8f61-dc641ff7d0af" />
Figure 2: Sysmon EventCode 1 showing PowerShell process creation and execution details.

Splunk search results displaying Sysmon EventCode 1 process creation events where the process name is powershell.exe. The logs show multiple PowerShell executions on the monitored host, including full command line details.


<img width="1500" height="788" alt="image" src="https://github.com/user-attachments/assets/1e2bc1d5-25c2-40ae-9716-35420c893783" />
Figure 3: Sysmon event showing PowerShell execution details including command line and process metadata.*

Sysmon EventCode 1 shows a PowerShell process execution on the monitored host. The event contains the full command line, along with associated metadata including process ID, file path, user context, parent process, and hash values.

---

## Analysis

PowerShell is a legitimate administrative tool in Windows environments; however, it is frequently used by attackers for malicious purposes such as reconnaissance, persistence, and execution of encoded commands.

The Splunk alert was triggered due to detection of PowerShell execution outside of normal baseline activity.

Upon investigation, the activity was confirmed to originate from a valid domain user session in a controlled lab environment. The commands executed were part of a simulated test scenario and did not indicate real compromise.

No evidence of privilege escalation, lateral movement, or external communication was observed.

## Conclusion

The alert for suspicious PowerShell activity was successfully investigated and determined to be part of a simulated scenario in a controlled SOC home lab environment.

## Key findings:

- Splunk alert correctly detected PowerShell execution
- Activity was linked to a valid user session
- No indicators of compromise beyond simulated behaviour








