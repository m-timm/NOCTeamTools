iDRAC Service Module
Version 6.0.3.0
Release Notes

********************************************************************************
Supported operating systems
********************************************************************************

iDRAC Service Module 6.0.3.0 supports the following operating systems on PowerEdge 17G servers:
● Microsoft Windows 2022
● Microsoft Windows 2025
● Red Hat Enterprise Linux 9.4
● SUSE Linux Enterprise Server 15 SP6
● Ubuntu Server 24.04.2
● VMware vSphere ESXi 8.0 U3
● VMware vSphere ESXi 9.0

===============================================================================
New features
===============================================================================
The following features were added in this release:

* Operating system:
	The new supported operating systems are:
		● SUSE Linux Enterprise Server 15 SP6
		● Ubuntu Server 24.04.2
		● VMware vSphere ESXi 9.0

===============================================================================
Supported features
===============================================================================
The following are the features supported in iDRAC Service Module 6.0.3.0 for PowerEdge 17G servers:

* Operating System Information
* Lifecycle Controller Log Replication into Operating System
* Automatic System Recovery
* Prepare to Remove a NVMe PCIe SSD device
* Remote iDRAC Hard Reset (supported only on Windows and Red Hat Enterprise Linux Operating systems)
* In-Band support for iDRAC SNMP alerts
* Mapping iDRAC Lifecycle Logs to OMSA and OMSS SNMP Alerts
* Autoupdating iSM
* FullPowerCycle (supported only on Windows and Red Hat Enterprise Linux Operating systems)
* IPV6 Communication between iSM and iDRAC over OS to iDRAC Pass-through
* Isolation of OS to iDRAC Pass-through Independent feature
* SupportAssist on the box

===============================================================================
Resolved issues
===============================================================================
No issues are resolved in this release.

********************************************************************************
Supported platforms
********************************************************************************

Following are the list of platforms supported by iDRAC Service Module 6.0.3.0:
● PowerEdge R470
● PowerEdge R570
● PowerEdge R670
● PowerEdge R770
● PowerEdge R6715
● PowerEdge R6725
● PowerEdge R7715
● PowerEdge R7725
● PowerEdge M7725

================================================================================
--The User Notes, known issues and workarounds are mentioned in the respective 
  Microsoft Windows, Linux or VMware ESXi specific sections in this document.
--More details on limitations and supported operating systems can be located 
  in the iDRAC Service Module User's Guide.

--------------------------------------------------------------------------------
Known issues on Microsoft Windows operating systems
--------------------------------------------------------------------------------
● JIT-138538, JIT-146421
When the iDRAC Service Module (iSM) is communicating with iDRAC over IPv6 protocol on a Microsoft Windows operating system,
and if you perform an iDRAC Hard Reset operation or iDRAC firmware upgrade or downgrade, then the communication switches back to IPv4.
 
● JIT-219358 
When iSM operating system DUP installation is completed, the following informational message is logged in 
the Windows Event Viewer: Either the component that raises this event is not installed on your local computer 
or the installation is corrupted.You can install or repair the component on the local computer.

● JIT-245016  
When Microsoft Windows operating system is installed for non-English languages, the NIC information on the
iDRAC Host OS page may not be displayed correctly.

● JIT-260903
When iDRAC hard reset operation is performed on Microsoft Windows operating systems, the following message
is logged in the Event Viewer:
Faulting application
name: dsm_ism_srvmgr.exe and Faulting
module name: dcwipm.dll.

● JIT-323320
When iDRAC hard reset is disabled and you perform the iDRAC hard reset operation from the host OS using the Invoke-iDRACHardReset 
PowerShell command or through the iDRAC Hard Reset application, the following message is displayed:
Do you want to proceed with this operation? (Y/N):
If you select Y, then the iDRAC hard reset operation is completed successfully, else the application exits.

● JIT-329128
When iDRAC Service Module (iSM) is uninstalled from Microsoft Windows operating system Host OS, then you may observe that the following ISM0007
message is not displayed in the logs:
ISM0007: The iDRAC Service Module communication with iDRAC has ended.

================================================================================
Limitations on Microsoft Windows operating systems
================================================================================

● JIT-115250
When iSM is installed on Microsoft Windows operating systems using an operating system DUP, 
then the iSM Modify and Repair operation from the Add/Remove option displays the following error message: 
Original source path of the file is now found. You can extract the iSM DUP, double-click the MSI, and run repair.

● JIT-169898
If you have recently changed the folder name of the Lifecycle Controller log files in the Event Viewer, 
you cannot view Lifecycle Controller log files in the new folder in the Event Viewer. 
Microsoft recommends that you reboot the operating system to view the Lifecycle Controller log files under the new view name.

● Do not specify user profile folders such as a desktop folder
  (C:\Users\administrator\Desktop) as custom installation paths for installing 
  iDRAC Service Module. This is because services running on the system account  
  cannot access such folders.

