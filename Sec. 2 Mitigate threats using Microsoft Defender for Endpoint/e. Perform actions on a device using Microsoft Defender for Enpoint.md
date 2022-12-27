# Introduction

Microsoft Defender for Endpoint provides the remote capability to contain devices and collect forensics data. The Live Response feature allows for a restricted remote access shell on the device.

You're a Security Operations Analyst working at a company that has implemented Microsoft Defender for Endpoint, and your primary job is to remediate incidents. You're assigned an incident with alerts related to a suspicious PowerShell command line. You start by reviewing the incident and understand all the related alerts, devices, and evidence.

You open the alert page to review the Alert Story and decide to perform further analysis on the device. You open the Device page and decide that you need remote access to the device to run a custom PowerShell script to collect more forensics information.

You initiate a Live Response session from the Device page and execute a PowerShell script from your script library. You download the file for use with forensics tools. After reviewing the forensics data, you perform the device isolation action from the Device page.

After completing this module, you'll be able to:

-   Perform actions on a device using Microsoft Defender for Endpoint
-   Conduct forensics data collection using Microsoft Defender for Endpoint
-   Access devices remotely using Microsoft Defender for Endpoint

# Explain device actions

When investigating a device, you can perform actions, collect data, or remotely access the machine. Defender for Endpoint provides the device control required.

You can perform the following containment actions:

-   Isolate Device
    
-   Restrict app execution
    
-   Run antivirus scan
    

You can perform the following investigation actions:

-   Initiate Automated Investigation
    
-   Collect investigation package
    
-   Initiate Live Response Session
    

The Action center provides information on actions that were taken on a device or file.

### Isolate devices from networks

Depending on the severity of the attack and the sensitivity of the device, you might want to isolate the device from the network. This action can help prevent the attacker from controlling the compromised device and performing further activities such as data exfiltration and lateral movement.

This device isolation feature disconnects the compromised device from the network while retaining connectivity to the Defender for Endpoint service, which continues to monitor the device.

On Windows 10, version 1709 or later, you'll have another control over the network isolation level. You can also choose to enable Outlook, Microsoft Teams, and Skype for Business connectivity (a.k.a 'Selective Isolation').

Once you have selected Isolate device on the device page, type a comment and select Confirm. The Action center will show the scan information and the device timeline will include a new event.

When a device is being isolated, a notification is displayed to inform the user that the device is being isolated from the network.

### Restrict app execution

In addition to containing an attack by stopping malicious processes, you can also lock down a device and prevent subsequent attempts of potentially malicious programs from running.

 Important

This action is available for devices on Windows 10, version 1709 or later. This feature is available if your organization uses Microsoft Defender Antivirus. This action needs to meet the Windows Defender Application Control code integrity policy formats and signing requirements. To restrict an application from running, a code integrity policy is applied that only allows files to run if they are signed by a Microsoft issued certificate. This method of restriction can help prevent an attacker from controlling compromised devices and performing further malicious activities.

You’ll be able to reverse the restriction of applications from running at any time. The button on the device page will change to say Remove app restrictions, and then you take the same steps as restricting app execution.

Once you've selected Restrict app execution on the device page, type a comment and select Confirm. The Action center will show the scan information, and the device timeline will include a new event.

When an app is restricted, a notification is displayed to inform the user that an app is being restricted from running.

# Run Microsoft Defender antivirus scan on devices

As part of the investigation or response process, you can remotely initiate an antivirus scan to help identify and remediate malware that might be present on a compromised device.

 Important

This action is available for devices on Windows 10, version 1709 or later. A Microsoft Defender Antivirus (Microsoft Defender AV) scan can run alongside other antivirus solutions, whether Microsoft Defender AV is the active antivirus solution or not. Microsoft Defender AV can be in Passive mode. For more information, see Microsoft Defender Antivirus compatibility.

