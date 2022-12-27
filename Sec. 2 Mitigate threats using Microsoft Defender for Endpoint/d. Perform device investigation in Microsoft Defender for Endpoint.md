# Introduction

Microsoft Defender for Endpoint provides detailed device information, including forensics information.

You're a Security Operations Analyst working at a company that has implemented Microsoft Defender for Endpoint, and your primary job is to remediate incidents. You're assigned an incident with alerts related to a suspicious PowerShell command line. You start by reviewing the incident and understand all the related alerts, devices, and evidence. You open the alert page to review the Alert Story and decide to perform further analysis on the device.

You open the Device page to provide more context to the incident. The overview tab on the Device page immediately provides concerning information such as the Risk level and Exposure level. You select the Alerts tab to see a history of alerts for the device. Next, you choose the Timeline tab to see a list of events from the device. You see many suspicious events.

After completing this module, you'll be able to:

-   Use the device page in Microsoft Defender for Endpoint
-   Describe device forensics information collected by Microsoft Defender for Endpoint
-   Describe behavioral blocking by Microsoft Defender for Endpoint

# Use the device inventory list

The Device inventory page shows a list of the devices in your network where alerts were generated. By default, the queue displays devices with alerts seen in the last 30 days. Select a device to open the Device page. The Device page is also accessed from various investigation pages like Incidents and Alerts.

