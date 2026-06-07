Brute Force Attempt and Suspicious Command Execution on Domain Client VM

Incident 001: Brute Force Login Attempt on Domain Account

--

## 1. Summary

A series of failed login attempts were observed against a domain user account within the Windows Server 2022 Acrive Sirectory environment. The Activity was detected though Splunk, which triggered and alert based on multiple authentication failures within a short time period.

The investigation confirmed repeated failed login attemps from the same source followed by a successful login, indicating a potential brute force or password guessing attempt simulated within the lab environment.

--
