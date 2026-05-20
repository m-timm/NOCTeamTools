iDRAC Service Module
Version 5.3.0.0
Release Notes

********************************************************************************
What's new in this release
********************************************************************************
Supported operating systems

iDRAC Service Module 5.3.0.0 supports the following operating systems on  PowerEdge 14G, PowerEdge 15G, and PowerEdge 16G servers:
● Microsoft Windows 2022
● Microsoft Windows 2019
● Red Hat Enterprise Linux 9.3
● Red Hat Enterprise Linux 8.9
● SUSE Linux Enterprise Server 15 SP5
● Ubuntu Server 22.04.2
● VMware vSphere ESXi 8.0 U2
● VMware vSphere ESXi 7.0 U3

iDRAC Service Module 5.3.0.0 supports the following Real Time Operating System (RTOS) on PowerEdge XR12, PowerEdge
XR11, PowerEdge 750, PowerEdge R650, and PowerEdge XR5610 servers:
● Red Hat Enterprise Linux 9.3
● Red Hat Enterprise Linux 8.9
● SUSE Linux Enterprise Server 15 SP5

iDRAC Service Module 5.3.0.0 supports the following client operating systems on Precision R7960 and Precision 7920:
● Microsoft Windows 11 21H2/22H2
● Microsoft Windows 10 22H2
● Red Hat Enterprise Linux 8.6
● Ubuntu Desktop 22.04 LTS

 
===============================================================================
New and enhanced features
===============================================================================
The following are the new and enhanced features of iDRAC Service Module 5.3.0.0:

* Metric Injection (Host OS Telemetry) support on VMware ESXi 8.0 U2 and Microsoft Windows operating system:
	Enhancement to support the Metric Injection(Host OS Telemetry) feature on the VMware ESXi 8.0 U2 Hypervisor.
	Enhancement to support the Metric Injection (Host OS Telemetry) feature with physical drives, logical drives, 
	and Logical Processor Utilization on the Microsoft Windows operating system. 

* Software RAID configuration:
	Software RAID configuration support to assign and unassign the global hot spare and dedicated hot spare.

* Operating system:
	The new supported operating systems are:
		● Red Hat Enterprise Linux 8.9
		● Red Hat Enterprise Linux 9.3
		● VMware vSphere ESXi 8.0 U2



===============================================================================
Resolved issues
===============================================================================

The following are the resolved issues in iDRAC Service Module 5.3.0.0:

●  JIT-269167
The ISM0058 message is logged in the OS log data four minutes after the following: 
When iSM 5.1.0.0 is installed with iDRAC firmware 7.00.00.00 or later versions, all 
features are enabled and prerequisites are met, the Redfish feature is disabled, and then iSM is restarted.

●  JIT-267807 & JIT-269301
When Redfish is Enabled on iDRAC, then you may have to wait up to 120 seconds
to perform any operations that are related to the Metric Injection (Host OS
Telemetry) feature on iDRAC Service Module.

●  JIT-265249
When you assign or unassign a dedicated hot spare, the software RAID alert
message displays incorrect disk ID on Microsoft Windows operating system log
and Lifecycle Controller log.

********************************************************************************
Supported platforms
********************************************************************************

For information about the supported platforms, see the Dell iDRAC Service Module User's 
Guide available at https://www.dell.com/idracmanuals.

================================================================================
--The User Notes, known issues and workarounds are mentioned in the respective 
  Microsoft Windows, Linux or VMware ESXi specific sections in this document.
--More details on limitations and supported operating systems can be located 
  in the iDRAC Service Module User Guide.

--------------------------------------------------------------------------------
Known issues on Microsoft Windows operating systems
--------------------------------------------------------------------------------

● JIT-87075 
While uninstalling "iDRAC Service Module" a popup is displayed if the Firefox browser is opened.
The popup prompts that Firefox browser needs to be closed before continuing the uninstallation.
Close the Firefox browser and click the "Retry" option to continue
the uninstallation.

● JIT-157981 
When Windows Management Instrumentation MOF query is ran on DCIM_View classes using iDRAC Service Module, 
no data will be populated. 

● JIT-138538 & JIT- 146421
When iDRAC Service Module is communicating with IDRAC over IPv6 protocol on a Microsoft Windows operating system
if the user performs iDRAC Hard Reset operation or iDRAC firmware upgrade or downgrade, then the communication
with switch back to IPv4.

● JIT-214241 & JIT-219472
When the iSM command-line utility dcismcfg.exe is used to list the physical drives on Dell PowerEdge 14G servers
with Software RAID configuration, the BayID property for SATA (HDD or SSD) drive is displayed incorrectly.
 
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

● JIT-269856
When Check Consistency task is cancelled on multiple virtual disks simultaneously,then the Microsoft Windows 
operating system does not respond and might reboot. However, after reboot the Check Consistency task is in active state.
NOTE: This issue is observed on PowerEdge 14G servers with software RAID configuration.

● JIT-269857
When you perform the Check Consistency task on a virtual disk with an invalid ID, the following 
error message is displayed: The operation is unsuccessful on Disk [X] because the device is busy, Retry the 
operation after sometime.