[![Screen shot of Defender for Endpoint Device Inventory List](https://learn.microsoft.com/en-us/training/wwl-sci/perform-device-investigations-microsoft-defender-for-endpoints/media/device-list.png)](https://learn.microsoft.com/en-us/training/wwl-sci/perform-device-investigations-microsoft-defender-for-endpoints/media/device-list.png#lightbox)

At a glance, you'll see information such as domain, risk level, OS platform, and other details for easy identification of devices most at risk.

During the onboarding process, the Devices list is gradually populated with devices as they begin to report sensor data. Use this view to track your onboarded endpoints as they come online, or download the complete endpoint list as a CSV file for offline analysis.

## Risk level

The risk level reflects the overall risk assessment of the device based on a combination of factors, including the types and severity of active alerts on the device. Resolving active alerts, approving remediation activities, and suppressing subsequent alerts can lower the risk level.

## Exposure level

The exposure level reflects the current exposure of the device based on the cumulative impact of its pending security recommendations. The possible levels are low, medium, and high. Low exposure means your devices are less vulnerable to exploitation.

If the exposure level says, "No data available," there are a few reasons why this may be the case:

-   The device stopped reporting for more than 30 days – in that case, it's considered inactive, and the exposure isn't computed
    
-   The device OS isn't supported - see minimum requirements for Microsoft Defender for Endpoint
    
-   The device has a stale agent (unlikely)
    

## Health state

The following device health states:

-   Active – Devices that are actively reporting sensor data to the service.
    
-   Inactive – Devices that have stopped sending signals for more than seven days.
    
-   Misconfigured – Devices that have impaired communications with service or are unable to send sensor data. Misconfigured devices can further be classified to:
    
    -   No sensor data
        
    -   Impaired communications
        

## Antivirus status

The antivirus status for Windows 10 devices only:

-   Disabled - Virus & threat protection is turned off.
    
-   Not reporting - Virus & threat protection isn't reporting.
    
-   Not updated - Virus & threat protection isn't up to date.

# Investigate the device

Investigate the details of an alert raised on a specific device to identify other behaviors or events that might be related to the alert or the potential scope of the breach.

You can select affected devices whenever you see them in the portal to open a detailed report about that device. Affected devices are identified in the following areas:

-   Devices list
    
-   Alerts queue
    
-   Security operations dashboard
    
-   Any individual alert
    
-   Any individual file details view
    
-   Any IP address or domain details view
    

When you investigate a specific device, you'll see:

-   Device details
    
-   Response actions
    
-   Tabs - overview, alerts, timeline, security recommendations, software inventory, discovered vulnerabilities, missing KBs (Knowledge Base IDs)
    
-   Cards (active alerts, logged on users, security assessment)
    

## Device details

The device details section provides information such as the device's domain, OS, and health state. If there's an investigation package available on the device, you'll see a link that allows you to download the package.

## Response actions

Response actions run along the top of a specific device page and include:

-   Manage tags
    
-   Isolate device
    
-   Restrict app execution
    
-   Run antivirus scan
    
-   Collect investigation package
    
-   Initiate Live Response Session
    
-   Initiate automated investigation
    
-   Consult a threat expert
    
-   Action center
    

You can take response actions in the Action center, on a specific device page, or on a specific file page.

## Tabs

### Overview

The Overview tab displays the cards for active alerts, logged on users, and security assessment.

**Active alerts**

You can view the overall number of active alerts from the last 30 days in your network from the tile. Alerts are grouped into New and In progress. Each group is further subcategorized into their corresponding alert severity levels. Select the number of alerts inside each alert ring to see a sorted view of that category's queue (New or In progress).

**Logged on users**

The Logged on users card shows how many users have logged on in the past 30 days, and the most and least frequent users. Selecting the "See all users" link opens the details pane, which displays user type, sign in type, and when the user was first and last seen.

**Security assessments**

The Security assessments card shows the overall exposure level, security recommendations, installed software, and discovered vulnerabilities. A device's exposure level is determined by the cumulative impact of its pending security recommendations.

### Alerts

The Alerts tab provides a list of alerts that are associated with the device. This list is a filtered version of the Alerts queue, and shows a short description of the alert, severity (high, medium, low, informational), status in the queue (new, in progress, resolved), classification (not set, false alert, true alert), investigation state, category of alert, who is addressing the alert, and last activity. You can also filter the alerts.

### Timeline

The Timeline tab provides a chronological view of the events and associated alerts that have been observed on the device. This can help you correlate any events, files, and IP addresses related to the device.

The timeline also enables you to selectively drill down into events that occurred within a given time period. You can view the temporal sequence of events that occurred on a device over a selected time period. To further control your view, you can filter by event groups or customize the columns.

Some of the functionality includes:

-   Search for specific events
    
    -   Use the search bar to look for specific timeline events.
-   Filter events from a specific date
    
    -   Select the calendar icon in the upper left of the table to display events in the past day, week, 30 days, or a custom range. By default, the device timeline is set to display the events from the past 30 days.
        
    -   Use the timeline to jump to a specific moment in time by highlighting the section. The arrows on the timeline pinpoint automated investigations
        
-   Export detailed device timeline events
    
    -   Export the device timeline for the current date or a specified date range up to seven days.

More details about certain events are provided and vary depending on the type of event, for example:

-   Contained by Application Guard - the web browser event was restricted by an isolated container
    
-   Active threat detected - the threat detection occurred while the threat was running
    
-   Remediation unsuccessful - an attempt to remediate the detected threat was invoked but failed
    
-   Remediation successful - the detected threat was stopped and cleaned
    
-   Warning bypassed by user - the Windows Defender SmartScreen warning was dismissed and overridden by a user
    
-   Suspicious script detected - a potentially malicious script was found running
    
-   The alert category - if the event led to the generation of an alert, the alert category ("Lateral Movement", for example) is provided
    

**Flag an event**

While navigating the device timeline, you can search and filter for specific events. You can set event flags by:

-   Highlighting the most important events
    
-   Marking events that require a deep dive
    
-   Building a clean breach timeline
    

Find the event that you want to flag. Select the flag icon in the Flag column.

**View flagged events**

In the timeline Filters section, enable Only Flagged events. Select Apply. Only flagged events are displayed. You can apply more filters by clicking the time bar. This will only show events prior to the flagged event.

### Event details

Select an event to view relevant details about that event. A panel displays to show general event information. When applicable and data is available, a graph showing related entities and their relationships are also shown.

To further inspect the event and related events, you can quickly run an advanced hunting query by selecting Hunt for related events. The query will return the selected event and the list of other events that occurred around the same time on the same endpoint.

### Security recommendations

Security recommendations are generated from Microsoft Defender for Endpoint's Threat & Vulnerability Management capability. Selecting a recommendation will show a panel where you can view relevant details such as the description of the recommendation and the potential risks associated with not enacting it.

### Software inventory

The Software inventory tab lets you view software on the device, along with any weaknesses or threats. Selecting the name of the software will take you to the software details page, where you can view security recommendations, discovered vulnerabilities, installed devices, and version distribution.

### Discovered vulnerabilities

The Discovered vulnerabilities tab shows the name, severity, and threat insights of discovered vulnerabilities on the device. Selecting specific vulnerabilities will show a description and details.

### Missing knowledge bases

The Missing KBs tab lists the missing security updates for the device.

# Use behavioral blocking

Today’s threat landscape is overrun by fileless malware that lives off the land. Malware with highly polymorphic threats that mutate faster than traditional solutions can keep up with, and human-operated attacks that adapt to what adversaries find on compromised devices. Traditional security solutions aren't sufficient to stop such attacks. You need artificial intelligence (AI) and machine learning (ML) backed capabilities, such as behavioral blocking and containment, included in Defender for Endpoint.

Behavioral blocking and containment capabilities can help identify and stop threats based on their behaviors and process trees even when the threat has already started. Next-generation protection, EDR, and Defender for Endpoint components and features work together in behavioral blocking and containment capabilities.

Behavioral blocking and containment capabilities work with multiple components and features of Defender for Endpoint to stop attacks immediately and prevent attacks from progressing.

-   Next-generation protection (which includes Microsoft Defender Antivirus) can detect threats by analyzing behaviors and stop threats that have started running.
    
-   Endpoint detection and response (EDR) receives security signals from across your network, devices, and Operating System (OS) kernel behavior. As threats are detected, alerts are created. Multiple alerts of the same type are aggregated into incidents, which makes it easier for your security operations team to investigate and respond.
    
-   Defender for Endpoint has a wide range of optics across identities, email, data, and apps. And the network, endpoint, and kernel behavior signals received through EDR. A component of Microsoft 365 Defender, Defender for Endpoint processes and correlates these signals, raises detection alerts, and connects related alerts in incidents.
    

With these capabilities, more threats can be prevented or blocked, even if they start running. Whenever suspicious behavior is detected, the threat is contained, alerts are created, and threats are stopped in their tracks.

The following image shows an example of an alert that was triggered by behavioral blocking and containment capabilities:

[![Screen shots of the Behavior block alert.](https://learn.microsoft.com/en-us/training/wwl-sci/perform-device-investigations-microsoft-defender-for-endpoints/media/blocked-behavior-alert.png)](https://learn.microsoft.com/en-us/training/wwl-sci/perform-device-investigations-microsoft-defender-for-endpoints/media/blocked-behavior-alert.png#lightbox)

## Client behavioral blocking

Client behavioral blocking is a component of behavioral blocking and containment capabilities in Defender for Endpoint. As suspicious behaviors are detected on devices, referred to as clients or endpoints, artifacts, like files or applications are blocked, checked, and remediated automatically.

[![Diagram of the pre execution and post execution detection engines process.](https://learn.microsoft.com/en-us/training/wwl-sci/perform-device-investigations-microsoft-defender-for-endpoints/media/pre-execution-post-execution-detection-engines.png)](https://learn.microsoft.com/en-us/training/wwl-sci/perform-device-investigations-microsoft-defender-for-endpoints/media/pre-execution-post-execution-detection-engines.png#lightbox)

### How client behavioral blocking works

Microsoft Defender Antivirus can detect suspicious behavior, malicious code, fileless and in-memory attacks, and more on a device. When suspicious behaviors are detected, Microsoft Defender Antivirus monitors and sends those suspicious behaviors and their process trees to the cloud protection service. Machine learning differentiates between malicious applications and good behaviors within milliseconds and classifies each artifact. As soon as an artifact is found to be malicious, it's blocked on the device.

Whenever a suspicious behavior is detected, an alert is generated and is visible in the Microsoft 365 Defender portal

Client behavioral blocking is effective because it not only helps prevent an attack from starting, but it can help stop an attack that has begun executing. With feedback-loop blocking (another capability of behavioral blocking and containment), attacks are prevented on other devices in your organization.

### Behavior-based detections

Behavior-based detections are named according to the MITRE ATT&CK Matrix for Enterprise. The naming convention helps identify the attack stage where malicious behavior was observed:

| Tactic | Detection threat name  |
|---|---|
| Initial Access | Behavior:Win32/InitialAccess.*!ml  |
| Execution | Behavior:Win32/Execution.*!ml  |
| Persistence | Behavior:Win32/Persistence.*!ml  |
| Privilege Escalation | Behavior:Win32/PrivilegeEscalation.*!ml  |
| Defense Evasion | Behavior:Win32/DefenseEvasion.*!ml  |
| Credential Access | Behavior:Win32/CredentialAccess.*!ml  |
| Discovery | Behavior:Win32/Discovery.*!ml  |
| Lateral Movement | Behavior:Win32/LateralMovement.*!ml  |
| Collection | Behavior:Win32/Collection.*!ml  |
| Command and Control | Behavior:Win32/CommandAndControl.*!ml  |
| Exfiltration | Behavior:Win32/Exfiltration.*!ml  |
| Impact | Behavior:Win32/Impact.*!ml  |
| Uncategorized | Win32/Generic.*!ml |

## Feedback-loop blocking

Feedback-loop blocking, also referred to as rapid protection, is a component of behavioral blocking and containment capabilities in Microsoft Defender for Endpoint. With feedback-loop blocking, devices across your organization are better protected from attacks.

### How feedback-loop blocking works

When a suspicious behavior or file is detected, such as by Microsoft Defender Antivirus, information about that artifact is sent to multiple classifiers. The rapid protection loop engine inspects and correlates the information with other signals to arrive at a decision as to whether to block a file. Checking and classifying artifacts happens quickly. It results in rapid blocking of confirmed malware and drives protection across the entire ecosystem.

With rapid protection in place, an attack can be stopped on a device, other devices in the organization, and devices in other organizations, as an attack attempts to broaden its foothold.

## Endpoint detection and response in block mode

When endpoint detection and response (EDR) in block mode is turned on, Defender for Endpoint blocks malicious artifacts or behaviors that are observed through post-breach protection. EDR in block mode works behind the scenes to remediate malicious artifacts that are detected post-breach.

[Microsoft Defender for Endpoint EDR in block mode](https://www.microsoft.com/en-us/videoplayer/embed/RE4HjW2?rel=0&postJsllMsg=true)

EDR in block mode is also integrated with threat & vulnerability management. Your organization's security team will get a security recommendation to turn EDR in block mode on if it isn't already enabled.

### What happens when something is detected?

When EDR in block mode is turned on and a malicious artifact is detected, blocking and remediation actions are taken. You'll see detection status as Blocked or Prevented as completed actions in the Action Center.

The following image shows an instance of unwanted software that was detected and blocked through EDR in block mode:

[![Screen shot of an E D R in Block Mode Alert.](https://learn.microsoft.com/en-us/training/wwl-sci/perform-device-investigations-microsoft-defender-for-endpoints/media/endpoint-detection-response-block-mode-detection.png)](https://learn.microsoft.com/en-us/training/wwl-sci/perform-device-investigations-microsoft-defender-for-endpoints/media/endpoint-detection-response-block-mode-detection.png#lightbox)
# Detect devices with device discovery

Protecting your environment requires taking inventory of the devices that are in your network. However, mapping devices in a network can often be expensive, challenging, and time-consuming.

Microsoft Defender for Endpoint provides a device discovery capability that helps you find unmanaged devices connected to your corporate network without the need for extra appliances or cumbersome process changes. Device discovery uses onboarded endpoints, in your network to collect, probe, or scan your network to discover unmanaged devices. The device discovery capability allows you to discover:

-   Enterprise endpoints (workstations, servers and mobile devices) that aren't yet onboarded to Microsoft Defender for Endpoint
-   Network devices like routers and switches
-   IoT devices like printers and cameras

Unknown and unmanaged devices introduce significant risks to your network - whether it's an unpatched printer, network devices with weak security configurations, or a server with no security controls. Once devices are discovered, you can:

-   Onboard unmanaged endpoints to the service, increasing the security visibility on them.
-   Reduce the attack surface by identifying and assessing vulnerabilities, and detecting configuration gaps.

To discover devices watch the: [Discover Devices Video](https://www.youtube.com/watch?v=TCDxICrZQa8).

To assess and Onboard Unmanaged Devices:

[Microsoft Defender for Endpoint Assessing and onboard unmanaged devices](https://www.microsoft.com/en-us/videoplayer/embed/RE4RwQz?postJsllMsg=true)

With this capability, a security recommendation to onboard devices to Microsoft Defender for Endpoint is available as part of the existing threat and vulnerability management experience.

Discovery methods You can choose the discovery mode to be used by your onboarded devices. The mode controls the level of visibility you can get for unmanaged devices in your corporate network.

There are two modes of discovery available:

-   Basic discovery: In this mode, endpoints will passively collect events in your network and extract device information from them. Basic discovery uses the SenseNDR.exe binary for passive network data collection and no network traffic will be initiated. Endpoints will extract data from every network traffic that is seen by an onboarded device. With basic discovery, you'll only gain limited visibility of unmanaged endpoints in your network.
    
-   Standard discovery (recommended): This mode allows endpoints to actively find devices in your network to enrich collected data and discover more devices - helping you build a reliable and coherent device inventory. In addition to devices that were observed using the passive method, standard mode also uses common discovery protocols that use multicast queries in the network to find even more devices. Standard mode uses smart, active probing to discover additional information about observed devices to enrich existing device information. When Standard mode is enabled, minimal, and negligible network activity generated by the discovery sensor might be observed by network monitoring tools in your organization.
    

Devices that have been discovered but haven't yet been onboarded and secured by Microsoft Defender for Endpoint will be listed in the device inventory within the Computers and Mobile tab.

To assess these devices, you can use a filter in the device inventory list called Onboarding status, which can have any of the following values:

-   Onboarded: The endpoint is onboarded to Microsoft Defender for Endpoint.
-   Can be onboarded: The endpoint was discovered in the network and the Operating System was identified as one that is supported by Microsoft Defender for Endpoint, but it is not currently onboarded. We highly recommend onboarding these devices.
-   Unsupported: The endpoint was discovered in the network but is not supported by Microsoft Defender for Endpoint.
-   Insufficient info: The system could not determine the supportability of the device. Enabling standard discovery on more devices in the network can enrich the discovered attributes.

# Knowledge check

1. The security operations analyst has found an interesting event, what should be done to mark it for further review?

Tag

Highlight

[X] Flag

Correct. You can Flag events.

2. Which Behavioral blocking can be used with third-party antivirus?

Client behavior blocking.

[X] EDR in block mode

Correct. EDR in Block allows for blocking even when third party AV is used.

Feedback-loop blocking

Incorrect. This is used with Defender AV.

3. A Windows 10 Device doesn't appear in the device list, what could be the problem?

The Device was renamed.

Incorrect. Renaming the device has no impact on the Device list.

The Device is missing the latest KBs

[X] The Device hasn't had alerts in the past 30 days.

Correct. You can adjust the time setting to find the device.

# Summary and resources

You should have learned how Microsoft Defender for Endpoint provides detailed device information, including forensics information.

You should now be able to:

-   Use the device page in Microsoft Defender for Endpoint
-   Describe device forensics information collected by Microsoft Defender for Endpoint
-   Describe behavioral blocking by Microsoft Defender for Endpoint

## Learn more

You can learn more by reviewing the following.

[Become a Microsoft Defender for Endpoint Ninja](https://nam06.safelinks.protection.outlook.com/?url=https%3A%2F%2Ftechcommunity.microsoft.com%2Ft5%2Fmicrosoft-defender-for-endpoint%2Fbecome-a-microsoft-defender-atp-ninja%2Fba-p%2F1515647&data=04%7C01%7Cbneeb%40microsoft.com%7C70ade848411b4dbb43bd08d8b1e6e51e%7C72f988bf86f141af91ab2d7cd011db47%7C1%7C0%7C637454952552234995%7CUnknown%7CTWFpbGZsb3d8eyJWIjoiMC4wLjAwMDAiLCJQIjoiV2luMzIiLCJBTiI6Ik1haWwiLCJXVCI6Mn0%3D%7C1000&sdata=%2FfCCxsoJg5FwJwrgGstqLGYHuABKDTOlvmPbT3zVQ6w%3D&reserved=0%3Fazure-portal%3Dtrue)

[Microsoft Tech Community Security Webinars](https://techcommunity.microsoft.com/t5/microsoft-security-and/security-community-webinars/ba-p/927888)