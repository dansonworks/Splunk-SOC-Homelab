Brute Force Attempt and Suspicious Command Execution on Domain Client VM

Incident 001: Brute Force Login Attempt on Domain Account

--

## 📌 1. Summary

A series of failed login attempts were observed against a domain user account within the Windows Server 2022 Acrive Sirectory environment. The Activity was detected though Splunk, which triggered and alert based on multiple authentication failures within a short time period.

The investigation confirmed repeated failed login attemps from the same source followed by a successful login, indicating a potential brute force or password guessing attempt simulated within the lab environment.

--

## ⏱️ 2. Timeline of Events
- 1:45:17.PM - Multiple failed login attemps detected for domain user: "Administrator"
- 13:45:19 PM - Authentication failure continue from same source machine
- 13:47:00 PM - Splunk alert triggered due to threadhold of failed logins
- 13:48:00 PM - Investigation initiated in Splunk
- 13:50:00 PM - Successful login observed for the same user account
- 13:51:00 PM - Event correlation performed between failed and successful logins

---

## 🔍 3. Investigation Steps
The following steps were taken to investigate the alert:

- Queried Splunk for Windows Event ID `4625` (failed login attempts)
- Filtered logs by username: `testuser`
- Identified repeated authentication failures from a single source IP / host
- Queried Event ID `4624` (successful login events)
- Confirmed successful login occurred shortly after repeated failures
- Reviewed time correlation between failed and successful authentication attempts
- Checked whether login source was expected within the lab environment

---

## 🖥️ 4. Evidence Collected

The following evidence was collected during the investigation:

- Splunk alert showing spike in failed login attempts
- Windows Security logs (Event ID 4625 – Failed Logons)
- Windows Security logs (Event ID 4624 – Successful Logon)
- Authentication timeline showing sequence of failed → successful login events

### Screenshots:






