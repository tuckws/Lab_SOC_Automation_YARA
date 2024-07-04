## Lab_SOC_Automation_YARA

#### Purpose
The purpose of this lab is to develop knowledge and experience in the application of EDR, Threat Hunting, and SIEM tools. We will use YARA and LimaCharlie to monitor and triage a lab environement with Windows 11 and Ubuntu Server. Test, break, have fun.
#### Skills Learned
- EDR implementation.
- Logging collection and management.
- Threat intelligence and analysis.
- Multi-platform functionality with various tools. SIEM-like integration. 
#### Tools Used
- LimaCharlie.
- YARA.
- Sysmon.
- Ubuntu Server.
- Powershell.
- VMware.
#### Notes
- Subnet IP: 192.168.220.0/24
- Gateway IP: 192.168.220.2
- ubuntu-server: 192.168.220.131/24
#### Rules
```event: SENSITIVE_PROCESS_ACCESS
op: ends with
path: event/*/TARGET/FILE_PATH
value: lsass.exe```