● JIT-277863
When Microsoft Windows operating system is installed, and if the server has more than 50 physical drives, 
then the Server storage (S2D) correlation feature monitors alerts only for the first 50 physical drives. 

================================================================================
Limitations on Microsoft Windows operating systems
================================================================================

● JIT-262181
When a virtual disk of type Volume with a virtual disk of size less than 1024 GB is created, then the size of the created
virtual disk may be 1 GB less than the requested size.

● JIT-115250
When iDRAC Service Module is installed on Microsoft Windows operating systems using 
OS DUP, then the iSM Modify and Repair operation from the Add/Remove programs will throw
'original source path of the file is not found' error. User can extract the iSM DUP 
and double click the MSI and run repair.

● JIT-169898
Lifecycle Controller logs are not seen in the new folder in the
Event Viewer, if you have recently changed the folder name of the
Lifecycle Controller logs in the Event Viewer. Microsoft recommends that 
you reboot the operating system to be able to view the Lifecycle Controller
logs under the new view name.

● JIT-265249
When you assign or unassign a dedicated hot spare drive to a physical disk and 
another physical disk that is present in the server with same Slot number and different Bay ID,
then the software RAID alert message displays incorrect Bay ID in Windows Event Viewer.

● Communication between iSM and iDRAC over IPv6 will work only on iDRAC firmware 2.70.70.70 or later.

● Do not specify user profile folders such as a desktop folder
  (C:\Users\administrator\Desktop) as custom installation paths for installing 
  iDRAC Service Module. This is because services running on the system account  
  cannot access such folders.

● Enabling and disabling feature:
A feature that is enabled using the installer and disabled using
any interface other than the installer can only be enabled
using the same interface or the installer in GUI mode.

● IPv6 support on Windows operating systems are not available for the following features: 
 	* iSM Auto Update 
	* Inband iDRAC Access 
	* SNMP Get via Host OS	

================================================================================
User notes for supported Linux operating systems 
================================================================================

On Linux operating systems, if the IPMI driver is not loaded, then reload the IPMI driver using the following commands:

	* To remove the IPMI driver, use the command: modprobe -r ipmi_si
          If the IPMI driver removal is unsuccessful, then stop all applications
	  that are using ipmi_si, such as iDRAC Service Module and OpenManage Server
	  Administrator and retry the operation.
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

   
● JIT-124514
When invoking "iDRAC GUI Launcher" for the first time either using iDRACLauncher.sh 
or using the program menu shortcut, the following message will be seen in operating system logs.
"localhost dbus-daemon[2369]: [system] Activating via systemd: service name='net.reactivated.Fprint'unit='fprintd.service'
requested by ':1.18176' (uid=0 pid=126684 comm="sudo -l /opt/dell/srvadmin/iSM/bin/InvokeiDRACLau"label="unconfined_u:unconfined_r:unconfined_t:s0-s0:c0.c1023")"
There is no functional impact. No action is required by the user.
 
--------------------------------------------------------------------------------
Limitations on Linux operating systems
-------------------------------------------------------------------------------- 

● JIT-132983
When iDRAC Service Module is communicating with iDRAC using IPv6 protocol,
enabling the feature "InBand iDRAC Access" indicates a successful message.
But this feature is unavailable over IPv6 protocol. No action is required 
by the user.

● BITS088419 
Feature Lifecycle Log Replication on OS Log shows one-hour difference in 
the "EventTimeStamp" displayed in OS log, when daylight saving is applied. 

● JIT-227317
When iSM container is deployed in the host operating system, the DHCP and 
DHCP Server details are incorrect in the Network Interfaces page under 
System > Host OS on iDRAC. The DHCP and DHCP server details in the Host OS
Network Interfaces are incorrectly populated for Redfish, WS-Man and Racadm 
command response as well.

● JIT-227625
When iSM container is running, installation of iSM on the host
operating system can cause conflict.

● IPv6 support on Linux operating systems are not available for the following features:
	- iSM Auto Update
	- Inband iDRAC Access
	- SNMP Get via Host-OS

===============================================================================
Known issues on VMware ESXi operating systems
===============================================================================

● After performing an iDRAC Hard Reset operation on certain VMware ESXi operating 
  systems, the IPMI driver (ipmi_si_drv on Esxi 6.5U2 and ipmi on ESXi 6.7U1 operating system) 
  may become unresponsive because of an existing issue in the IPMI driver. If the IPMI driver 
  becomes unresponsive, reload the IPMI driver (ipmi_si_drv on Esxi 6.5U2 and ipmi on ESXi 6.7U1 operating system). 
  
  The issue is observed on all iDRAC Service Module v2.3 and later supported ESXi versions.
  Steps to reload the ipmi_si_drv.
  
  * esxcli system wbem set -e 0 
  * esxcfg-module -u ipmi_si_drv/ipmi  => unload ipmi_si_drv/ipmi
  * esxcfg-module  ipmi_si_drv/ipmi    => load ipmi_si_drv/ipmi
  * esxcli system wbem set -e 1 
  Alternatively, the administrator can also restart the Host OS to resolve 
  the issue.

