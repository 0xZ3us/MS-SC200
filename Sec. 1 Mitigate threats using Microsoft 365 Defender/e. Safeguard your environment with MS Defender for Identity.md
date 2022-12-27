# Introduction to Microsoft Defender for Identity

**Microsoft Defender for Identity** is a cloud-based security solution that leverages your on-premises Active Directory signals to identify, detect, and investigate advanced threats, compromised identities, and malicious insider actions directed at your organization.

![The benefits of Microsoft Defender for Identity.](https://learn.microsoft.com/en-us/training/m365/m365-threat-safeguard/media/azure-benefits.png)

Microsoft Defender for Identity provides the following benefits:

-   Monitor users, entity behavior, and activities with learning-based analytics
-   Protect user identities and credentials stored in Active Directory
-   Identify and investigate suspicious user activities and advanced attacks throughout the kill chain
-   Provide clear incident information on a simple timeline for fast triage

## Monitor and profile user behavior and activities

Microsoft Defender for Identity monitors and analyzes user activities and information across your network, such as permissions and group membership. It then creates a behavioral baseline for each user. Microsoft Defender for Identity then identifies anomalies with adaptive built-in intelligence, giving you insights into suspicious activities and events, revealing the advanced threats, compromised users, and insider threats facing your organization. Microsoft Defender for Identity's proprietary sensors monitor organizational domain controllers, providing a comprehensive view for all user activities from every device.

[![Overview of user activities.](https://learn.microsoft.com/en-us/training/m365/m365-threat-safeguard/media/user-activities-view.png)](https://learn.microsoft.com/en-us/training/m365/m365-threat-safeguard/media/user-activities-view-magnify.png#lightbox)

## Protect user identities and reduce the attack surface

Microsoft Defender for Identity provides you invaluable insights on identity configurations and suggested security best-practices. Through security reports and user profile analytics, Microsoft Defender for Identity helps dramatically reduce your organizational attack surface, making it harder to compromise user credentials and advance an attack. Microsoft Defender for Identity's visual Lateral Movement Paths help you quickly understand exactly how an attacker can move laterally inside your organization to compromise sensitive accounts and assists in preventing those risks in advance. Microsoft Defender for Identity security reports help identify users and devices that authenticate using clear-text passwords and provide additional insights to improve your organizational security posture and policies.

![Security Report user improvement suggestions.](https://learn.microsoft.com/en-us/training/m365/m365-threat-safeguard/media/security-report-improvement-action-cropped.png)

## Identify suspicious activities and advanced attacks across the cyber-attack kill-chain

Typically, attacks are launched against any accessible entity, such as a low-privileged user, and then quickly move laterally until the attacker gains access to valuable assets – such as sensitive accounts, domain administrators, and highly sensitive data. Microsoft Defender for Identity has a large range of detections across the Kill-chain from **reconnaissance** through to **compromised credentials** to **lateral movements** and **domain dominance**.

![Lateral movement across the kill chain.](https://learn.microsoft.com/en-us/training/m365/m365-threat-safeguard/media/lateral-movement-across-kill-chain.png)

For example, in the reconnaissance stage, LDAP reconnaissance is used by attackers to gain critical information about the domain environment. Information that helps attackers map the domain structure, and identify privileged accounts for use later. This detection is triggered based on computers performing suspicious LDAP enumeration queries or queries targeting sensitive groups.

Brute force attacks are a common way to compromise credentials. This is when an attacker attempts to authenticate with multiple passwords on different accounts until a correct password is found or by using one password in a large-scale password spray that works for at least one account. Once found, the attacker logs in using the authenticated account. Microsoft Defender for Identity can detect this when it notices multiple authentication failures occurring using Kerberos, NTLM, or use of a password spray.

The next stage is when attackers attempt to move laterally through your environment, using pass-the-ticket, for example. Pass-the-ticket is a lateral movement technique in which attackers steal a Kerberos ticket from one computer and use it to gain access to another computer by reusing the stolen ticket. In this detection, a Kerberos ticket is being used on two (or more) different computers.

Ultimately, attackers want to establish domain dominance. One method, for example is the DCShadow attack. This attack is designed to change directory objects using malicious replication. This attack can be performed from any machine by creating a rogue domain controller using a replication process. If this occurs, Microsoft Defender for Identity triggers an alert when a machine in the network tries to register as a rogue domain controller.

This is not the complete set of detections, but it shows the breadth of detections Microsoft Defender for Identity covers.

### Explore how to detect suspicious activities and potential attacks with Microsoft Defender for Identity

View a [video version](https://www.microsoft.com/videoplayer/embed/RE4Gq4n) of the interactive guide (captions available in more languages).

Be sure to click the full-screen option in the video player. When you're done, use the **Back** arrow in your browser to come back to this page.

# Configure Microsoft Defender for Identity sensors

At a high level, the following steps are required to enable Microsoft Defender for Identity:

1.  Create an instance on Microsoft Defender for Identity management portal.
2.  Specify an on-premises AD service account in the Microsoft Defender for Identity portal.
3.  Download and install the sensor package.
4.  Install the Microsoft Defender for Identity sensor on all domain controllers.
5.  Integrate your VPN solution (optional).
6.  Exclude the sensitive accounts you've listed during the design process.
7.  Configure the required permissions for the sensor to make SAM-R calls.
8.  Configure integration with Microsoft Defender for Cloud Apps.
9.  Configure integration with Microsoft 365 Defender (optional).

The following diagram shows the Microsoft Defender for Identity architecture. In this unit, we will discuss how to configure the Microsoft Defender for Identity Sensor.

![Microsoft Defender for Identity architecture](https://learn.microsoft.com/en-us/training/m365/m365-threat-safeguard/media/defender-identity-architecture-topology.png)

Installed directly on your domain controllers, the Microsoft Defender for Identity sensor accesses the event logs it requires directly from the domain controller. After the logs and network traffic are parsed by the sensor, Microsoft Defender for Identity sends only the parsed information to the Microsoft Defender for Identity cloud service (only a percentage of the logs are sent).

The Microsoft Defender for Identity sensor has the following core functionality:

-   Capture and inspect domain controller network traffic (local traffic of the domain controller)
-   Receive Windows events directly from the domain controllers
-   Receive RADIUS accounting information from your VPN provider
-   Retrieve data about users and computers from the Active Directory domain
-   Perform resolution of network entities (users, groups, and computers)
-   Transfer relevant data to the Microsoft Defender for Identity cloud service

The Microsoft Defender for Identity sensor has the following requirements:

-   KB4487044 is installed on Server 2019. Microsoft Defender for Identity sensors already installed on 2019 servers without this update will be automatically stopped.
-   The Microsoft Defender for Identity sensor supported domain controller OS list:
    -   Windows Server 2008 R2 SP1 (not including Server Core)
    -   Windows Server 2012
    -   Windows Server 2012 R2
    -   Windows Server 2016 (including Windows Server Core but not Windows Nano Server)
    -   Windows Server 2019 (including Windows Core but not Windows Nano Server)
-   The domain controller can be a read-only domain controller (RODC).
-   10 GB of disk space is recommended. This includes space needed for the Microsoft Defender for Identity binaries, Microsoft Defender for Identity logs, and performance logs.
-   The Microsoft Defender for Identity sensor requires a minimum of two cores and 6 GB of RAM installed on the domain controller.
-   Power option of the Microsoft Defender for Identity sensor to high performance.
-   Microsoft Defender for Identity sensors can be deployed on domain controllers of various loads and sizes, depending on the amount of network traffic to and from the domain controllers, and the amount of resources installed.
-   When running as a virtual machine, dynamic memory or any other memory ballooning feature is not supported.

### To install the Microsoft Defender for Identity sensor

1.  Download and extract the sensor file. Run **Microsoft Defender for Identity sensor setup.exe** and follow the setup wizard.
2.  On the Welcome page, select your language and click **Next**.

![Install steps: Choose Language.](https://learn.microsoft.com/en-us/training/m365/m365-threat-safeguard/media/install-choose-language.png)

3.  The installation wizard automatically checks if the server is a domain controller or a dedicated server. If it's a domain controller, the Microsoft Defender for Identity sensor is installed. If it's a dedicated server, the Microsoft Defender for Identity standalone sensor is installed. For example, for a Microsoft Defender for Identity sensor, the following screen is displayed to let you know that a Microsoft Defender for Identity sensor is installed on your dedicated server:
    
    ![Install steps: Determine server type.](https://learn.microsoft.com/en-us/training/m365/m365-threat-safeguard/media/install-server-type.png)
    
4.  Under **Configure the sensor**, enter the installation path and the access key, based on your environment:
    
    -   **Installation path**: The location where the Microsoft Defender for Identity sensor is installed. By default, the path is **%programfiles%\Microsoft Defender for Identity sensor**. Leave the default value.
    -   **Access key**: Retrieved from the Microsoft Defender for Identity portal.
    
    ![Install steps: Configure the sensor.](https://learn.microsoft.com/en-us/training/m365/m365-threat-safeguard/media/install-configure-sensor.png)
    
5.  Click **Install**.
    

After the Microsoft Defender for Identity sensor is installed, do the following to configure Microsoft Defender for Identity sensor settings:

1.  Click **Launch** to open your browser and sign into the Microsoft Defender for Identity portal.
    
2.  In the Microsoft Defender for Identity portal, go to **Configuration**. Under the System section, select **Sensors**.
    
    [![Install steps: Select sensors in Microsoft Defender for Office 365 portal.](https://learn.microsoft.com/en-us/training/m365/m365-threat-safeguard/media/install-select-sensors.png)](https://learn.microsoft.com/en-us/training/m365/m365-threat-safeguard/media/install-select-sensors-magnify.png#lightbox)
    
3.  Click on the sensor you want to configure and enter the following information:
    
    -   **Description**: Enter a description for the Microsoft Defender for Identity sensor (optional).
        
    -   **Domain Controllers** (FQDN) (required for the Microsoft Defender for Identity standalone sensor, this can't be changed for the Microsoft Defender for Identity sensor): Enter the complete FQDN of your domain controller and click the **plus sign** to add it to the list. For example, dc01.contoso.com.
        
        The following information applies to the servers you enter in the Domain Controllers list:
        
        -   All domain controllers whose traffic is being monitored via port mirroring by the Microsoft Defender for Identity standalone sensor must be listed in the Domain Controllers list. If a domain controller isn't listed in the Domain Controllers list, detection of suspicious activities might not function as expected.
        -   At least one domain controller in the list should be a global catalog. This enables Microsoft Defender for Identity to resolve computer and user objects in other domains in the forest.
    -   **Capture Network adapters** (required):
        
        -   For Microsoft Defender for Identity sensors, all network adapters that are used for communication with other computers in your organization.
        -   For Microsoft Defender for Identity standalone sensor on a dedicated server, select the network adapters that are configured as the destination mirror port. These network adapters receive the mirrored domain controller traffic.
    
    ![Install steps: Enter information to configure sensor.](https://learn.microsoft.com/en-us/training/m365/m365-threat-safeguard/media/install-configure-sensor-info.png)
    
4.  Click **Save**.

# Review compromised accounts of data

Microsoft Defender for Identity security alerts explain suspicious activities detected by Microsoft Defender for Identity sensors on your network, and the actors and computers involved in each threat. Alert evidence lists contain direct links to the involved users and computers, to help make your investigations easy and direct.

Microsoft Defender for Identity security alerts are divided into the following categories or phases, like the phases seen in a typical cyber-attack kill chain:

-   Reconnaissance phase alerts
-   Compromised credential phase alerts
-   Lateral movement phase alerts
-   Domain dominance phase alerts
-   Exfiltration phase alerts

Each Microsoft Defender for Identity security alert includes:

-   **Alert title.** Official Microsoft Defender for Identity name of the alert.
-   **Description.** Brief explanation of what happened.
-   **Evidence.** Additional relevant information and related data about what happened to help in the investigation process.
-   **Excel download.** Detailed Excel download report for analysis

![Microsoft Defender for Identity security alert.](https://learn.microsoft.com/en-us/training/m365/m365-threat-safeguard/media/security-alert.png)

Alerts can also be viewed within Microsoft Defender for Cloud Apps:

[![Microsoft Defender for Cloud Apps alert.](https://learn.microsoft.com/en-us/training/m365/m365-threat-safeguard/media/cloud-app-security-alerts.png)](https://learn.microsoft.com/en-us/training/m365/m365-threat-safeguard/media/cloud-app-security-alerts-magnify.png#lightbox)

The following scenario describes an investigation into an attacker gaining administrator access to the domain controller and compromising the Active Directory domain and forest.

The first alert we notice in the Defender for Cloud Apps portal shows **User and IP address reconnaissance** (SMB). Clicking into this alert, we see (under Description) that a user was able to learn the IP addresses of two accounts by enumerating SMB sessions on the domain controller.

[![User and I P address reconnaissance.](https://learn.microsoft.com/en-us/training/m365/m365-threat-safeguard/media/user-ip-address-reconnaissance.png)](https://learn.microsoft.com/en-us/training/m365/m365-threat-safeguard/media/user-ip-address-reconnaissance-magnify.png#lightbox)

Within the alert, we can also find the activity log, which shows more information about the command that was run.

[![Activity log.](https://learn.microsoft.com/en-us/training/m365/m365-threat-safeguard/media/activity-log.png)](https://learn.microsoft.com/en-us/training/m365/m365-threat-safeguard/media/activity-log-magnify.png#lightbox)

Back in the Alerts overview, we can see a more recent alert pointing to an **overpass-the-hash attack**.

[![Alert: Overpass-the-hash-attack.](https://learn.microsoft.com/en-us/training/m365/m365-threat-safeguard/media/overpass-hash-attack.png)](https://learn.microsoft.com/en-us/training/m365/m365-threat-safeguard/media/overpass-hash-attack-magnify.png#lightbox)

Opening the suspected overpass-the-hash-attack (Kerberos) alert, we see evidence that the user account was part of a lateral movement path.

[![Open the suspected attack alert.](https://learn.microsoft.com/en-us/training/m365/m365-threat-safeguard/media/open-suspected-attack.png)](https://learn.microsoft.com/en-us/training/m365/m365-threat-safeguard/media/open-suspected-attack-magnify.png#lightbox)

The next alert shows a **Suspected identity theft (pass-the-ticket)**.

[![Pass-the-ticket alert.](https://learn.microsoft.com/en-us/training/m365/m365-threat-safeguard/media/pass-ticket-alert.png)](https://learn.microsoft.com/en-us/training/m365/m365-threat-safeguard/media/pass-ticket-alert-magnify.png#lightbox)

Microsoft Defender for Identity has detected theft of a ticket from a domain administrator to the infiltrated PC. The Defender for Cloud Apps portal shows exactly which resources were accessed using the stolen tickets.

[![More information on the pass-the-ticket alert.](https://learn.microsoft.com/en-us/training/m365/m365-threat-safeguard/media/alert-pass-ticket.png)](https://learn.microsoft.com/en-us/training/m365/m365-threat-safeguard/media/alert-pass-ticket-magnify.png#lightbox)

In the next alert, we see that the stolen credentials were used to run a remote command on the domain controller.

[![Alert showing remote code execution attemptl.](https://learn.microsoft.com/en-us/training/m365/m365-threat-safeguard/media/alert-remote-code-execution.png)](https://learn.microsoft.com/en-us/training/m365/m365-threat-safeguard/media/alert-remote-code-execution-magnify.png#lightbox)

Looking into the Activity Log for the alert, we see that the command was to create a new user within the Administrators group.

[![Command used to create a new user.](https://learn.microsoft.com/en-us/training/m365/m365-threat-safeguard/media/create-new-user.png)](https://learn.microsoft.com/en-us/training/m365/m365-threat-safeguard/media/create-new-user-magnify.png#lightbox)

From all the previous alerts, we suspect that an attacker has:

-   Infiltrated a PC.
-   Used the PC to determine IP addresses of other users' PCs, one of which belongs to a domain administrator.
-   Performed an overpass-the-hash attack by stealing the NTLM hash from another user who previously authenticated to the infiltrated PC to access any resource the user has permissions for. (In this case, local admin rights to IP addresses previously exposed)
-   Used the newly stolen credentials to gain access to the domain administrator's PC.
-   Used their access to the domain administrator's PC to steal the identity of the domain administrator.
-   Used the domain administrator's identity to access the domain controller, and created a new user account with domain administrative permissions.

With domain administrative permissions, the attacker has effectively compromised the environment. Now they are free to perform any number of attacks, such as a Skeleton Key attack.

### Explore how to investigate and respond to attacks with Microsoft Defender for Identity

View a [video version](https://www.microsoft.com/videoplayer/embed/RE4GiZJ) of the interactive guide (captions available in more languages).

Be sure to click the full-screen option in the video player. When you're done, use the **Back** arrow in your browser to come back to this page.

# Integrate with other Microsoft tools

[![Integration architecture.](https://learn.microsoft.com/en-us/training/m365/m365-threat-safeguard/media/integration-architecture.png)](https://learn.microsoft.com/en-us/training/m365/m365-threat-safeguard/media/integration-architecture-magnify.png#lightbox)

The Microsoft Defender for Identity cloud service runs on Azure infrastructure and is currently deployed in the US, Europe, and Asia. Microsoft Defender for Identity cloud service is connected to Microsoft's intelligent security graph. This enables Microsoft Defender for Identity to integrate with Microsoft Defender for Cloud Apps, as part of a Microsoft 365 Defender monitoring strategy.

Once integrated into Microsoft Defender for Cloud Apps, you'll be able to see on-premises activities for all the users in your organization. You will also get advanced insights on your users that combine alerts and suspicious activities across your cloud and on-premises environments. Additionally, policies from Microsoft Defender for Identity will appear on the Defender for Cloud Apps policies page. The following screenshot shows Microsoft Defender for Identity reporting within Defender for Cloud Apps.

[![Microsoft Defender for Identity reporting within Microsoft Defender for Cloud Apps.](https://learn.microsoft.com/en-us/training/m365/m365-threat-safeguard/media/azure-reporting-cloud-app-security.png)](https://learn.microsoft.com/en-us/training/m365/m365-threat-safeguard/media/azure-reporting-cloud-app-security-magnify.png#lightbox)

[Microsoft Cloud App Security Video](https://www.microsoft.com/en-us/videoplayer/embed/RE4CVTT?postJsllMsg=true)

Microsoft Defender for Identity also enables you to integrate Microsoft Defender for Identity with Microsoft Defender for Endpoint, for an even more complete threat protection solution. While Microsoft Defender for Identity monitors the traffic on your domain controllers, Microsoft Defender for Endpoint monitors your endpoints, together providing a single interface from which you can protect your environment. Once Microsoft Defender for Endpoint and Microsoft Defender for Identity are integrated, you can click on an endpoint to view Microsoft Defender for Identity alerts in the Microsoft Defender for Endpoint portal.

[![Windows Defender Security Center.](https://learn.microsoft.com/en-us/training/m365/m365-threat-safeguard/media/windows-defender-security-center.png)](https://learn.microsoft.com/en-us/training/m365/m365-threat-safeguard/media/windows-defender-security-center-magnify.png#lightbox)

Having this level of insight into system running processes allows an analyst to locate event sequences leading to a compromise of the network. In the screenshot below, there are high severity alerts pointing to malware being installed on the system.

[![High severity malware alert.](https://learn.microsoft.com/en-us/training/m365/m365-threat-safeguard/media/high-severity-malware-alert.png)](https://learn.microsoft.com/en-us/training/m365/m365-threat-safeguard/media/high-severity-malware-alert-magnify.png#lightbox)

Clicking into the alert verifies that a Pass-The-Hash (PtH) attack occurred using the tool Mimikatz. Under actions for the alert, we can also review a timeline of events surrounding the credential theft.

[![Review a timeline of events surrounding the credential theft.](https://learn.microsoft.com/en-us/training/m365/m365-threat-safeguard/media/event-timeline.png)](https://learn.microsoft.com/en-us/training/m365/m365-threat-safeguard/media/event-timeline-magnify.png#lightbox)

# Summary and knowledge check

In this module, you learned about the Microsoft Defender for Identity component of Microsoft 365 Defender.

Now that you have completed this module, you should be able to:

-   Define the capabilities of Microsoft Defender for Identity.
-   Understand how to configure Microsoft Defender for Identity sensors.
-   Explain how Microsoft Defender for Identity can remediate risks in your environment.

## Check your knowledge
1. Microsoft Defender for Identity requires an on-premises Active Directory environment.
[X] True
	Correct! Microsoft Defender for Identity is a cloud-based security solution that leverages your on-premises Active Directory.
False
	Incorrect. Microsoft Defender for Identity is a cloud-based security solution that requires an on-premises Active Directory.

2. Which of the following describes advanced threats detected by Microsoft Defender for Identity?
[X] Reconnaissance
	Correct! Microsoft Defender for Identity can identify rogue users and attackers' attempts to gain information such as usernames, users' group membership, IP addresses assigned to devices, resources, and more, using various methods.
Vertical movements
Bitcoin mining

3. Which of the following is **not** a supported integration for Microsoft Defender for Identity?
Microsoft Defender for Endpoint
Microsoft Defender for Cloud Apps
[X] Intune
	Correct! Currently, there is no supported integration with Microsoft Defender for Identity and Microsoft Intune.