Brute Force Attempt and Suspicious Command Execution on Domain Client VM

Incident 001: Brute Force Login Attempt on Domain Account

--

## 📌 1. Summary

A series of failed login attempts were observed against a domain user account within the Windows Server 2022 Acrive Sirectory environment. The Activity was detected though Splunk, which triggered and alert based on multiple authentication failures within a short time period.

The investigation confirmed repeated failed login attemps from the same source followed by a successful login, indicating a potential brute force or password guessing attempt simulated within the lab environment.

--

## ⏱️ 2. Timeline of Events
- 13:45:17.PM - Multiple failed login attemps detected for domain user: "Administrator"
- 13:45:19 PM - Authentication failure continue from same source machine
- 13:47:00 PM - Splunk alert triggered due to threadhold of failed logins
- 13:48:00 PM - Investigation initiated in Splunk
- 13:48:14 PM - Successful login observed for the same user account
- 13:51:00 PM - Event correlation performed between failed and successful logins

---

## 🔍 3. Investigation Steps
The following steps were taken to investigate the alert:

- Queried Splunk for Windows Event ID `4625` (failed login attempts)
- Filtered logs by username: `WIN-T6O06KOGOUU`
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
<img width="1292" height="944" alt="image" src="https://github.com/user-attachments/assets/ddf8c8ae-3adb-4afb-8d3f-ba6eb097e561" />
Figure 1: Splunk alert configuration and triggered detection for failed login attempts (EventCode 4625).

Splunk alert configured to detect repeated failed authentication attempts using Windows EventCode 4625. The detection rule evaluates authentication logs within a defined time window and triggers when the number of failed login attempts exceeds the configured threshold.

<img width="1860" height="318" alt="image" src="https://github.com/user-attachments/assets/957b94f2-ecbf-4a81-8c79-367c3a068b55" />
Figure 2: Windows Security Event Log entry for EventCode 4625 (failed authentication attempt).

Windows Security Event Log showing EventCode 4625, indicating a failed login attempt on the system. The event includes details such as the account name, timestamp, host information, and source network address.


<img width="1922" height="318" alt="image" src="https://github.com/user-attachments/assets/1413f618-c029-4966-9d91-b17f42bce563" />
Figure 3: Windows Security Event Log entry for EventCode 4624 (successful authentication event).

Windows Security Event Log showing EventCode 4624, indicating a successful login to the system. The event contains details including the account name, timestamp, system name, and source network address.

<img width="2428" height="1006" alt="image" src="https://github.com/user-attachments/assets/e8e33696-8a96-4369-b2bc-7225d2ae0c13" />
Figure 4: Splunk search results showing filtered EventCode 4625 failed authentication events.

Splunk search query filtering EventCode 4625 events on the target Windows host within a defined time range. The results display multiple failed login attempts associated with the same system and user account.

The query was refined using host filtering and time range selection to isolate authentication failures during the investigation window.

<img width="1930" height="932" alt="image" src="https://github.com/user-attachments/assets/c0a020b5-e839-42f8-8be4-35319815a6fa" />
Figure 5: Splunk timechart showing EventCode 4624 (successful logins) and EventCode 4625 (failed logins) over time.

Splunk timechart visualisation showing authentication activity on the target Windows host. The chart plots both successful logins (EventCode 4624) and failed login attempts (EventCode 4625) over a selected time range.

Data was filtered to the specific host involved in the investigation, with a one-minute interval applied to display event distribution over time.

The visualisation displays variations in authentication events across the selected period.


###Extra###

<img width="1742" height="710" alt="Screenshot 2026-06-07 135621" src="https://github.com/user-attachments/assets/3adab1af-08e0-415c-b49a-3f1bf094e1a0" />
Figure 9: Windows Security Event Log showing failed interactive logon attempt (EventCode 4625).

Windows Security Event 4625 showing a failed interactive logon attempt for the Administrator account. The event indicates the failure was due to an incorrect password and includes details such as logon type, process name (svchost.exe), and source address (127.0.0.1).


Note: In this lab environment, the domain user account was intentionally named WIN-T6O06KOGOUU to match the host machine for simplicity during setup. In production environments, user and host naming conventions are typically distinct.