Once you have selected Run antivirus scan, select the scan type that you'd like to run (quick or full) and add a comment before confirming the scan.

The Action center will show the scan information, and the device timeline will include a new event, reflecting that a scan action was submitted on the device. Microsoft Defender AV alerts will reflect any detections that surfaced during the scan.

 Note

When triggering a scan using Defender for Endpoint response action, Microsoft Defender antivirus 'ScanAvgCPULoadFactor' value still applies and limits the CPU impact of the scan. If ScanAvgCPULoadFactor is not configured, the default value is a limit of 50% maximum CPU load during a scan.

### Initiate automated investigations

You can start a new general purpose automated investigation on the device if needed. While an investigation is running, any other alert generated from the device will be added to an ongoing Automated investigation until that investigation is completed. In addition, if the same threat is seen on other devices, those devices are added to the investigation.

# Collect investigation package from devices

As part of the investigation or response process, you can collect an investigation package from a device. By collecting the investigation package, you can identify the current state of the device and further understand the tools and techniques used by the attacker.

To download the package (Zip file) and investigate the events that occurred on a device

-   Select **Collect investigation package** from the row of response actions at the top of the device page.
    
-   Specify in the text box why you want to do this action. Select **Confirm**.
    
-   The zip file will download
    

Alternate way:

-   Select **Action center** from the response actions section of the device page.
    
-   In the Action center fly-out, select Package collection package available to download the zip file.
    

The package contains the following folders:

## Autoruns

Contains set of files that each represent the content of the registry of a known auto start entry point (ASEP) to help identify attacker’s persistency on the device. If the registry key isn't found, the file will contain the following message: “ERROR: The system was unable to find the specified registry key or value.”

## Installed programs

This .CSV file contains the list of installed programs that can help identify what is currently installed on the device. For more information, see Win32_Product class.

## Network connections

This folder contains a set of data points related to the connectivity information, which can help identify connectivity to suspicious URLs, attacker’s command and control (C&C) infrastructure, any lateral movement, or remote connections.

-   ActiveNetConnections.txt – Displays protocol statistics and current TCP/IP network connections. It provides the ability to look for suspicious connectivity made by a process.
    
-   Arp.txt – Displays the current address resolution protocol (ARP) cache tables for all interfaces.
    
-   ARP cache can reveal other hosts on a network that have been compromised or suspicious systems on the network that might have been used to run an internal attack.
    
-   DnsCache.txt - Displays the contents of the DNS client resolver cache, which includes both entries preloaded from the local Hosts file and any recently obtained resource records for name queries resolved by the computer. This can help in identifying suspicious connections.
    
-   IpConfig.txt – Displays the full TCP/IP configuration for all adapters. Adapters can represent physical interfaces, such as installed network adapters, or logical interfaces, such as dial-up connections.
    
-   FirewallExecutionLog.txt and pfirewall.log
    

## Prefetch files

Windows Prefetch files are designed to speed up the application startup process. It can be used to track all the files recently used in the system and find traces for applications that might have been deleted but can still be found in the prefetch file list.

-   Prefetch folder – Contains a copy of the prefetch files from %SystemRoot%\Prefetch. It's suggested to download a prefetch file viewer to view the prefetch files.
    
-   PrefetchFilesList.txt – Contains the list of all the copied files that can be used to track if there were any copy failures to the prefetch folder.
    

## Processes

Contains a .CSV file listing the running processes, which provide the ability to identify current processes running on the device. This can be useful when identifying a suspicious process and its state.

## Scheduled tasks

Contains a .CSV file listing the scheduled tasks, which can be used to identify routines performed automatically on a chosen device to look for suspicious code that was set to run automatically.

## Security event log

Contains the security event log, which contains records of login or logout activity or other security-related events specified by the system's audit policy. You can open the event log file using the Event viewer.

## Services

Contains a .CSV file that lists services and their states.

## Windows Server Message Block (SMB) sessions

