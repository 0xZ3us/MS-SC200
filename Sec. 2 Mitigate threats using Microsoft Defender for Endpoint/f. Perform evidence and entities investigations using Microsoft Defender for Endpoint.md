# Introduction

Microsoft Defender for Endpoint provides information about forensic artifacts found in the environment. There are specific observable pages for Files, User Accounts, IP Addresses, and Domains.

You're a Security Operations Analyst working at a company that has implemented Microsoft Defender for Endpoint, and your primary job is to remediate incidents. You're assigned an incident with alerts related to a suspicious PowerShell command line.

You start by reviewing the incident and understand all the related alerts, devices, and evidence. The evidence tab shows three files, six processes, and one persistence method. One of the files has a name you have never seen before. You open the file page to review everything known about the file.

The file has never been seen in the organization other than this incident. If the situation is malware, it's good to know whether this file impacted only this machine. You decide to submit a deep analysis on the file to see if the file performs any suspicious activities. The results show suspicious activity; you then select Add Indicator from the file page to ensure Defender for Endpoint will use the indicator for detections.

After completing this module, you'll be able to:

-   Investigate files in Microsoft Defender for Endpoint
-   Investigate domains and IP addresses in Microsoft Defender for Endpoint
-   Investigate user accounts in Microsoft Defender for Endpoint

# Investigate a file

Investigate the details of a file associated with a specific alert, behavior, or event to help determine if the file exhibits malicious activities, identify the attack motivation, and understand the potential scope of the breach.

