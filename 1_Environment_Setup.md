##### Initial Concept
1. We will create a Windows 11 client and Ubuntu Server to facilitate the network traffic and host environment we need to conduct our testing.
##### Virtualization and Setup
1. Using VMware, we downloaded Windows 11 Eval version from Microsoft and Ubuntu Server 22.04.1. 
2. For the Windows 11, we need to make sure to disable Hypervisor and disable virtual security settings. Check using `msconfig`. See below:
![](https://github.com/tuckws/Lab_SOC_Automation_YARA/blob/main/images/1_TroubleshootingVmwareWin11.png?raw=true)
3. For VM hardware settings, we left everything default. NAT networking. Approximately 20GB hard drive. 2 CPU Cores. 2GB Ram for Ubuntu Server and 8GB for Windows 11. I have 64GB RAM on my system to allocated. 
4. Review the NAT Settings within VMware. Will be needed for Ubuntu Server configuration. 
![](https://github.com/tuckws/Lab_SOC_Automation_YARA/blob/main/images/2_VerifyNATSettingsForServer.png?raw=true)
X
