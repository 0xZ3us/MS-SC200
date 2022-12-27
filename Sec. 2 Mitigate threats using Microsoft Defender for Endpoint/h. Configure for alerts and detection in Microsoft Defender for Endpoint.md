# Introduction

Microsoft Defender for Endpoint provides configuration options for alerts and detections. The configurations include notifications, custom indicators, and detection rules.

You're a Security Operations Analyst working at a company that has implemented Microsoft Defender for Endpoint. You're responsible for managing alert related settings in the environment. You manage Live Response settings, alert notification settings, indicators, and custom detections.

Your threat hunting team has provided you with a CSV file with indicators they would like Defender for Endpoint to alert on. In the Settings page, Rules area, you select indicators and then import. After the file is imported, the indicators will be used in detections.

Your manager asks for alert notifications for a specific device group and with the severity of high. In the Settings page, General area, you select Alert notifications. You then create an alert notification rule to meet the manager’s request.

After completing this module, you'll be able to:

-   Configure alert settings in Microsoft Defender for Endpoint
-   Manage indicators in Microsoft Defender for Endpoint

# Configure advanced features

The **Advanced features** page in the **General** area of the **Settings - Endpoints** menu of the Microsoft 365 Defender portal provides the following alert and detection-related settings:

The Advanced features area in General Settings area provides many an on/off switch for features within the product. The following are settings that are alert focused.

| Feature | Description  |
|---|---|
| Live Response | Allows users with appropriate RBAC permissions to investigate devices that they're authorized to access, using a remote shell connection.  |
| Live Response unsigned script execution | Enables using unsigned scripts in Live Response.  |
| Custom network indicators | Configures devices to allow or block connections to IP addresses, domains, or URLs in your custom indicator lists. |

### Live response

Turn on this feature so that users with the appropriate permissions can start a live response session on devices.

### Live response unsigned script execution

Enabling this feature allows you to run unsigned scripts in a live response session.

### Custom network indicators

Turning on this feature allows you to create indicators for IP addresses, domains, or URLs, which determine whether they'll be allowed or blocked based on your custom indicator list.

# Configure alert notifications

You can configure Defender for Endpoint to send email notifications to specified recipients for new alerts. This feature enables you to identify a group of individuals who will immediately be informed and can act on alerts based on their severity.

Only users with 'Manage security settings' permissions can configure email notifications. If you've chosen to use basic permissions management, users with Security Administrator or Global Administrator roles can configure email notifications.

You can set the alert severity levels that trigger notifications. You can also add or remove recipients of the email notification. New recipients get notified about alerts encountered after they're added. For more information about alerts, see View and organize the Alerts queue.

If you're using role-based access control (RBAC), recipients will only receive notifications based on the device groups that were configured in the notification rule. Users with the proper permission can only create, edit, or delete notifications limited to their device group management scope. Only users assigned to the Global administrator role can manage notification rules that were configured for all device groups.

The email notification includes basic information about the alert and a link to the portal where you can do further investigation.

## Create rules for alert notifications

You can create rules that determine the devices and alert severities to send email notifications to notification recipients.

1.  In the Microsoft 365 Defender portal, select **Settings** then select **Endpoints** and then select **Email notifications**.
    
2.  Select **+ Add item**.
    
3.  Specify the General information:
    
    -   Rule name - Specify a name for the notification rule.
        
    -   Include organization name - Specify the customer name that appears on the email notification.
        
    -   Include tenant-specific portal link - Adds a link with the tenant ID to allow access to a specific tenant.
        
    -   Include device information - Includes the device name in the email alert body.
        
    -   Devices - Choose whether to notify recipients for alerts on all devices (Global administrator role only) or selected device groups. For more information, see Create and manage device groups.
        
    -   Alert severity - Choose the alert severity level.
        
4.  Select **Next**.
    
5.  Enter the recipient's email address, then select **Add recipient**. You can add multiple email addresses.
    
6.  Check that email recipients are able to receive the email notifications by selecting Send test email.
    