Lists shared access to files, printers, serial ports, and miscellaneous communications between nodes on a network. This can help identify data exfiltration or lateral movement. It also contains files for SMBInboundSessions and SMBOutboundSession. If there are no sessions (inbound or outbound), you'll get a text file that tells you that there are no SMB sessions found.

## System information

Contains a SystemInformation.txt file that lists system information such as OS version and network cards.

## Temp directories

Contains a set of text files that lists the files located in %Temp% for every user in the system. This can help to track suspicious files that an attacker may have dropped on the system. If the file contains the following message: “The system can't find the path specified”, it means that there's no temp directory for this user, and might be because the user didn’t sign in to the system.

## Users and groups

Provides a list of files that each represent a group and its members.

## WdSupportLogs

Provides the MpCmdRunLog.txt and MPSupportFiles.cab.

## CollectionSummaryReport.xls

This file is a summary of the investigation package collection, it contains the list of data points, the command used to extract the data, the execution status, and the error code if there's failure. You can use this report to track if the package includes all the expected data and identify if there were any errors.

# Initiate live response session

Live response provides security operations teams instantaneous access to a device using a remote shell connection. Live response provides you the power to do in-depth investigation and take immediate response actions to promptly contain identified threats.

Live response is designed to enhance investigations by enabling your security operations team to collect forensic data, run scripts, send suspicious entities for analysis, remediate threats, and proactively hunt for emerging threats.

