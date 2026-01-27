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
- Kali Linux: Simulated adversary behavior by initiating remote access attempts to generate realistic authentication and security telemetry.
- Splunk Server: Collected, indexed, and analyzed Windows event logs to identify remote logon activity and generate security alerts.
- Sysmon: Enhanced Windows logging by capturing detailed process, network, and authentication activity to improve visibility and detection accuracy in Splunk.

## Diagram
<img width="507" height="510" alt="image" src="https://github.com/user-attachments/assets/478ad988-4586-4128-ac1e-33311ef70643" />

## Lab Set Up
<img width="757" height="417" alt="image" src="https://github.com/user-attachments/assets/7382f393-b726-4ab0-9540-f2d945e403ea" />         <img width="701" height="436" alt="image" src="https://github.com/user-attachments/assets/513ab3c5-cb4d-494b-8349-1dbb8ce0e8e2" />
 

Windows 11 Server DC



*Ref 1: Network Diagram*