![Screen shot of the Microsoft Defender for Endpoint File page information.](https://learn.microsoft.com/en-us/training/wwl-sci/perform-evidence-entities-investigations-microsoft-defender-for-endpoint/media/file-page.png)

There are many ways to access the detailed profile page of a specific file. For example, you can use the search feature, select a link from the Alert process tree, Incident graph, Artifact timeline, or select an event listed in the Device timeline. You can get information from the following sections in the file view:

File details, Malware detection, File prevalence

-   File details, malware detection, and file prevalence
    
-   Alerts
    
-   Observed in organization
    
-   Deep analysis
    
-   File names
    

Along the top of the profile page, above the file information cards. Actions you can perform here include:

-   Stop and quarantine
    
-   Add/edit indicator
    
-   Download file
    
-   Consult a threat expert
    
-   Action center
    

## Detailed profile page

### File details, malware detection, and file prevalence

The file details, incident, malware detection, and file prevalence cards display various attributes about the file. You'll see details such as the file’s MD5, the Virus Total detection ratio, and Microsoft Defender AV detection if available, and the file’s prevalence, both worldwide and within your organizations.

### Alerts

The Alerts tab provides a list of alerts that are associated with the file. This list covers much of the same information as the Alerts queue, except for the device group that the affected device belongs to, if applicable. You can choose what kind of information is shown by selecting Customize columns from the toolbar above the column headers.

### Observed in organization

The Observed in the organization tab allows you to specify a date range to see which devices have been observed with the file. This tab will show a maximum of 100 devices. To see all devices with the file, export the tab to a CSV file, by selecting Export from the action menu above the tab's column headers.

Use the slider or the range selector to quickly specify a time period that you want to check for events involving the file. You can specify a time window as small as a single day. This will allow you to see only files that communicated with that IP Address at that time, drastically reducing unnecessary scrolling and searching.

### Deep analysis

The Deep analysis tab allows you to submit the file for deep analysis to uncover more details about the file's behavior and its effect within your organizations. After you submit the file, the deep analysis report will appear in this tab once the results are available. If deep analysis didn't find anything, the report will be empty, and the results space will remain blank.

### File names

The File names tab lists all names the file has been observed to use within your organizations.

## Deep file analysis

Cyber security investigations are typically triggered by an alert. Alerts are related to one or more observed files that are often new or unknown. Clicking a file takes you to the file view, where you can see the file's metadata. To enrich the data related to the file, you can submit the file for deep analysis.

The Deep analysis feature executes a file in a secure, fully instrumented cloud environment. Deep analysis results show the file's activities, observed behaviors, and associated artifacts, such as dropped files, registry modifications, and communication with IPs. Deep analysis currently supports extensive analysis of portable executable (PE) files (including .exe and .dll files).

Deep analysis of a file takes several minutes. Once the file analysis is complete, the Deep Analysis tab will update to display the date and time of the latest results available, and a summary of the report itself.

The Deep analysis summary includes a list of observed behaviors, some of which can indicate malicious activity, and observables, including contacted IPs and files created on the disk. If nothing was found, these sections will display a brief message.

The deep analysis results are matched against threat intelligence, and any matches will generate appropriate alerts.

Use the deep analysis feature to investigate the details of any file, usually during an investigation of an alert or for any other reason where you suspect malicious behavior. This feature is available within the Deep analysis tab on the file's profile page.

[Microsoft Defender for Endpoint Deep analysis](https://www.microsoft.com/en-us/videoplayer/embed/RE4aAYy?rel=0&postJsllMsg=true)

Submit for deep analysis is enabled when the file is available in the Defender for Endpoint backend sample collection, or if it was observed on a Windows 10 device that supports submitting to deep analysis. You can also manually submit a sample through the Microsoft Security Center Portal if the file wasn't observed on a Windows 10 device and wait for Submit for deep analysis button to become available.

When the sample is collected, Defender for Endpoint runs the file in a secure environment and creates a detailed report of observed behaviors and associated artifacts, such as files dropped on devices, communication to IPs, and registry modifications.

Submit files for deep analysis:

1.  Select the file that you want to submit for deep analysis. You can select or search a file from any of the following views:
    
    -   Alerts - select the file links from the Description or Details in the Artifact timeline
        
    -   Devices list - select the file links from the Description or Details in the Device in the organization section
        
    -   Search box - select File from the drop–down menu and enter the file name
        
2.  In the Deep analysis tab of the file view, select Submit.
    

Only PE files are supported, including _.exe_ and _.dll_ files. A progress bar is displayed and provides information on the different stages of the analysis. You can then view the report when the analysis is done.

### View deep analysis reports

View the deep analysis report that Defender for Endpoint provides to see the details of the deep analysis conducted on the file you submitted. This feature is available in the file view context.

You can view the comprehensive report that provides details on the following sections:

-   Behaviors
    
-   Observables
    

The details provided can help you investigate if there are indications of a potential attack.

1.  Select the file you submitted for deep analysis.
    
2.  Select the Deep analysis tab. If there are any previous reports, the report summary will appear in this tab.
    

### Troubleshoot deep analysis

If you encounter a problem when trying to submit a file, try each of the following troubleshooting steps.

1.  Ensure that the file in question is a PE file. PE files typically have .exe or .dll extensions (executable programs or applications).
    
2.  Ensure the service has access to the file, that it still exists, and hasn't been corrupted or modified.
    
3.  You can wait a short while and try to submit the file again if the queue is full or there was a temporary connection or communication error.
    
4.  If the sample collection policy isn't configured, then the default behavior is to allow sample collection. If it's configured, then verify the policy setting allows sample collection before submitting the file again. When sample collection is configured, then check the following registry value:
    
    -   Path: HKLM\SOFTWARE\Policies\Microsoft\Windows Advanced Threat Protection
        
    -   Name: AllowSampleCollection
        
    -   Type: DWORD
        
    -   Hexadecimal value:
        
    -   Value = 0 – block sample collection
        
    -   Value = 1 – allow sample collection
        
5.  Change the organizational unit through the Group Policy.
    

## File response actions

Quickly respond to detected attacks by stopping and quarantining files or blocking a file. After taking action on files, you can check activity details in the Action center. Response actions are available on a file's detailed profile page.

Response actions run along the top of the file page and include:

-   Stop and Quarantine File
    
-   Add Indicator
    
-   Download file
    
-   Action center
    

### Stop and quarantine file

You can contain an attack in your organization by stopping the malicious process and quarantining the file where it was observed.

You can only take this action if:

-   The device you're taking action on is running Windows 10, version 1703 or later
    
-   The file doesn't belong to trusted third-party publishers or not signed by Microsoft
    
-   Microsoft Defender Antivirus must at least be running on Passive mode.
    

The Stop and Quarantine File action includes stopping running processes, quarantining the files, and deleting persistent data, such as any registry keys. The stop and quarantine file action is limited to a maximum of 1000 devices. To stop a file on a larger number of devices, see Add indicator to block or allow file.

**Stop and quarantine files**

1.  Select the file you want to stop and quarantine. You can select a file from any of the following views or use the Search box:
    
    -   Alerts - select the corresponding links from the Description or Details in the Artifact timeline
        
    -   Search box - select File from the drop-down menu and enter the file name
        
2.  Go to the top bar and select **Stop and Quarantine File**.
    
3.  Specify a reason, then select **Confirm**.
    

The Action center shows the submission information:

```
- Submission time - Shows when the action was submitted.

- Success - Shows the number of devices where the file has been stopped and quarantined.

- Failed - Shows the number of devices where the action failed and details about the failure.

- Pending - Shows the number of devices where the file is yet to be stopped and quarantined from. This can take time for cases when the device is offline or not connected to the network.
```

Select any of the status indicators to view more information about the action. For example, select Failed to see where the action failed. When the file is removed from a device, the user receives a notification.

A new event is added for each device in the device timeline where a file was stopped and quarantined. For files widely used throughout an organization, a warning is shown before action is taken to validate that the operation is intended.

**Restore file from quarantine**

You can roll back and remove a file from quarantine if you’ve determined that it’s clean after an investigation. Run the following command on each device where the file was quarantined.

1.  Open an elevated command-line prompt on the device:
    
    -   Go to Start and type _cmd_.
        
    -   Right-click Command prompt and select **Run as administrator**.
        
2.  Enter the following command, and press Enter:
    
    ```PowerShell
    “%ProgramFiles%\Windows Defender\MpCmdRun.exe” –Restore –Name EUS:Win32/CustomEnterpriseBlock –All
    
    ```
    

### Add indicator to block or allow a file

You can prevent further propagation of an attack in your organization by banning potentially malicious files or suspected malware. If you know a potentially malicious portable executable (PE) file, you can block it. This operation will prevent it from being read, written, or executed on devices in your organization.

**Enable the block file feature**

To start blocking files, you first need to turn the Block or allow feature on in Settings.

**Allow or block file**

When you add an indicator hash for a file, you can choose to raise an alert and block the file whenever a device in your organization attempts to run it. Files automatically blocked by an indicator won't show up in the files' Action center, but the alerts will still be visible in the Alerts queue. See manage indicators for more details on blocking and raising alerts on files. To stop blocking a file, remove the indicator. You can do so via the Edit Indicator action on the file's profile page. This action will be visible in the same position that the _Add Indicator_ action was before adding the indicator. You can also edit indicators from the Settings page, under Rules > Indicators. Indicators are listed in this area by their file's hash.

### Download file

Selecting Download file from the response actions allows you to download a local, password-protected .zip archive containing your file. When you select this action, a fly-out will appear. From the fly-out, you can record a reason as to why you're downloading the file. You can also set a password to open the file. If a file isn't already stored by Defender for Endpoint, you can't download it. Instead, you'll see a Collect file button in the same location. If a file hasn't been seen in the organization in the past 30 days, Collect file will be disabled.

### Check activity details in the action center

The Action center provides information on actions that were taken on a device or file. You’ll be able to view the following details:

-   Investigation package collection
    
-   Antivirus scan
    
-   App restriction
    
-   Device isolation
    

All other related details are also shown, for example, submission date/time, submitting user, and if the action succeeded or failed.

# Investigate a user account

Identify user accounts with the most active alerts (displayed on the dashboard as "Users at risk"), and investigate cases of potentially compromised credentials. Or, pivot on the associated user account when investigating an alert or device to identify possible lateral movement between devices with that user account.

You can find user account information in the following views:

-   Dashboard
    
-   Alert queue
    
-   Device details page
    

A clickable user account link is available in these views. Selecting the link will take you to the user account details page where more details about the user account are displayed.

When you investigate a user account entity, you'll see:

-   User account details and logged on devices, role, log-on type, and other details
    
-   Overview of the incidents and user's devices
    
-   Alerts related to this user
    
-   Observed locations in the organization (devices logged on to)
    

### User details

The User details pane on left provides information about the user, such as related open incidents, active alerts, SAM name, SID, number of devices the user is logged on to, when the user was first and last seen, role, and log-on types. Depending on the integration features you've enabled, you'll see other details.

### Overview

The Overview tab shows the incident details and a list of the devices the user has logged on to. You can expand the device list to see details of the log-on events for each device.

### Alerts

The Alerts tab provides a list of alerts that are associated with the user account. This list is a filtered view of the Alert queue and shows alerts where the user context is the selected user account, the date when the last activity was detected, a short description of the alert, the device associated with the alert, the alert's severity, the alert's status in the queue, and who is assigned the alert.

### Observed in organization

The Observed in organization tab allows you to specify a date range to see a list of devices where this user was observed logged on to, the most frequent and least frequent logged on user account for each of these devices, and total observed users on each device. Selecting an item on the Observed in organization table will expand the item, revealing more details about the device. Directly selecting a link within an item will send you to the corresponding page.

# Investigate an IP address

Examine possible communication between your devices and external internet protocol (IP) addresses.

Identifying all devices in the organization that communicated with a suspected or known malicious IP address, such as Command and Control (C2) servers, helps determine the potential scope of the breach. You can then quarantine associated files, and infected devices.

You can find information from the following sections in the IP address view:

-   IP worldwide
    
-   Reverse DNS names
    
-   Alerts related to this IP
    
-   IP in organization
    
-   Prevalence
    

### IP Worldwide and Reverse DNS names

The IP address details section shows attributes of the IP address such as its ASN and its Reverse DNS names.

### Alerts related to this IP

The Alerts related to this IP section provides a list of alerts that are associated with the IP.

### IP in organization

The IP in the organization section provides details on the prevalence of the IP address in the organization.

### Prevalence

The Prevalence section displays how many devices have connected to this IP address and when the IP was first and last seen. You can filter the results of this section by time period; the default period is 30 days.

### Most recent observed devices with IP

The most recent observed devices with IP section provides a chronological view on the events and associated alerts that were observed on the IP address.

Investigate an external IP:

1.  Select **IP** from the Search bar drop-down menu.
    
2.  Enter the IP address in the Search field.
    
3.  Select the search icon or press Enter.
    

Details about the IP address are displayed, including registration details (if available), reverse IPs (for example, domains), prevalence of devices in the organization that communicated with this IP Address (during the selected time period), and the devices in the organization that were observed communicating with this IP address.

# Investigate a domain

Investigate a domain to see if devices and servers in your enterprise network have been communicating with a known malicious domain.

You can investigate a domain by using the search feature or by clicking on a domain link from the Device timeline.

You can see information from the following sections in the URL view:

-   URL details, Contacts, Nameservers
    
-   Alerts related to this URL
    
-   URL in organization
    
-   Most recent observed devices with URL
    

### URL worldwide

The URL Worldwide section lists the URL, a link to further details, the number of related open incidents, and the number of active alerts.

### Incident

The Incident card displays a bar chart of all active alerts in incidents over the past 180 days.

### Prevalence

The Prevalence card provides details on the URL's prevalence within the organization over a specified period of time.

Although the default time period is the past 30 days, you can customize the range by selecting the downward-pointing arrow in the corner of the card. The shortest range available is for prevalence over the past day, while the longest range is over the past six months.

### Alerts

The Alerts tab provides a list of alerts that are associated with the URL. The table shown here's a filtered version of the alerts visible on the Alert queue screen, showing only alerts associated with the domain, their severity, status, the associated incident, classification, investigation state, and more.

The Alerts tab can be adjusted to show more or less information by selecting Customize columns from the action menu above the column headers. The number of items displayed can also be adjusted by selecting items per page on the same menu.

### Observed in organization

The Observed in organization tab provides a chronological view of the events and associated alerts observed on the URL. This tab includes a timeline and a customizable table-listing event details, such as the time, device, and a brief description of what happened.

You can view events from different periods of time by entering the dates into the text fields above the table headers. You can also customize the time range by selecting different areas of the timeline.

Investigate a domain:

1.  Select **URL** from the Search bar drop-down menu.
    
2.  Enter the URL in the Search field.
    
3.  Select the search icon or press Enter. Details about the URL are displayed. Search results will only be returned for URLs observed in communications from devices in the organization.
    
4.  Use the search filters to define the search criteria. You can also use the timeline search box to filter the displayed results of all devices in the organization observed communicating with the URL, the file associated with the communication and the last date observed.
    
5.  Selecting any of the device names will take you to that device's view, where you can continue to investigate reported alerts, behaviors, and events.

# Knowledge check

1. Which of the following artifact types has an investigation page?

[X] Domain

Correct. There's an investigation page for Domain.

Hunter

Threat Actor

2. What information is provided by a deep file analysis?

Command history

[X] Registry Modifications

Correct. Registry modifications are reported.

Code change history

3. Which information is provided on the user account page?

[X] Associated alerts

Correct. This is provided.

Security groups

Threat hunt ID

# Summary and resources

You learned how Microsoft Defender for Endpoint provides information about forensic artifacts found in the environment. How there are specific observable pages for Files, User Accounts, IP Addresses, and Domains.

You should now be able to:

-   Investigate files in Microsoft Defender for Endpoint
-   Investigate domains and IP addresses in Microsoft Defender for Endpoint
-   Investigate user accounts in Microsoft Defender for Endpoint

## Learn more

You can learn more by reviewing the following.

[Become a Microsoft Defender for Endpoint Ninja](https://nam06.safelinks.protection.outlook.com/?url=https%3A%2F%2Ftechcommunity.microsoft.com%2Ft5%2Fmicrosoft-defender-for-endpoint%2Fbecome-a-microsoft-defender-atp-ninja%2Fba-p%2F1515647&data=04%7C01%7Cbneeb%40microsoft.com%7C70ade848411b4dbb43bd08d8b1e6e51e%7C72f988bf86f141af91ab2d7cd011db47%7C1%7C0%7C637454952552234995%7CUnknown%7CTWFpbGZsb3d8eyJWIjoiMC4wLjAwMDAiLCJQIjoiV2luMzIiLCJBTiI6Ik1haWwiLCJXVCI6Mn0%3D%7C1000&sdata=%2FfCCxsoJg5FwJwrgGstqLGYHuABKDTOlvmPbT3zVQ6w%3D&reserved=0%3Fazure-portal%3Dtrue)

[Microsoft Tech Community Security Webinars](https://techcommunity.microsoft.com/t5/microsoft-security-and/security-community-webinars/ba-p/927888)