● Enabling and disabling feature:
A feature that is enabled using the installer and disabled using
any interface other than the installer can only be enabled
using the same interface or the installer in GUI mode.

● JIT-169898
When you perform the modify operation for iSM components on Microsoft Windows operating system,
the operation may fail, and the following message is displayed:
iDRAC Service Module Object has timed out. Please check iDRAC Service Module services has gracefully started.
================================================================================
User notes for supported Linux operating systems 
================================================================================

On Linux operating systems, if the IPMI driver is not loaded, then reload the IPMI driver using the following commands:

	* To remove the IPMI driver, use the command: modprobe -r ipmi_si
          If the IPMI driver removal is unsuccessful, then stop all applications
	  that are using ipmi_si, such as iDRAC Service Module and retry the operation.
	* To install the IPMI driver, use the command: modprobe ipmi_si

--------------------------------------------------------------------------------
Known issues on Linux operating systems
-------------------------------------------------------------------------------- 

● JIT-102480 
When iDRAC Service Module is installed on Redhat Enterprise Linux operating system with 
SELinux enabled in either of Permissive or Enforcing modes, AVC denial logs (AVC denial is noticed with iptables)
are observed in /var/log/audit/audit.log  while the following features are enabled or disabled:
	1.	iDRAC Access via Host OS
	2.	Host SNMP Alerts
iDRAC Service Module does not support explicit SELinux policies. 
No action is expected from the user. There is no functionality impact to iSM features due to this.
Future releases of iSM shall address the AVC denials.

● JIT-280841
When the communication between iSM and iDRAC is established using IPv6 protocol, then iSM creates an invalid firewall rule.
This issue is observed when the IPv4 protocol is disabled or when the IPv4 address is removed from the OS to iDRAC Pass-through interface.
As a result, the operating system firewall service logs the following error messages: 
firewalld: ERROR: RUNNING_BUT_FAILED: Changing permanent configuration is not allowed.
firewalld: ERROR: ‘/usr/sbin/iptables-restore -w -n’ failed
firewalld: ERROR: COMMAND_FAILED: Direct: ‘/usr/sbin/iptables-restore -w -n’ failed

--------------------------------------------------------------------------------
Limitations on Linux operating systems
-------------------------------------------------------------------------------- 

● BITS088419 
Feature Lifecycle Log Replication on OS Log shows one-hour difference in 
the "EventTimeStamp" displayed in OS log, when daylight saving is applied. 

● JIT-305963
When iSM is running in Limited Functionality mode or iSM service is not running on Linux operating system, and then you try to re-enable the In-band SNMP Traps feature using the Enable-iDRACSNMPTrap.sh script, then the following ISM0057 message is not displayed: 
The iDRAC Service Module is running with Limited Functionality Mode, hence some features are unavailable. Possible reasons are: 
1) OS-to-BMC Passthrough setting in iDRAC is disabled
2) USBNIC interface on the host OS does not have a configured IP address.
This issue is observed if the In-band SNMP Traps feature is already enabled during the installation of iSM.

● JIT-336553
On Linux operating systems, the iDRAC network interface is configured with AutoConnect enabled by default. This setting ensures that the interface is automatically activated when the system boots or when the Network Manager service starts.
To configure the interface for IPv6-only operation, disable the IPv4 connection by running the following commands:

nmcli connection modify idrac ipv4.method disabled
nmcli connection down idrac && nmcli connection up idrac

===============================================================================
Known issues on VMware ESXi operating systems
===============================================================================

● JIT-278930, JIT-278933
In the ESXi 8.x operating system, when the network interface IP is changed or newly added while running dellism deamon, 
the latest information of network interfaces is not populated in the Network Interfaces page under System > Host OS page 
on the iDRAC user interface until the dellism deamon is restarted. 
Workaround: Run any of the following commands to see the reflected network interfaces information on the iDRAC: 
# Restart dellism deamon service on ESXi 8.x operating system by running the following command  /etc/init.d/dellism restart. 
# Disable and reenable the operating system Information (Network) feature under iDRAC Service Module Setup on the iDRAC. 

● JIT-306859
When the USBNIC IP address is updated on iDRAC UI, then the status of iDRAC Service Module is displayed as Not Running. 
This issue is observed on the VMware ESXi 8.x operating systems.
Workaround: After changing the USBNIC IP address on the iDRAC UI, ensure to change the IP address manually on the ESXi host USBNIC endpoint. 
To change the IP address manually on the USBNIC vmkernel interface, run the following command: dhclient-uw <vmkX>, where vmkX is the USBNIC traffic based vmkernel network interface.

● JIT-329094
After iSM is successfully installed on the VMware ESXi operating system and the iSM service is in running state, the following
failure logs are observed in the syslog in /var/log path:
dcismmut.DAT failed
dcismcomm64.ini failed
Workaround: There is no functional impact. No action is required.

--------------------------------------------------------------------------------
Limitations and workarounds on VMware ESXi operating systems
--------------------------------------------------------------------------------

