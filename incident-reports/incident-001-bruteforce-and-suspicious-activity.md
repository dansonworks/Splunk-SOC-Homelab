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
<img width="1292" height="944" alt="image" src="https://github.com/user-attachments/assets/ddf8c8ae-3adb-4afb-8d3f-ba6eb097e561" />
Summary of the Brute‑Force Detection Alert

This alert is designed to detect potential brute‑force login attempts on a Windows system by monitoring repeated failed authentication events. It focuses specifically on EventCode 4625, which is generated whenever a user enters an incorrect password.

The alert works by analysing authentication logs over a defined time window and identifying any account that has more than three failed login attempts. If this threshold is exceeded, the alert triggers and notifies the security team so they can investigate possible malicious activity or user error.

<img width="1860" height="318" alt="image" src="https://github.com/user-attachments/assets/957b94f2-ecbf-4a81-8c79-367c3a068b55" />
Failed Login

This screenshot shows a Windows Security Log entry for EventCode 4625, which records a failed login attempt. The event includes details such as the system name, the account involved, the timestamp, and the source network address (in this case, 127.0.0.1, meaning the attempt originated locally). EventCode 4625 is generated whenever a user enters an incorrect password or when authentication fails for another reason, making it a key indicator of suspicious activity. These failed login events are essential for detecting brute‑force attempts or repeated unauthorized access, and they form the core data source for my Splunk brute‑force detection alert, which monitors repeated failures and triggers when a user exceeds a defined threshold.

<img width="1922" height="318" alt="image" src="https://github.com/user-attachments/assets/1413f618-c029-4966-9d91-b17f42bce563" />
Successful Login

This log entry shows a Windows Security Event 4624, which indicates a successful login. In the context of my brute‑force detection scenario, this event appears immediately after multiple failed login attempts (EventCode 4625). The attacker repeatedly tried incorrect passwords, triggering my Splunk brute‑force alert, and eventually managed to authenticate successfully. The log records details such as the system name, timestamp, and the source network address (127.0.0.1), confirming that the login attempt originated locally. This successful authentication event demonstrates the moment the brute‑force attack succeeded, highlighting why continuous monitoring of both failed and successful logins is critical for detecting compromised accounts in a SOC environment.

<img width="2428" height="1006" alt="image" src="https://github.com/user-attachments/assets/e8e33696-8a96-4369-b2bc-7225d2ae0c13" />
Splunk Search Query itself

This screenshot shows the Splunk search I performed to filter and analyse all failed login attempts (EventCode 4625) on the target Windows machine. I refined the search by specifying the host name and adjusting the time range to focus only on the period during which the brute‑force activity occurred. The query returned 26 failed login events, confirming repeated incorrect password attempts against the same system. By narrowing the search to a specific host and timeframe, I was able to clearly isolate the brute‑force pattern and validate that the attacker was repeatedly attempting to authenticate. This filtered view helped me correlate the failed attempts with the later successful login event, demonstrating how Splunk can be used to trace the full sequence of an attack from initial failures to eventual compromise.

<img width="1930" height="932" alt="image" src="https://github.com/user-attachments/assets/c0a020b5-e839-42f8-8be4-35319815a6fa" />
Timeline View

This screenshot shows a Splunk timechart visualisation I created to analyse authentication activity on the target Windows host by plotting both successful logins (EventCode 4624) and failed logins (EventCode 4625) over time. I filtered the data to the specific machine involved in the brute‑force attack and used a one‑minute time span to clearly show spikes in login behaviour. The chart displays over a thousand events across the selected timeframe, with noticeable peaks that correspond to periods of repeated failed login attempts followed by successful authentication. This visualisation helped me understand the attack pattern more clearly, showing when the brute‑force attempts intensified and when the attacker finally gained access. By comparing both event types on the same graph, I could easily correlate the failed attempts with the eventual successful login, demonstrating how Splunk can be used to visually track and confirm the progression of an account compromise.






