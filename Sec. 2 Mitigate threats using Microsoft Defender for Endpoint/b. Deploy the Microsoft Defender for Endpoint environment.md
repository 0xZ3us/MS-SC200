# Introduction

Deploying the Microsoft Defender for Endpoint environment involves configuring your tenant, onboarding your devices, and configuring security team access.

You're a Security Operations Analyst working at a company that is implementing Microsoft Defender for Endpoint. Your manager plans to onboard a few devices to provide insight into required changes to the SecOps team response procedures.

You start by initializing the Defender for Endpoint environment—next, you onboard the initial devices for your deployment by running the onboarding script on the devices. You configure security for the environment. Next, you create Device groups and assign the appropriate devices.

After completing this module, you'll be able to:

-   Create a Microsoft Defender for Endpoint environment
-   Onboard devices to be monitored by Microsoft Defender for Endpoint
-   Configure Microsoft Defender for Endpoint environment settings

# Create your environment

When accessing your Microsoft 365 Defender portal settings for Endpoints for the first time, you'll be able to configure many attributes. You must be a global administrator or security administrator for the tenant. On the Set-up preferences page, you can set the:

**Data storage location** - Determine where you want to be primarily hosted: US, EU, or UK. You can't change the location after this set up and Microsoft won't transfer the data from the specified geolocation.

**Data retention** - The default is six months.

**Enable preview features** - The default is on, can be changed later.

To access the Microsoft 365 Defender portal settings for Endpoints do the following action:

