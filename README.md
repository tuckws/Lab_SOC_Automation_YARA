## Lab_SOC_Automation_YARA

#### Purpose
The purpose of this lab is to develop knowledge and experience in the application of EDR, Threat Hunting, and SIEM tools. We will use YARA and LimaCharlie to monitor and triage a lab environement with Windows 11 and Ubuntu Server. Test, break, have fun.
#### Skills Learned
- EDR implementation.
- Telemetry generation.
- Logging collection and management.
- Threat intelligence and analysis.
- Rule-Tuning, false positives. 
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
```
#Detection LSASS Access:
event: SENSITIVE_PROCESS_ACCESS
op: ends with
path: event/*/TARGET/FILE_PATH
value: lsass.exe
#Response:
- action: report
  name: LSASS access
```
```
#Detection Shadow Volume Deletion:
event: NEW_PROCESS
op: and
rules:
  - op: is
    path: event/FILE_PATH
    value: C:\Windows\system32\vssadmin.exe
  - op: is
    path: event/COMMAND_LINE
    value: '"C:\Windows\system32\vssadmin.exe" delete shadows /all'
  - op: is
    path: routing/hostname
    value: windev2404eval.localdomain
#Response:
- action: report
  name: vss_deletion_kill_it
- action: task
  command:
    - deny_tree
    - <<routing/parent>>
```
```
#Detection svchost.exe Suspicious Processes
event: NEW_PROCESS
  - op: ends with
    path: event/FILE_PATH
    value: \svchost.exe
#False Positive Rule
op: and
rules:
- op: is
    path: cat
    value: Suspicious svchost execution
- op: is
  path: detect/event/FILE_PATH
  value: C:\Windows\system32\svchost.exe
- op: contains
  path: detect/event/COMMAND_LINE
  value: -k
#Response:
- action: report
  name: Suspicious svchost execution
```
