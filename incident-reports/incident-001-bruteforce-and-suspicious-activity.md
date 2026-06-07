Brute Force Attempt and Suspicious Command Execution on Domain Client VM

Incident 001: Brute Force Login Attempt on Domain Account

--

## 📌 1. Summary

A series of failed login attempts were observed against a domain user account within the Windows Server 2022 Acrive Sirectory environment. The Activity was detected though Splunk, which triggered and alert based on multiple authentication failures within a short time period.

The investigation confirmed repeated failed login attemps from the same source followed by a successful login, indicating a potential brute force or password guessing attempt simulated within the lab environment.

--

## ⏱️ 2. Timeline of Events
- 1:45:17.PM - Multiple failed login attemps detected for domain user: "Administrator"
- 1:45:19 PM - Authentication failure continue from same source machine
- 1:47:00 PM - Splunk alert triggered due to threadhold of failed logins
- 1:48:00 PM - Investigation initiated in Splunk
- 1:50:00 PM - Successful login observed for the same user account

---

- 