● JIT-172915 
On VMware ESXi operating system (OS), iDRAC Service Module (iSM) communication with iDRAC might restart.
No action is required by the user as the communication is restored automatically within 1 to 2 minutes.

● JIT-188568
The iSM feature “Invoke-FullPowerCycle” is not supported when the “SMM Security Mitigation” 
is enabled from BIOS on VMware ESXi 7.x operating systems.

● JIT-278930 & JIT-278933
In ESXi 8.x operating system, when the network interface IP is changed or newly added while running dellism 
deamon, the latest information of network interfaces is not populated in the Network Interfaces page 
under System > Host OS page on iDRAC GUI until the dellism deamon is restarted.
Workaround: Run any of the following commands to see the reflected Network Interfaces information on iDRAC:
-Restart dellism deamon service on ESXi8.x OS by running the following command
/etc/init.d/dellism restart
-Disable and reenable the OS Information (Network) feature under iDRAC Service Module Setup on iDRAC.
 
--------------------------------------------------------------------------------
Limitations and workarounds on VMware ESXi operating systems
--------------------------------------------------------------------------------

● Upgrading an earlier version of ESXi to ESXi 8.x is unsuccessful with iSM VIB installed.
Workaround: Before upgrading an earlier version of ESXi to ESXi 8.0, uninstall the iSM
VIB corresponding to iSM on the hypervisor.

● The iDRAC Access via Host OS feature is not supported on VMware ESXi operating 
  systems.

● When the small footprint CIM broker (SFCB) configuration is set to read-only mode
in the VMware ESXi operating system, iSM-Windows remote management (WinRM)
commands such as iDRACHardreset, and EnableInBandSNMPTraps do not function
Workaround: On VMWare ESXi 7.x operatingsystem, use the Invoke-iDRACHardReset command
line utility to perform the iDRACHardreset operation.

● After performing iDRAC HardReset, iSM communication will not establish with iDRAC
  when iDRAC Service Module sfcbd service or daemon script is not running On VMware ESXi operating systems.

● When Local Racadm set is disabled through iDRAC interfaces: 
  * iDRAC Service Module is unsuccessful in configuring the OS to iDRAC Pass-through in the USB NIC mode.
  * iDRAC Service Module functionality is restored when "Local racadm set" is enabled.

● EventID for Lifecycle Controller Logs replicated to OS log will be 0 for
  some of the past events.

● TrapID for In-band SNMP Traps will be 0 for some of the past traps.


● JIT-87572
When iDRAC Hard Reset is disabled in iDRAC and user performs iDRACHardReset 
from the Hypervisor operating systems like VMware ESXi, the result 
indicates success although iDRAC is not reset.

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

● JIT-249985
On Microsoft Windows and Linux operatingsystems, the iSM may be unsuccessful toinject the 
metric data into the iDRAC, evenwhen theidrac.Telemetry.EnableMetricInjection attribute is 
enabled in RACADM.
Workaround: Restart the iDRAC and retry theoperation.

● JIT-241957

When iSM is running in Limited Functionality mode, you can enable or disable the iSM features 
using the RACADM, WS-Man, or Redfish interfaces.However, the iSM features will not 
be functional in the host operating system.


--------------------------------------------------------------------------------
Limitations on all supported operating systems
--------------------------------------------------------------------------------

● JIT-158514, JIT-158740, JIT-158667, JIT-159019
When there is increased workload on the host due to intensive task request by the CPU, the communication between 
iDRAC Service Module and iDRAC will be interrupted for a moment and restored automatically. 
There is no action required by the user. 

While performing feature enablement using the EnableiDRACAccessHostRoute tool, if there are no free slots in the
ManualDNSEntry parameter in the iDRAC, then the OS to iDRAC Pass-through feature may not function.

● iDRAC to OMSA SNMP alert mapping gets enabled when OMSA is running.
To disable the iSM Host SNMP OMSA alert, restart the iDRAC Service Module.

● JIT-214305
While performing feature enablement using the Enable-iDRACAccessHostRoute tool, if there are no free slots in the
ManualDNSEntry parameter in iDRAC and operating system IP address is not updated in ManualDNSEntry, then the OS
to iDRAC Pass-through feature does not function.

● JIT-279015
For all PowerEdge 14G servers, during the validation of Redfish attributes, the last letters for the 
value of Host name and FQDN are not displayed.

● JIT-277931
While starting or restarting iSM, it may take up to 180 seconds for the iSM command-line utility to start 
functioning because the dependent libraries may take some time to initiate.

●The Metric Injection (Host OS Telemetry) feature supports a maximum of 48 metric values on iDRAC 
firmware 7.00.60.00 and earlier versions. 

********************************************************************************
Global Support
********************************************************************************
For information on technical support, contact your service provider.

****************************************************************************************************************************************************************

Copyright ©️ 2023 Dell Inc. or its subsidiaries. All rights reserved. Dell Technologies, 
Dell, and other trademarks are trademarks of Dell Inc. or its subsidiaries. Other 
trademarks may be trademarks of their respective owners.


2023 - 11		Rev. A00 