1.  Go to ([https://security.microsoft.com](https://security.microsoft.com/))
2.  Select **Settings**.
3.  Select **Endpoints**.

## Network configuration

If the organization doesn't require the endpoints to use a Proxy to access the Internet, the following configuration isn't required.

The Microsoft Defender for Endpoint sensor requires Microsoft Windows HTTP (WinHTTP) to report sensor data and communicate with the Microsoft Defender for Endpoint service. The embedded Microsoft Defender for Endpoint sensor runs in the system context using the LocalSystem account. The sensor uses Microsoft Windows HTTP Services (WinHTTP) to enable communication with the Microsoft Defender for Endpoint cloud service. The WinHTTP configuration setting is independent of the Windows Internet (WinINet) internet browsing proxy settings and can only discover a proxy server by using the following discovery methods:

Autodiscovery methods:

-   Transparent proxy
    
-   Web Proxy Autodiscovery Protocol (WPAD)
    

If a Transparent proxy or WPAD has been implemented in the network topology, there's no need for special configuration settings.

# Understand operating systems compatibility and features

Microsoft Defender for Endpoint is available on the following Operating Systems:

-   Windows
-   macOS
-   Linux
-   Android
-   iOS

## Windows

Supported Windows versions

-   Windows 7 SP1 Enterprise (Requires ESU for support.)
-   Windows 7 SP1 Pro (Requires ESU for support.)
-   Windows 8.1 Enterprise
-   Windows 8.1 Pro
-   Windows 11 Enterprise
-   Windows 11 Education
-   Windows 11 Pro
-   Windows 11 Pro Education
-   Windows 10 Enterprise
-   Windows 10 Enterprise LTSC 2016 (or later)
-   Windows 10 Enterprise IoT
-   Windows 10 Education
-   Windows 10 Pro
-   Windows 10 Pro Education
-   Windows server
-   Windows Server 2008 R2 SP1 (Requires ESU for support)
-   Windows Server 2012 R2
-   Windows Server 2016
-   Windows Server, version 1803 or later
-   Windows Server 2019
-   Windows Server 2022
-   Windows Virtual Desktop

## Microsoft Defender for Endpoint on macOS

Microsoft Defender for Endpoint on macOS offers antivirus, endpoint detection and response (EDR), and vulnerability management capabilities for the three latest released versions of macOS. Customers can deploy and manage the solution through Microsoft Endpoint Manager and Jamf. Just like with Microsoft Office applications on macOS, Microsoft AutoUpdate is used to manage Microsoft Defender for Endpoint on Mac updates.

## Microsoft Defender for Endpoint on Linux

Microsoft Defender for Endpoint on Linux offers preventative antivirus (AV), endpoint detection and response (EDR), and vulnerability management capabilities for Linux servers. This includes a full command line experience to configure and manage the agent, initiate scans, and manage threats. We support recent versions of the six most common Linux Server distributions: RHEL 7.2+, CentOS Linux 7.2+, Ubuntu 16 LTS, or higher LTS, SLES 12+, Debian 9+, and Oracle Linux 7.2. Microsoft Defender for Endpoint on Linux can be deployed and configured using Puppet, Ansible, or using your existing Linux configuration management tool.

## Microsoft Defender for Endpoint on Android

Microsoft Defender for Endpoint on Android is our mobile threat defense solution for devices running Android 6.0 and higher. Both Android Enterprise (Work Profile) and Device Administrator modes are supported. On Android, we offer web protection, which includes anti-phishing, blocking of unsafe connections, and setting of custom indicators. The solution scans for malware and potentially unwanted applications (PUA) and offers more breach prevention capabilities through integration with Microsoft Endpoint Manager and Conditional Access.

## Microsoft Defender for Endpoint on iOS

Microsoft Defender for Endpoint on iOS is our mobile threat defense solution for devices running iOS 11.0 and higher. Devices that are registered within a customer's tenant (enrolled or unenrolled) are supported. Both supervised and unsupervised enrolled devices are supported. On iOS, we offer web protection, which includes anti-phishing, blocking unsafe connections and setting custom indicators, and jailbreak detection.

# Onboard devices

## Initialize the Microsoft Defender for Endpoint environment

When accessing your Microsoft 365 Defender portal settings for Endpoints for the first time, you'll be able to configure many attributes. You must be a global administrator or security administrator for the tenant. On the Set-up preferences page, you can set the:

**Data storage location** - Determine where you want to be primarily hosted: US, EU, or UK. You can't change the location after this set up and Microsoft won't transfer the data from the specified geolocation.

**Data retention** - The default is six months.

**Enable preview features** - The default is on, can be changed later.

To access the Microsoft 365 Defender portal settings for Endpoints do the following action:

1.  Go to ([https://security.microsoft.com](https://security.microsoft.com/))
2.  Select **Settings**.
3.  Select **Endpoints**.

## Network configuration

If the organization doesn't require the endpoints to use a Proxy to access the Internet, the following configuration isn't required.

The Microsoft Defender for Endpoint sensor requires Microsoft Windows HTTP (WinHTTP) to report sensor data and communicate with the Microsoft Defender for Endpoint service. The embedded Microsoft Defender for Endpoint sensor runs in the system context using the LocalSystem account. The sensor uses Microsoft Windows HTTP Services (WinHTTP) to enable communication with the Microsoft Defender for Endpoint cloud service. The WinHTTP configuration setting is independent of the Windows Internet (WinINet) internet browsing proxy settings and can only discover a proxy server by using the following discovery methods:

Autodiscovery methods:

-   Transparent proxy
    
-   Web Proxy Autodiscovery Protocol (WPAD)
    

If a Transparent proxy or WPAD has been implemented in the network topology, there's no need for special configuration settings.

## Onboard devices

You'll need to go to the onboarding section of the Microsoft 365 Defender portal to onboard any of the supported devices. Depending on the device, you'll be guided with appropriate steps and provided management and deployment tool options suitable for the device.

In general, to onboard devices to the service:

-   Verify that the device fulfills the minimum requirements
    
-   Depending on the device, follow the configuration steps provided in the onboarding section of the Microsoft 365 Defender portal
    
-   Use the appropriate management tool and deployment method for your devices
    
-   Run a detection test to verify that the devices are properly onboarded and reporting to the service
    

In Settings, Endpoints, Device management, Onboarding select operating system dropdown to see the supported options.

[![Screenshot of the Supported Operating Systems dropdown.](https://learn.microsoft.com/en-us/training/wwl-sci/deploy-microsoft-defender-for-endpoints-environment/media/onboarding.png)](https://learn.microsoft.com/en-us/training/wwl-sci/deploy-microsoft-defender-for-endpoints-environment/media/onboarding.png#lightbox)

After you select the appropriate operating system option, the supported deployment options are outlined. Here's a list of the Windows 10 supported deployment options:

-   Group Policy
    
-   Microsoft Endpoint Configuration Manager current branch and later
    
-   Mobile Device Management (including Microsoft Intune)
    
-   Local script (for up to 10 devices)
    
-   VDI onboarding script for non-persistent devices
    
-   System Center Configuration Manager 2012 / 2012 R2 / 1511 /1602
    

[![Screenshot of the Windows 10 Deployment options.](https://learn.microsoft.com/en-us/training/wwl-sci/deploy-microsoft-defender-for-endpoints-environment/media/onboard-deployment.png)](https://learn.microsoft.com/en-us/training/wwl-sci/deploy-microsoft-defender-for-endpoints-environment/media/onboard-deployment.png#lightbox)

As you can see, there are many configuration options.

## Offboarding devices

In Settings, Endpoints, Device Management, Offboarding, select operating system dropdown to see the direction to offboard devices.

# Manage access

Using role-based access control (RBAC), you can create roles and groups within your security operations team to grant appropriate access to the portal. Based on the roles and groups you create, you have fine-grained control over what users with access to the portal can see and do. The following video explains the use of Role-Based Access Control (RBAC) and Device Groups (Machine Groups).

[Microsoft Defender for Endpoint Role-based access control video](https://www.microsoft.com/en-us/videoplayer/embed/RE4bJ2a?rel=0&postJsllMsg=true)

Defender for Endpoint RBAC is designed to support your tier or role-based model of choice. It gives you granular control over what roles can see, devices they can access, and actions they can take. The RBAC framework is centered around the following controls:

-   Control who can take specific actions
    
    -   Create custom roles and control what Defender for Endpoint capabilities they can access with granularity.
-   Control who can see information on a specific device group or groups
    
    -   Create device groups by specific criteria such as names, tags, domains, and others, then grant role access to them using a specific Azure Active Directory (Azure AD) user group.

To implement role-based access, you'll need to define admin roles, assign corresponding permissions, and assign Azure AD user groups assigned to the roles.

Before using RBAC, you should understand the roles that can grant permissions and the consequences of turning on RBAC. On your first sign-in to Microsoft 365 Defender you're granted either full access or read-only access. Full access rights are granted to users with Security Administrator or Global Administrator roles in Azure AD. Read-only access is granted to users with a Security Reader role in Azure AD. Someone with a Defender for Endpoint Global administrator role has unrestricted access to all devices, regardless of their device group association and the Azure AD user groups assignments

# Create and manage roles and role-based access control

The following steps guide you on how to create roles in the Microsoft 365 Defender portal. It assumes that you have already created Azure Active Directory user groups.

1.  Access the Microsoft 365 Defender portal using an account with a Security administrator or Global administrator role assigned.
2.  In the navigation pane, select **Settings** then select **Endpoints**. Under the Permissions area, select **Roles**.
3.  Select the **Turn on roles** button.
4.  Select **+ Add item**.
5.  Enter the role name, description, and permissions you'd like to assign to the role.
6.  Select **Next** to assign the role to an Azure AD Security group.
7.  Use the filter to select the Azure AD group that you would like to add this role to.
8.  Select **Save**.

 Important

After creating roles, you'll need to create a device group and provide access to the device group by assigning it to a role that you just created.

## Permission options

The permission options:

-   View data
    
    -   Security operations - View all security operations data in the portal
        
    -   Threat and vulnerability management - View threat and vulnerability management data in the portal
        
-   Active remediation actions
    
    -   Security operations - Take response actions, approve or dismiss pending remediation actions, manage allowed/blocked lists for automation and indicators
        
    -   Threat and vulnerability management - Exception handling - Create new exceptions and manage active exceptions
        
    -   Threat and vulnerability management - Remediation handling - Submit new remediation requests, create tickets, and manage existing remediation activities
        
    -   Threat and vulnerability management - Application handling - Apply immediate mitigation actions by blocking vulnerable applications, and manage the blocked apps by unblocking if approved
        
-   Threat and vulnerability management – Manage security baselines assessment profiles - Create and manage profiles to assess if your devices comply with security industry baselines
    
-   Alerts investigation - Manage alerts, start automated investigations, run scans, collect investigation packages, manage device tags, and download only portable executable (PE) files
    
-   Manage security settings in Security Center - Configure alert suppression settings, manage folder exclusions for automation, onboard and offboard devices, and manage email notifications, manage evaluation lab
    
-   Manage endpoint security settings in Microsoft Endpoint Manager - Full access to the "Endpoint Security" area in Microsoft Endpoint Manager, Intune "Endpoint Security Manager" role permissions, configure endpoint security and compliance features including Microsoft Defender for Endpoint onboarding, and the ability to view the "Configuration Management" page in Security Center
    
-   Live response capabilities
    
    -   Basic commands:
        
        -   Start a live response session
            
        -   Perform read-only live response commands on remote device (excluding file copy and execution)
            
    -   Advanced commands:
        
        -   Download a file from the remote device via live response
            
        -   Download PE and non-PE files from the file page
            
        -   Upload a file to the remote device
            
        -   View a script from the files library
            
        -   Execute a script on the remote device from the files library

# Configure device groups

In an enterprise scenario, security operation teams are typically assigned a set of devices. These devices are grouped together based on a set of attributes such as their domains, computer names, or designated tags.

In Microsoft Defender for Endpoint, you can create device groups and use them to:

-   Limit access to related alerts and data to specific Azure AD user groups with assigned RBAC roles
    
-   Configure different auto-remediation settings for different sets of devices
    
-   Assign specific remediation levels to apply during automated investigations
    
-   In an investigation, filter the Devices list to specific device groups by using the Group filter.
    

You can create device groups in the context of role-based access (RBAC) to control who can take specific action or see information by assigning the device group(s) to a user group.

As part of the process of creating a device group, you'll:

-   Set the automated remediation level for that group.
    
-   Specify the matching rule that determines which device group belongs to the group based on the device name, domain, tags, and OS platform. If a device is also matched to other groups, it's added only to the highest ranked device group.
    
-   Select the Azure AD user group that should have access to the device group.
    
-   Rank the device group relative to other groups after it's created.
    

## Create a device group

To create a device group:

1.  In the navigation pane, select **Settings**, select **Endpoints** and then under **Permissions** select **Device groups**.
    
2.  Select **+ Add device group**.
    
3.  Enter the group name and automation settings and specify the matching rule that determines which devices belong to the group. See How the automated investigation starts.
    
4.  Preview several devices that will be matched by this rule. If you're satisfied with the rule, select the User access tab.
    
5.  Assign the user groups that can access the device group you created. You can only grant access to Azure AD user groups that have been assigned to RBAC roles.
    
6.  Select **Close**. The configuration changes are applied.

# Configure environment advanced features

The Advanced Features area in the General Settings area provides many on/off switches for features within the product. Some of these features you'll learn about in later modules.

Depending on the Microsoft security products that you use, some advanced features might be available for you to integrate Defender for Endpoint with.

In the navigation pane, select Settings > Endpoints > Advanced features.

Select the advanced feature you want to configure and toggle the setting between On and Off.

Select Save preferences.

Use the following advanced features to get better protected from potentially malicious files and gain better insight during security investigations.

### Automated investigation

Turn on this feature to take advantage of the automated investigation and remediation features of the service. For more information, see Automated investigation.

### Live response

 Note

Live response requires Automated investigation to be turned on before you can enable it in the advanced settings section in the portal.

Turn on this feature so that users with the appropriate permissions can start a live response session on devices.

### Live response for servers

Turn on this feature so that users with the appropriate permissions can start a live response session on servers.

### Live response unsigned script execution

Enabling this feature allows you to run unsigned scripts in a live response session.

### Always remediate PUA

Potentially unwanted applications (PUA) are a category of software that can cause your machine to run slowly, display unexpected ads, or at worst, install other software, which might be unexpected or unwanted.

Turn on this feature so that potentially unwanted applications (PUA) are remediated on all devices in your tenant even if PUA protection isn't configured on the devices. This activation of the feature helps to protect users from inadvertently installing unwanted applications on their device. When turned off, remediation is dependent on the device configuration.

### Restrict correlation to within scoped device groups

This configuration can be used for scenarios where local SOC operations would like to limit alert correlations only to device groups that they can access. By enabling this setting, an incident composed of alerts that cross-device groups will no longer be considered a single incident. The local SOC can then take action on the incident because they have access to one of the device groups involved. However, global SOC will see several different incidents by device group instead of one incident. We don't recommend turning on this setting unless doing so outweighs the benefits of incident correlation across the entire organization.

 Note

Changing this setting impacts future alert correlations only.

### Enable EDR in block mode

Endpoint detection and response (EDR) in block mode provides protection from malicious artifacts, even when Microsoft Defender Antivirus is running in passive mode. When turned on, EDR in block mode blocks malicious artifacts or behaviors that are detected on a device. EDR in block mode works behind the scenes to remediate malicious artifacts that are detected post breach.

### Autoresolve remediated alerts

For tenants created on or after Windows 10, version 1809, the automated investigation, and remediation capability is configured by default to resolve alerts where the automated analysis result status is "No threats found" or "Remediated". If you don't want to have alerts auto resolved, you'll need to manually turn off the feature.

 Tip

For tenants created prior to that version, you'll need to manually turn this feature on from the Advanced features page.

 Note

The result of the auto-resolve action may influence the Device risk level calculation which is based on the active alerts found on a device. If a security operations analyst manually sets the status of an alert to "In progress" or "Resolved" the auto-resolve capability will not overwrite it.

### Allow or block file

Blocking is only available if your organization fulfills these requirements:

-   Uses Microsoft Defender Antivirus as the active antimalware solution
-   The cloud-based protection feature is enabled

This feature enables you to block potentially malicious files in your network. Blocking a file will prevent it from being read, written, or executed on devices in your organization.

After turning on this feature, you can block files via the Add Indicator tab on a file's profile page.

### Custom network indicators

Turning on this feature allows you to create indicators for IP addresses, domains, or URLs, which determine whether they'll be allowed or blocked based on your custom indicator list.

To use this feature, devices must be running Windows 10 version 1709 or later, or Windows 11. They should also have network protection in block mode and version 4.18.1906.3 or later of the antimalware platform see KB 4052623.

 Note

Network protection leverages reputation services that process requests in locations that might be outside of the location you've selected for your Defender for Endpoint data.

### Tamper protection

During some kinds of cyber attacks, bad actors try to disable security features, such as anti-virus protection, on your machines. Bad actors like to disable your security features to get easier access to your data, to install malware, or to otherwise exploit your data, identity, and devices.

Tamper protection essentially locks Microsoft Defender Antivirus and prevents your security settings from being changed through apps and methods.

This feature is available if your organization uses Microsoft Defender Antivirus and Cloud-based protection is enabled.

Leave tamper protection turned on to prevent unwanted changes to your security solution and its essential features.

### Show user details

Turn on this feature so that you can see user details stored in Azure Active Directory. Details include a user's picture, name, title, and department information when investigating user account entities. You can find user account information in the following views:

-   Security operations dashboard
-   Alert queue
-   Device details page

### Skype for Business integration

Enabling the Skype for Business integration gives you the ability to communicate with users using Skype for Business, email, or phone. This activation can be handy when you need to communicate with the user and mitigate risks.

 Note

When a device is being isolated from the network, there's a pop-up where you can choose to enable Outlook and Skype communications which allows communications to the user while they are disconnected from the network. This setting applies to Skype and Outlook communication when devices are in isolation mode.

### Microsoft Defender for Identity integration

The integration with Microsoft Defender for Identity allows you to pivot directly into another Microsoft Identity security product. Microsoft Defender for Identity augments an investigation with more insights about a suspected compromised account and related resources. By enabling this feature, you'll enrich the device-based investigation capability by pivoting across the network from an identify point of view.

 Note

You'll need to have the appropriate license to enable this feature.

### Office 365 Threat Intelligence connection

This feature is only available if you've an active Office 365 E5 or the Threat Intelligence add-on.

When you turn on this feature, you'll be able to incorporate data from Microsoft Defender for Office 365 into Microsoft 365 Defender to conduct a comprehensive security investigation across Office 365 mailboxes and Windows devices.

 Note

You'll need to have the appropriate license to enable this feature.

To receive contextual device integration in Office 365 Threat Intelligence, you'll need to enable the Defender for Endpoint settings in the Security & Compliance dashboard.

### Microsoft Threat Experts - Targeted Attack Notifications

You can only use the experts-on-demand capability if you've applied for preview and your application has been approved. You can receive targeted attack notifications from Microsoft Threat Experts through your portal's alerts dashboard and via email if you configure it.

### Microsoft Defender for Cloud Apps

Enabling this setting forwards Defender for Endpoint signals to Microsoft Defender for Cloud Apps to provide deeper visibility into cloud application usage. Forwarded data is stored and processed in the same location as your Defender for Cloud Apps data.

### Enable the Microsoft Defender for Endpoint integration from the Microsoft Defender for Identity portal

To receive contextual device integration in Microsoft Defender for Identity, you'll also need to enable the feature in the Microsoft Defender for Identity portal.

### Web content filtering

Block access to websites containing unwanted content and track web activity across all domains. To specify the web content categories you want to block, create a web content filtering policy. Ensure you've network protection in block mode when deploying the Microsoft Defender for Endpoint security baseline.

### Share endpoint alerts with Microsoft Purview compliance portal

Forwards endpoint security alerts and their triage status to Microsoft Purview compliance portal, allowing you to enhance insider risk management policies with alerts and remediate internal risks before they cause harm. Forwarded data is processed and stored in the same location as your Office 365 data.

After configuring the Security policy violation indicators in the insider risk management settings, Defender for Endpoint alerts will be shared with insider risk management for applicable users.

### Microsoft Intune connection

Defender for Endpoint can be integrated with Microsoft Intune to enable device risk-based conditional access. When you turn on this feature, you'll be able to share Defender for Endpoint device information with Intune, enhancing policy enforcement.

 Important

You'll need to enable the integration on both Intune and Defender for Endpoint to use this feature.

This feature is only available if you've the following prerequisites:

A licensed tenant for Enterprise Mobility + Security E3, and Windows E5 (or Microsoft 365 Enterprise E5)

An active Microsoft Intune environment, with Intune-managed Windows devices Azure AD-joined.

### Conditional Access policy

When you enable Intune integration, Intune will automatically create a classic Conditional Access (CA) policy. This classic CA policy is a prerequisite for setting up status reports to Intune. It shouldn't be deleted.

 Note

The classic CA policy created by Intune is distinct from modern Conditional Access policies, which are used for configuring endpoints.

### Device discovery

Helps you find unmanaged devices connected to your corporate network without the need for extra appliances or cumbersome process changes. Using onboarded devices, you can find unmanaged devices in your network and assess vulnerabilities and risks.

 Note

You can always apply filters to exclude unmanaged devices from the device inventory list. You can also use the onboarding status column on API queries to filter out unmanaged devices.

### Preview features

Learn about new features in the Defender for Endpoint preview release. Try upcoming features by turning on the preview experience.

You'll have access to upcoming features, which you can provide feedback on to help improve the overall experience before features are generally available.

### Download quarantined files

Backup quarantined files in a secure and compliant location so they can be downloaded directly from quarantine. The Download file button will always be available in the file page. This setting is turned on by default.

# Knowledge check

1. The default data retention period in Microsoft 365 Defender for Endpoint is?

One month

[X] Six months

Correct. The default is six months.

Three months

2. Which of the following options is a valid Microsoft 365 Defender for Endpoint onboarding option for Windows 10 devices?

[X] Group policy

Correct. Group policy is a valid deployment option.

Microsoft Store

General install package

3. Which security permission allows the configuration of storage settings?

Manage security settings in Security Center

Incorrect. This permission doesn't allow the configuration of storage settings.

[X] Manage portal system settings

Correct. This permission allows the configuration of storage settings.

Advanced commands

# Summary and resources

You learned how deploying the Microsoft Defender for Endpoint environment involves configuring your tenant, onboarding your devices, and configuring security.

You should now be able to:

-   Create your Microsoft Defender for Endpoint environment
    
-   Onboard devices to be monitored by Microsoft Defender for Endpoint
    
-   Configure Microsoft Defender for Endpoint environment settings
    

## Learn more

You can learn more by reviewing the following.

[Set up Microsoft Defender for Endpoint deployment](https://learn.microsoft.com/en-us/windows/security/threat-protection/microsoft-defender-atp/production-deployment)

[Onboard devices to the Microsoft Defender for Endpoint service](https://learn.microsoft.com/en-us/windows/security/threat-protection/microsoft-defender-atp/onboard-configure)

[Become a Microsoft Defender for Endpoint Ninja (formerly MDATP)](https://nam06.safelinks.protection.outlook.com/?url=https%3A%2F%2Ftechcommunity.microsoft.com%2Ft5%2Fmicrosoft-defender-for-endpoint%2Fbecome-a-microsoft-defender-atp-ninja%2Fba-p%2F1515647&data=04%7C01%7Cbneeb%40microsoft.com%7C70ade848411b4dbb43bd08d8b1e6e51e%7C72f988bf86f141af91ab2d7cd011db47%7C1%7C0%7C637454952552234995%7CUnknown%7CTWFpbGZsb3d8eyJWIjoiMC4wLjAwMDAiLCJQIjoiV2luMzIiLCJBTiI6Ik1haWwiLCJXVCI6Mn0%3D%7C1000&sdata=%2FfCCxsoJg5FwJwrgGstqLGYHuABKDTOlvmPbT3zVQ6w%3D&reserved=0%3Fazure-portal%3Dtrue)

[Microsoft Tech Community Security Webinars](https://techcommunity.microsoft.com/t5/microsoft-security-and/security-community-webinars/ba-p/927888)