7.  Select **Save notification rule**.

# Manage alert suppression

There might be scenarios where you need to suppress alerts from appearing in the portal. You can create suppression rules for specific alerts known to be innocuous, such as known tools or processes in your organization.

**View existing rules**

You can view a list of all the suppression rules and manage them in one place. You can also turn an alert suppression rule on or off by completing these actions:

1.  In the Microsoft 365 Defender portal, select **Settings** then select **Endpoints** and then under Rules select **Alert suppression**. The list of suppression rules that users in your organization have created is displayed.
    
2.  Select a rule by selecting the check-box beside the rule name.
    
3.  Select **Turn rule on**, **Edit rule**, or **Delete rule**. When making changes to a rule, you can choose to release alerts that it has already suppressed, regardless of whether or not these alerts match the new criteria.

# Manage indicators

Indicator of compromise (IoCs) matching is an essential feature in every endpoint protection solution. This capability gives SecOps the ability to set a list of detection indicators and for blocking (prevention and response). Create indicators that define the detection, prevention, and exclusion of entities. You can define the action to be taken, the duration for when to apply the action, and the scope of the device group to apply it to.

[Microsoft Defender for Endpoint Unified IOCs](https://www.microsoft.com/en-us/videoplayer/embed/RE4qLVw?rel=0&postJsllMsg=true)

Currently supported sources are the cloud detection engine of Defender for Endpoint, the automated investigation and remediation engine, and the endpoint prevention engine (Microsoft Defender AV).

**Cloud detection engine**

The Defender for Endpoint's cloud detection engine regularly scans collected data and tries to match the indicators you set. When there's a match, action will be taken according to the IoC settings you specified.

**Endpoint prevention engine**

The same list of indicators is honored by the prevention agent. Meaning, if Microsoft Defender AV is the primary AV configured, the matched indicators will be treated according to the settings. For example, if the action is "Alert and Block", Microsoft Defender AV will prevent file executions (block and remediate), and a corresponding alert will be raised. Otherwise, if the Action is set to "Allow", Microsoft Defender AV won't detect nor block the file from being run.

**Automated investigation and remediation engine**

The automated investigation and remediation behave the same. If an indicator is set to "Allow", Automated investigation and remediation will ignore a "bad" verdict for it. If set to "Block", Automated investigation and remediation will treat it as "bad".

The current supported actions are:

-   Allow
    
-   Alert only
    
-   Alert and block
    

You can create an indicator for:

-   Files
    
-   IP addresses, URLs/domains
    
-   Certificates
    

There's a limit of 15,000 indicators per tenant.

## Manage indicators

To manage indicators:

-   In the navigation pane, select **Settings > Endpoints** and then select **Indicators** in the Rules area.
    
-   Select the tab of the entity type you'd like to manage.
    
-   Update the indicator details and select Save or select the Delete button if you'd like to remove the entity from the list.
    

## Create indicators for files

You can prevent further propagation of attacks in your organization by banning potentially malicious files or suspected malware. If you know a potentially malicious portable executable (PE) file, you can block it. This operation will prevent it from being read, written, or executed on machines in your organization.

There are two ways you can create indicators for files:

-   By creating an indicator through the settings page
    
-   By creating a contextual indicator using the add indicator button from the file details page
    

### Prerequisites

Before you create indicators for files, you should understand the following prerequisites:

-   This feature is available if your organization uses Windows Defender Antivirus and Cloud-based protection is enabled. For more information, see Manage cloud-based protection.
    
-   The Antimalware client version must be 4.18.1901.x or later.
    
-   It's supported on machines with Windows 10, version 1703 or later, Windows server 2016 and 2019.
    
-   To start blocking files, you first need to turn the Block or allow feature on in Settings.
    
-   This feature is designed to prevent suspected malware (or potentially malicious files) from being downloaded from the web. It currently supports portable executable (PE) files, including .exe and .dll files. The coverage will be extended over time.
    

 Important

The allow or block function cannot be done on files if the file's classification exists on the device's cache prior to the allow or block action. Trusted signed files will be treated differently. Defender for Endpoint is optimized to handle malicious files. Trying to block trusted signed files, in some cases, may have performance implications. Typically, file blocks are enforced within a couple of minutes but can take upwards of 30 minutes.

### Create a contextual indicator from the file details page

One of the options when taking response actions on a file is adding an indicator for the file. When you add an indicator hash for a file, you can choose to raise an alert and block the file whenever a machine in your organization attempts to run it. Files automatically blocked by an indicator won't show up in the file's Action center, but the alerts will still be visible in the Alerts queue.

## Create indicators for IPs and URLs/domains

Defender for Endpoint can block what Microsoft deems as malicious IPs/URLs through Windows Defender SmartScreen for Microsoft browsers and through Network Protection for non-Microsoft browsers or calls made outside of a browser.

The threat intelligence data set for this has been managed by Microsoft.

By creating indicators for IPs and URLs or domains, you can now allow or block IPs, URLs, or domains based on your own threat intelligence. You can do this through the settings page or by machine groups if you deem certain groups to be more or less at risk than others. Classless Inter-Domain Routing (CIDR) notation for IP addresses isn't supported.

### Prerequisites

You should understand the following prerequisites prior to creating indicators for IPS, URLs, or domains:

-   URL/IP allow and block relies on the Defender for Endpoint component Network Protection to be enabled in block mode. For more information on Network Protection and configuration instructions, see Enable network protection.
    
-   The Antimalware client version must be 4.18.1906.x or later.
    
-   Supported on machines on Windows 10, version 1709 or later.
    
-   Ensure that _Custom network indicators_ are enabled in Microsoft Defender Security Center > Settings > Advanced features. For more information, see Advanced features.
    

Only external IPs can be added to the indicator list. Indicators can't be created for internal IPs. For web protection scenarios, we recommend using the built-in capabilities in Microsoft Edge. Microsoft Edge uses Network Protection to inspect network traffic and allows blocks for TCP, HTTP, and HTTPS (TLS). For all other processes, web protection scenarios use Network Protection for inspection and enforcement:

-   IP is supported for all three protocols
    
-   Only single IP addresses are supported (no CIDR blocks or IP ranges)
    
-   Encrypted URLs (full path) can only be blocked on first party browsers
    
-   Encrypted URLs (FQDN only) can be blocked outside of first party browsers
    
-   Full URL path blocks can be applied on the domain level and all unencrypted URLs
    

There may be up to 2 hours of latency (usually less) between the time the action is taken and the URL and IP being blocked.

### Create an indicator for IPs, URLs, or domains

1.  In the navigation pane, select **Settings > Indicators**.
    
2.  Select the IP addresses or URLs/Domains tab.
    
3.  Select **Add item**.
    
4.  Specify the following details:
    
    -   Indicator - Specify the entity details and define the expiration of the indicator.
        
    -   Action - Specify the action to be taken and provide a description.
        
    -   Scope - Define the scope of the machine group.
        
5.  Review the details in the Summary tab, then select **Save**.
    

## Create indicators based on certificates

You can create indicators for certificates. Some common use cases include:

-   Scenarios when you need to deploy blocking technologies, such as attack surface reduction rules and controlled folder access but need to allow behaviors from signed applications by adding the certificate in the allowlist.
    
-   Blocking the use of a specific signed application across your organization. By creating an indicator to block the certificate of the application, Windows Defender AV will prevent file executions (block and remediate), and the Automated Investigation and Remediation will behave the same.
    

### Prerequisites

You should understand the following requirements prior to creating indicators for certificates:

-   This feature is available if your organization uses Windows Defender Antivirus and Cloud-based protection is enabled. For more information, see Manage cloud-based protection.
    
-   The Antimalware client version must be 4.18.1901.x or later.
    
-   Supported on machines on Windows 10, version 1703 or later, Windows server 2016 and 2019.
    
-   The virus and threat protection definitions must be up to date.
    
-   This feature currently supports entering .CER or .PEM file extensions.
    

A valid leaf certificate is a signing certificate with a valid certification path and must be chained to the Root Certificate Authority (CA) trusted by Microsoft. Alternatively, a custom (self-signed) certificate can be used as long as it's trusted by the client (Root CA certificate is installed under the Local Machine 'Trusted Root Certification Authorities'). The children or parents of the allow/block certificate IOCs are not included in the allow/block IoC functionality; only leaf certificates are supported. Microsoft signed certificates cannot be blocked.

It can take up to 3 hours to create and remove a certificate IoC.

### Create an indicator for certificates:

1.  In the Microsoft 365 Defender portal, select **Settings > Endpoints > Indicators**.
    
2.  Select the Certificate tab.
    
3.  Select **+ Add item**.
    
4.  Specify the following details:
    
    -   Indicator - Specify the entity details and define the expiration of the indicator.
        
    -   Action - Specify the action to be taken and provide a description.
        
    -   Scope - Define the scope of the machine group.
        
5.  Review the details in the Summary tab, then select **Save**.
    

## Import a list of IoCs

You can also choose to upload a CSV file that defines the attributes of indicators, the action to be taken, and other details.

Download the sample CSV to know the supported column attributes.

1.  In the Microsoft 365 Defender portal, select **Settings > Endpoints > Indicators**.
    
2.  Select the tab of the entity type you'd like to import indicators for.
    
3.  Select **Import > Choose file**.
    
4.  Select **Import**. Do this for all the files you'd like to import.
    
5.  Select **Done**.
    

The following table shows the supported parameters.

| Parameter | Type | Description  |
|---|---|---|
| indicatorType | Enum | Type of the indicator. Possible values are: "FileSha1", "FileSha256", "IpAddress", "DomainName" and "Url". Required  |
| indicatorValue | String | Identity of the Indicator entity. Required  |
| action | Enum | The action that will be taken if the indicator will be discovered in the organization. Possible values are: "Alert", "AlertAndBlock", and "Allowed". Required  |
| title | String | Indicator alert title. Required  |
| description | String | Description of the indicator. Required  |
| expirationTime | DateTimeOffset | The expiration time of the indicator in the following format YYYY-MM-DDTHH:MM:SS.0Z. Optional  |
| severity | Enum | The severity of the indicator. Possible values are: "Informational", "Low", "Medium" and "High". Optional  |
| recommendedActions | String | TI indicator alert recommended actions. Optional  |
| rbacGroupNames | String | Comma-separated list of RBAC group names the indicator would be applied to. Optional  |
| category | String | Category of the alert. Examples include: Execution and credential access. Optional  |
| MITRE techniques | String | MITRE techniques code/id (comma separated). For more information, see Enterprise tactics. Optional It is recommended to add a value in category when a MITRE technique. |

# Knowledge check

1. Which file type can be used to upload Indicators?

JSON

XML

[X] CSV

Correct. CSV file format is supported.

2. Which type is an accepted indicator type?

[X] Certificates

correct. Certificates are an indicator type.

Email subject line

Code data

3. Which filter is included as part of an Alert notification rule?

[X] Alert Severity

Correct. Alert Severity is a filter option for the rule.

Account

Subject IDs

# Summary and resources

You should have learned how Microsoft Defender for Endpoint provides configuration options for alerts and detections. And that the configurations include notifications, custom indicators, and detection rules.

You should now be able to:

-   Configure alert settings in Microsoft Defender for Endpoint
-   Manage indicators in Microsoft Defender for Endpoint

## Learn more

You can learn more by reviewing the following.

[Become a Microsoft Defender for Endpoint Ninja](https://techcommunity.microsoft.com/t5/microsoft-defender-for-endpoint/become-a-microsoft-defender-for-endpoint-ninja/ba-p/1515647)

[Microsoft Tech Community Security Webinars](https://techcommunity.microsoft.com/t5/microsoft-security-and/security-community-webinars/ba-p/927888)