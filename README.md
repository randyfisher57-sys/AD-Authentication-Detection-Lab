# AD-Authentication-Detection-Lab

## Objective


This project simulates remote access activity from a Windows 11 server to a Windows 10 endpoint and captures the resulting authentication and logon telemetry. Windows security events are ingested into Splunk, analyzed to validate remote sessions, and used to create a detection alert that identifies potentially unauthorized or suspicious remote access activity.

### Skills Learned


- Configured a multi-VM lab environment (Windows 10, Windows 11 Server, Splunk) - Ingested Windows event logs into Splunk
- Identified and analyzed Windows authentication and remote logon telemetry
- Wrote and refined SPL queries to filter and correlate security events
- Built real-time alerts in Splunk based on authentication telemetry

### Tools Used


- Windows 11 Server: Acted as the Active Directory domain controller, authenticating users and generating security event logs related to domain logons and remote access activity.
- Windows 10 PC: Served as the endpoint target for remote access, producing authentication and logon telemetry used to validate RDP sessions and user activity.
- Splunk Server: Collected, indexed, and analyzed Windows event logs to identify remote logon activity and generate security alerts.
- Sysmon: Enhanced Windows logging by capturing detailed process, network, and authentication activity to improve visibility and detection accuracy in Splunk.

## Diagram
<img width="507" height="410" alt="image" src="https://github.com/user-attachments/assets/478ad988-4586-4128-ac1e-33311ef70643" />

## Lab Set Up

<div style="display: flex; gap: 10px;">
 
 <img width="657" height="417" alt="image" src="https://github.com/user-attachments/assets/7382f393-b726-4ab0-9540-f2d945e403ea" />       
 
 Windows 11 Server DC
 
 <img width="601" height="436" alt="image" src="https://github.com/user-attachments/assets/f50c6dc2-2dbf-4345-bdd4-ba054b397b59" />

</div>

Windows 10 PC Join Domain

<img width="682" height="431" alt="image" src="https://github.com/user-attachments/assets/2fca88df-969d-47cb-bd0d-fa4d134c3916" />

Splunk Installed on Ubuntu


<img width="619" height="443" alt="image" src="https://github.com/user-attachments/assets/78d20cda-117e-4207-aa31-c9f06d16c047" />

Kali Linux Install 

## Remote Session Logs

<img width="1904" height="914" alt="splunk_rule_p1" src="https://github.com/user-attachments/assets/f7d20a71-f894-4e0c-96d4-258ffe8980fd" />

I remotely logged into the Windows 10 machine from the Windows 11 Server and verified the connection. The Splunk agent installed on the Windows 10 system successfully forwarded logs to the Splunk server, confirming the remote session was established successfully.

## Detection alert creation 

<img width="1911" height="913" alt="splunk_alert_p2" src="https://github.com/user-attachments/assets/13ea55c1-b1cd-4399-97fa-8aa7f2d2b429" />

This Splunk detection rule is a scheduled alert that monitors Windows Security logs (Event ID 4624) for successful logins with Logon Type 10 (Remote Interactive/RDP) and Logon Type 7 (workstation unlock) in the specified index. It runs on a cron schedule, looks back over the last 60 minutes, and triggers a medium-severity alert whenever one or more matching events are found. The results are grouped by time, computer name, source network address, and user to show who logged in, from where, and to which system.

## Triggered Alerts test 

<img width="1883" height="817" alt="Screenshot 2026-01-23 124947" src="https://github.com/user-attachments/assets/28b097de-b01a-4106-bd50-a8b4996642e3" />

The alert was successfully triggered after remotely connecting to the Windows 10 machine from the Windows 11 Server, confirming that the detection rule properly identified the RDP login activity.

## Summary 

This lab simulated real-world remote access activity within an Active Directory environment to better understand how authentication and RDP logon events are generated, collected, and detected. By configuring a multi-VM setup (Windows 11 Server as a domain controller, Windows 10 endpoint, Kali Linux attacker machine, and a Splunk server), I was able to generate authentication telemetry, ingest Windows Security logs into Splunk, and analyze Event ID 4624 with Logon Types 7 and 10 to validate remote sessions.

Through this project, I strengthened my ability to interpret Windows authentication logs, write and refine SPL queries, and build scheduled detection alerts in Splunk. Most importantly, I learned how to translate raw security telemetry into actionable detections, validate alerts through controlled testing, and understand how legitimate versus potentially suspicious remote access activity appears in log data. This lab reinforced core SOC skills including log analysis, alert creation, and authentication-based threat detection.