[Microsoft Defender for Endpoint Live Response](https://www.microsoft.com/en-us/videoplayer/embed/RE4qLUW?rel=0&postJsllMsg=true)

With live response, analysts can do all of the following tasks:

-   Run basic and advanced commands to do investigative work on a device.
    
-   Download files such as malware samples and outcomes of PowerShell scripts.
    
-   Download files in the background (new!).
    
-   Upload a PowerShell script or executable to the library and run it on a device from a tenant level.
    
-   Take or undo remediation actions.
    

## Prerequisites

Before you can start a session on a device, make sure you fulfill the following requirements:

**Verify that you're running a supported version of Windows 10 or later**

Enable live response from the settings page. You'll need to enable the live response capability in the Advanced features settings page.

Only users with manage security or global admin roles can edit these settings.

**Ensure that the device has an Automation Remediation level assigned to it**

You'll need to enable, at least, the minimum Remediation Level for a given Device Group. Otherwise you can't establish a Live Response session to a member of that group.

**Enable live response unsigned script execution (optional)**

Allowing the use of unsigned scripts may increase your exposure to threats. Running unsigned scripts isn't recommended as it can increase your exposure to threats. If you must use them however, you'll need to enable the setting in the Advanced features settings page.

**Ensure that you have the appropriate permissions**

Only users who have been provisioned with the appropriate permissions can initiate a session. The option to upload a file to the library is only available to users with the appropriate Role-based access control (RBAC) permissions. The button is greyed out for users with only delegated permissions. Depending on the role that's been granted to you, you can run basic or advanced live response commands. Users' permissions are controlled by RBAC custom role.

## Live response dashboard overview

When you initiate a live response session on a device, a dashboard opens. The dashboard provides information about the session like:

-   Who created the session
    
-   When the session started
    
-   The duration of the session
    

The dashboard also gives you access to:

-   Disconnect session
    
-   Upload files to the library
    
-   Command console
    
-   Command log
    

## Live response commands

Depending on the role that's been granted to you, you can run basic or advanced live response commands. User permissions are controlled by RBAC custom roles. Live response is a cloud-based interactive shell. So, specific command experience may vary in response time depending on network quality and system load between the end user and the target device.

### Basic commands

The following commands are available for user roles that are granted the ability to run basic live response commands.

| Command | Description  |
|---|---|
| [cd] | Changes the current directory.  |
| [cls] | Clears the console screen.  |
| [connect] | Starts a live response session to the device.  |
| [connections] | Shows all the active connections.  |
| [dir] | Shows a list of files and subdirectories in a directory.  |
| [getfile] <file_path> | Downloads a file in the background.  |
| [drivers] | Shows all drivers installed on the device.  |
| [fg] <command ID> | Returns a file download to the foreground.  |
| [fileinfo] | Get information about a file.  |
| [findfile] | Locates files by a given name on the device.  |
| [help] | Provides help information for live response commands.  |
| [persistence] | Shows all known persistence methods on the device.  |
| [processes] | Shows all processes running on the device.  |
| [registry] | Shows registry values.  |
| [scheduledtasks] | Shows all scheduled tasks on the device.  |
| [services] | Shows all services on the device.  |
| [trace] | Sets the terminal's logging mode to debug. |

### Advanced commands

The following commands are available for user roles that are granted the ability to run advanced live response commands.

| Command | Description  |
|---|---|
| analyze | Analyses the entity with various incrimination engines to reach a verdict.  |
| getfile | Gets a file from the device. This command has a prerequisite command. You can use the -auto command with getfile to automatically run the prerequisite command.  |
| run | Runs a PowerShell script from the library on the device.  |
| library | Lists files that were uploaded to the live response library.  |
| putfile | Puts a file from the library to the device. Files are saved in a working folder and are deleted when the device restarts by default.  |
| remediate | Remediates an entity on the device. The remediation action will vary depending on the entity type. This command has a prerequisite command. You can use the -auto command with remediate to automatically run the prerequisite command.  |
| Undo | Restores an entity that was remediated. |

## Use live response commands

The commands that you can use in the console follow similar principles as Windows Commands. The advanced commands offer expanded capabilities that allow you to take more powerful actions. Advanced actions include downloading or uploading a file, running scripts on the device, and taking remediation actions on an entity.

### Get a file from the device

For scenarios when you'd like to get a file from a device you're investigating, you can use the [getfile] command. The [getfile] command allows you to save the file from the device for further investigation.

The following file size limits apply:

-   getfile limit: 3 GB
    
-   fileinfo limit: 10 GB
    
-   library limit: 250 MB
    

### Download a file in the background

To enable your security operations team to continue investigating an impacted device, files can now be downloaded in the background.

-   To download a file in the background, in the live response command console, type **getfile <file_path>**.
    
-   If you're waiting for a file to be downloaded, you can move it to the background by using **Ctrl + Z**.
    
-   To bring a file download to the foreground, in the live response command console, type **fg <command_id>**.
    

Here are some examples:

| Command | What it does  |
|---|---|
| getfile "C:\windows\some_file.exe" | Starts downloading a file named some_file.exe in the background.  |
| fg 1234 | Returns a download with command ID 1234 to the foreground. |

### Put a file in the library

Live response has a library where you can put files in. The library stores files (such as scripts) that can be run in a live response session at the tenant level. Live response allows PowerShell scripts to run. However, you must first put the files into the library before you can run them. You can have a collection of PowerShell scripts that can run on devices that you initiate live response sessions with.

To upload a file in the library:

1.  Select **Upload file to library**.
    
2.  Select **Browse** and select the file.
    
3.  Provide a brief description.
    
4.  Specify if you'd like to overwrite a file with the same name.
    
5.  If you'd like to be, know what parameters are needed for the script, select the script parameters check box. In the text field, enter an example and a description.
    
6.  Select **Confirm**.
    
7.  (Optional) To verify that the file was uploaded to the library, run the library command.
    

### Cancel a command

Anytime during a session, you can cancel a command by pressing CTRL + C.

### Automatically run prerequisite commands

Some commands have prerequisite commands to run. If you don't run the prerequisite command, you'll get an error. For example, running the download command without _fileinfo_ will return an error. You can use the auto flag to automatically run prerequisite commands, for example:

```Console
getfile c:\Users\user\Desktop\work.txt -auto

```

### Run a PowerShell script

Before you can run a PowerShell script, you must first upload it to the library. After uploading the script to the library, use the **run** command to run the script. If you plan to use an unsigned script in the session, you'll need to enable the setting in the Advanced features settings page.

### Apply command parameters

View the console help to learn about command parameters. To learn about an individual command, run:

```PowerShell
help <command name>

```

When applying parameters to commands, parameters are handled based on a fixed order:

```PowerShell
<command name> param1 param2

```

When specifying parameters outside of the fixed order, specify the name of the parameter with a hyphen before providing its value:

```PowerShell
<command name> -param2_name param2

```

When using commands that have prerequisite commands, you can use flags:

```PowerShell
<command name> -type file -id <file path> - auto or remediate file <file path> - auto.

```

### Supported output types

Live response supports table and JSON format output types. For each command, there's a default output behavior. You can modify the output in your preferred output format using the following commands:

-   -output json
    
-   -output table
    

### Supported output pipes

Live response supports output piping to CLI and file. CLI is the default output behavior. You can pipe the output to a file using the following command: [command] > [filename].txt.

### View the command log

Select the Command log tab to see the commands used on the device during a session. Each command is tracked with full details such as:

-   ID
    
-   Command line
    
-   Duration
    
-   Status and input or output side bar
    

## Command examples

The next commands are examples that demonstrate the use of the live response commands.

### Analyze

```Console
# Analyze the file malware.txt

analyze file c:\Users\user\Desktop\malware.txt

```

```Console
# Analyze the process by PID

analyze process 1234

```

## Limitations

Live response has the following limitations:

-   Live response sessions are limited to 10 live response sessions at a time.
    
-   Large-scale command execution isn't supported.
    
-   Live response session inactive timeout value is 5 minutes.
    
-   A user can only initiate one session at a time.
    
-   A device can only be in one session at a time.
    
-   The following file size limits apply:
    
    -   Getfile limit: 3 GB
        
    -   Fileinfo limit: 10 GB
        
    -   Library limit: 250 MB
# Knowledge check

1. Which type of information is collected in an Investigation package?

Command History

[X] Prefetch Files

Correct. Prefetch files are collected.

Network transactions

2. Which of the actions below is a Device action?

Reboot

Reformat device

[X] Isolate device

Correct. You can isolate a device.

# Summary and resources

You learned how Microsoft Defender for Endpoint provides the remote capability to contain devices and collect forensics data. The Live Response feature allows for a restricted remote access shell on the device.

You should now be able to:

-   Perform actions on a device using Microsoft Defender for Endpoint
-   Conduct forensics data collection using Microsoft Defender for Endpoint
-   Access devices remotely using Microsoft Defender for Endpoint

## Learn more

You can learn more by reviewing the following.

[Become a Microsoft Defender for Endpoint Ninja](https://nam06.safelinks.protection.outlook.com/?url=https%3A%2F%2Ftechcommunity.microsoft.com%2Ft5%2Fmicrosoft-defender-for-endpoint%2Fbecome-a-microsoft-defender-atp-ninja%2Fba-p%2F1515647&data=04%7C01%7Cbneeb%40microsoft.com%7C70ade848411b4dbb43bd08d8b1e6e51e%7C72f988bf86f141af91ab2d7cd011db47%7C1%7C0%7C637454952552234995%7CUnknown%7CTWFpbGZsb3d8eyJWIjoiMC4wLjAwMDAiLCJQIjoiV2luMzIiLCJBTiI6Ik1haWwiLCJXVCI6Mn0%3D%7C1000&sdata=%2FfCCxsoJg5FwJwrgGstqLGYHuABKDTOlvmPbT3zVQ6w%3D&reserved=0%3Fazure-portal%3Dtrue)

[Microsoft Tech Community Security Webinars](https://techcommunity.microsoft.com/t5/microsoft-security-and/security-community-webinars/ba-p/927888)