● When Local Racadm set is disabled through iDRAC interfaces: 
  * iDRAC Service Module is unsuccessful in configuring the OS to iDRAC Pass-through in the USB NIC mode.
  * iDRAC Service Module functionality is restored when "Local racadm set" is enabled.
 
● EventID for Lifecycle Controller Logs replicated to OS log will e 0 for some of the past events.

● TrapID for In-band SNMP Traps will be 0 for some of the past traps

● JIT-160283
When the user interrupts any iSM command-line utility on VMware ESXi operating system,
user will not be able to remove the iSM VIB using the same terminal.
Workaround: Use another terminal to remove the iSM VIB.


===============================================================================
Known issues on all supported operating systems
===============================================================================

● JIT-159410
When the workload on the host increases due to intensive task requests by the processor, 
communication between iSM and iDRAC is temporarily interrupted with the following warning message
in the Lifecycle log file: "The iDRAC Service Module communication with iDRAC has ended."
Workaround: The connection automatically resumes and no action is required.

● JIT-161262
If a USB NIC is enabled after the system board is replaced without restoring the configuration or
after the iDRAC is reset to factory settings, you can observe the following ISM0003 event message
on operating system log files before starting the communication:
"The iDRAC Service Module is unable to discover iDRAC from the operating system of the server."
Workaround: No action is required.

● JIT-241957
When iSM is running in Limited Functionality mode, you can enable or disable the iSM features 
using the RACADM, WS-Man, or Redfish interfaces.However, the iSM features will not 
be functional in the host operating system.

● JIT-326906
When there are more than 50 past events logged in the Lifecycle Controller log before the iSM is installed or
the iSM service is started, only the top 50 past events are logged in the operating system log.

● JIT-328810
iDRAC GUI and RACADM interfaces do not block the toggle option for the WMI information feature.
This issue is observed on Red Hat Linux and VMware ESXi 8.x operating systems.

● JIT-328722
If iSM initiates communication using either the IPv4 or IPv6 protocol and later if any protocol is unavailable
on the USBNIC device, the iSM service will not resume communication with iDRAC unless you restart the iSM service.
This issue is observed on Red Hat Linux and Microsoft Windows operating systems.
Workaround: Restart iDRAC Service Module

● JIT-330105
The iSM status for Connection Status on Host OS is displayed as Not Running, when any of the following operations are
performed—iDRAC firmware is updated, iDRAC restarts on a system with the iDRAC Service Module (iSM) installed,
or the USBNIC IP address is updated on iDRAC UI.
Workaround: Restart iSM service on the host system and check the iSM status

● JIT-331717
When you select the iDRAC access via Host OS option on the Custom Setup page and click Next to enable it, the next page is
not displayed because this feature is not supported on iSM version 6.0.1.0.

● JIT-331639, JIT-331721
When iSM is installed on the host system and USBNIC is disabled there might be some delay in updating the iSM status for 
Connection Status on Host OS and Installed Version on Host OS. The updated status is displayed in the order of Running,
 Not Running, or Running in Limited Functionality mode.

● JIT-331609, JIT-331618, JIT-331634
When iSM is installed on the host system, then you may observe that the following messages are not displayed in the operating systems
logs and Lifecycle Controller log files:
ISM0004: The iDRAC Service Module has successfully started communication with iDRAC.
ISM0005: The iDRAC Service Module has successfully restarted communication with iDRAC.
ISM0057: The iDRAC Service Module is running with Limited Functionality Mode hence some features are unavailable. 
Possible reasons are: 1) OS-to-BMC Passthrough setting in iDRAC is disabled 2) USBNIC interface on the host OS does not have a configured IP address.

● JIT-332288
When you run the dcism-sync utility command to update iSM, you may observe the following message:
Unable to complete auto update of iDRAC Service Module. Retry the operation after sometime.
This issue is observed on Microsoft Windows operating systems and Linux operating systems.
 

--------------------------------------------------------------------------------
Limitations on all supported operating systems
--------------------------------------------------------------------------------

● JIT-158667, JIT-159019, JIT-158514, JIT-158740, JIT-294812, JIT-296875
When there is increased workload on the host due to intensive task request by the CPU, the communication between 
iDRAC Service Module and iDRAC will be interrupted for a moment and restored automatically. 
There is no action required by the user. 

● JIT-277931
While starting or restarting iSM, it may take up to 180 seconds for the iSM command-line utility to start 
functioning because the dependent libraries may take some time to initiate.

● JIT-344072:
When the OS to iDRAC pass-through status is changed using any supported iDRAC interfaces,
there may be a delay in logging the alert message associated with event ID iSM0007. 

********************************************************************************
Global Support
********************************************************************************
For information on technical support, contact your service provider.

****************************************************************************************************************************************************************

Copyright ©️ 2025 Dell Inc. or its subsidiaries. All rights reserved. Dell Technologies,
Dell, and other trademarks are trademarks of Dell Inc. or its subsidiaries. Other
trademarks may be trademarks of their respective owners.


2025 - 06		Rev. A00
