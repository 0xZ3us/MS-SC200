# Introduction

Microsoft Defender for Endpoint provides automated investigation and remediation. The automation configuration options allow for control of how the automation is applied to devices.

You're a Security Operations Analyst working at a company that is implementing Microsoft Defender for Endpoint. You have different remediation automation requirements for devices. You plan to create device groups to manage remediation levels.

Device groups provide two primary functions; set the remediation level, and set security access. You meet with your Security Operations team and design device groups to meet both of these functional requirements. You then configure the Remediation Level for each device group and assign the devices.

After completing this module, you'll be able to:

-   Configure advanced features of Microsoft Defender for Endpoint
    
-   Manage automation settings in Microsoft Defender for Endpoint

# Cofigure advanced features

The Advanced features page in the Settings/General area provides the following automation-related settings:

The Advanced features area in the General Settings area provides many an on/off switch for features within the product. The following are settings that are automation focused.

| Feature | Description  |
|---|---|
| Automated Investigation | Enables the automation capabilities for investigation and response.  |
| Enable EDR in block mode | When turned on, Microsoft Defender for Endpoint uses behavioral blocking and containment capabilities by blocking malicious artifacts or behaviors observed through post-breach endpoint detection and response (EDR) capabilities. This feature doesn't change how Microsoft Defender for Endpoint performs detection, alert generation, and incident correlation.  |
| Automatically resolve alerts | Resolves an alert if Automated investigation finds no threats or has successfully remediated all malicious artifacts.  |
| Allow or block file | Make sure that Windows Defender Antivirus is turned on and the cloud-based protection feature is enabled in your organization to use the allow or block file feature. |

### Automated investigation

Turn on this feature to take advantage of the automated investigation and remediation features of the service.

### Autoresolve remediated alerts

For tenants created on or after Windows 10, version 1809, the automated investigation and remediation capability are configured by default to resolve alerts where the automated analysis result status is "No threats found" or "Remediated". If you don't want to have alerts autoresolved, you'll need to turn off the feature manually.

The result of the autoresolve action may influence the Device risk level calculation based on the active alerts found on a device. If a security operations analyst manually sets the status of an alert to "In progress" or "Resolved," the autoresolve capability won't overwrite it.

### Allow or block file

Blocking is only available if your organization fulfills these requirements:

-   Uses Microsoft Defender Antivirus as the active antimalware solution

And

-   The cloud-based protection feature is enabled

This feature enables you to block potentially malicious files in your network. Blocking a file will prevent it from being read, written, or executed on devices in your organization. After turning on this feature, you can block files via the Add Indicator tab on a file's profile page.

# Manage automation upload nad folder settings

## Manage automation uploads

Enable the **File Content Analysis** capability so that certain files and email attachments can automatically be uploaded to the cloud for more inspection in Automated investigation. Identify the files and email attachments by specifying the file extension names and email attachment extension names. For example, if you add exe and bat as file or attachment extension names, then all files or attachments with those extensions will automatically be sent to the cloud for more inspection during Automated investigation.

Enable the Memory Content Analysis capability if you would like Microsoft Defender for Endpoint to automatically investigate memory content of processes. When enabled, memory content might be uploaded to Microsoft Defender for Endpoint during an Automated investigation.

[![Screenshot of Automation File upload settings.](https://learn.microsoft.com/en-us/training/wwl-sci/configure-manage-automation-microsoft-defender-for-endpoint/media/automation-uploads.png)](https://learn.microsoft.com/en-us/training/wwl-sci/configure-manage-automation-microsoft-defender-for-endpoint/media/automation-uploads.png#lightbox)

### Add file extension names and attachment extension names

To configure file settings:

-   In the navigation pane for Microsoft 365 Defender, select **Settings > Endpoints**. Under the Rules section, select **Automation uploads**.
    
-   Toggle the content analysis setting between On and Off.
    
-   Configure the following extension names and separate extension names with a comma:
    
    -   File extension names - Suspicious files except email attachments will be submitted for more inspection

## Manage automation folder exclusions

Automation folder exclusions allow you to specify folders that the Automated investigation will skip. You can control the following attributes about the folder that you'd like to be skipped:

-   Folders
    
-   Extensions of the files
    
-   File names
    

### Folders

You can specify a folder and its subfolders to be skipped.

### Extensions

You can specify the extensions to exclude in a specific directory. The extensions are a way to prevent an attacker from using an excluded folder to hide an exploit. The extensions explicitly define which files to ignore.

### File names

You can specify the file names that you want to be excluded in a specific directory. The names are a way to prevent an attacker from using an excluded folder to hide an exploit. The names explicitly define which files to ignore.

### Add an automation folder exclusion

To manage folder exclusions:

-   In the navigation pane for Microsoft 365 Defender, select **Settings > Endpoints**. Under the Rules section, select **Automation folder exclusions**.
    
-   Select New folder exclusion.
    
-   Enter the folder details:
    
    -   Folder
        
    -   Extensions
        
    -   File names
        
    -   Description
        
-   Select **Save**.

# Configure automated investigation and remediation capabilities

To configure automated investigation and remediation, turn on the features, and then set up device groups.

## **Turn on automated investigation and remediation**

As a global administrator or security administrator:

1.  In the navigation pane, select **Settings > Endpoints**.
    
2.  In the General section, select **Advanced features**.
    
3.  Turn on both Automated Investigation and Automatically resolve alerts.
    

## Set up device groups

1.  In the navigation pane for Endpoints under Permissions, select **Device groups**.
    
2.  Select **+ Add device group**.
    
    -   Create at least one device group, as follows:
        
        -   Specify a name and description for the device group.
            
        -   In the Automation level list, select a level, such as Full – remediate threats automatically. The automation level determines whether remediation actions are taken automatically or only upon approval. To learn more, see How threats are remediated.
            
        -   In the Devices section, use one or more conditions to identify and include devices.
            
        -   On the User access tab, select the Azure Active Directory groups that should have access to the device group you're creating.
            
3.  Select **Done** when you're finished setting up your device group.
    

### Automation levels

**Full - remediate threats automatically (also referred to as full automation)**

With full automation, remediation actions are performed automatically. All remediation actions that are taken can be viewed in the Action Center on the History tab. If necessary, a remediation action can be undone.

**Semi - require approval for any remediation (also referred to as semi-automation)**

With this level of semi-automation, approval is required for any remediation action. Such pending actions can be viewed and approved in the Action Center, on the Pending tab.

**Semi - require approval for core folders remediation (also a type of semi-automation)**

With this level of semi-automation, approval is required for any remediation actions needed on files or executables that are in core folders. Core folders include operating system directories, such as the Windows (\windows*). Remediation actions can be taken automatically on files or executables that are in other (non-core) folders. Pending actions for files or executables in core folders can be viewed and approved in the Action Center, on the Pending tab. Actions that were taken on files or executables in other folders can be viewed in the Action Center, on the History tab.

**Semi - require approval for non-temp folders remediation (also a type of semi-automation)**

With this level of semi-automation, approval is required for any remediation actions needed on files or executables that aren't in temporary folders.

Temporary folders can include the following examples:

-   \users*\appdata\local\temp*
    
-   \documents and settings*\local settings\temp*
    
-   \documents and settings*\local settings\temporary*
    
-   \windows\temp*
    
-   \users*\downloads*
    
-   \program files\
    
-   \program files (x86)*
    
-   \documents and settings*\users*
    

Remediation actions can be taken automatically on files or executables that are in temporary folders. Pending actions for files or executables that aren't in temporary folders can be viewed and approved in the Action Center, on the Pending tab. Actions that were taken on files or executables in temporary folders can be viewed and approved in the Action Center on the History tab.

**No automated response (also referred to as 'no automation')**

With no automation, the automated investigation doesn't run on your organization's devices. As a result, no remediation actions are taken or pending as a result of an automated investigation. However, other threat protection features, such as protection from potentially unwanted applications, can be in effect, depending on how your antivirus and next-generation protection features are configured.

Using the no automation option isn't recommended because it reduces the security posture of your organization's devices. Consider setting up your automation level to full automation (or at least semi-automation).

## Quickly configure remediation levels on device groups

Another way to set or update remediation levels on Device groups is in the Settings, General, Auto remediation page. The page provides a list of Device groups and the current remediation level for each. Select the row will allow you to adjust the remediation setting.

# Block at risk devices

Contain a threat by not letting risky devices access your corporate resources through Conditional Access.

[Microsoft Defender for Endpoint Conditional access](https://www.microsoft.com/en-us/videoplayer/embed/RE4byD1?rel=0&postJsllMsg=true)

You'll need a Microsoft Endpoint Manager environment, with Intune managed and Azure AD joined Windows 10 or higher devices.

There are steps you'll need to take in Microsoft 365 Defender, Microsoft Endpoint Manager portal, and Azure AD portal.

The required roles to access these portals and implement Conditional access:

-   Microsoft 365 Defender portal - You'll need to sign in to the portal with a global administrator role to turn on the integration.
    
-   Intune - You'll need to sign in to the portal with security administrator rights with management permissions.
    
-   Azure AD portal - You'll need to sign in as a global administrator, security administrator, or Conditional Access administrator.
    

![Diagram of architecture for M D E conditional access.](https://learn.microsoft.com/en-us/training/wwl-sci/configure-manage-automation-microsoft-defender-for-endpoint/media/mde-architecture.png)

Take the following steps to enable Conditional Access:

1.  Turn on the Microsoft Intune connection from Microsoft 365 Defender.
    
2.  Turn on the Defender for Endpoint integration in Endpoint Manager
    
3.  Create the compliance policy in Intune
    
4.  Assign the policy
    
5.  Create an Azure AD Conditional Access policy
    

### Turn on the Microsoft Intune connection

1.  In the Microsoft 365 Defender navigation pane, select **Settings > Endpoints** and then under General section select **Advanced features**.
    
2.  Toggle the Microsoft Intune connection setting to **On**.
    
3.  Select **Save preferences**.
    

### Turn on the Defender for Endpoint integration in Endpoint Manager

1.  Sign in to the Microsoft Endpoint Manager admin center [https://endpoint.microsoft.com](https://endpoint.microsoft.com/).
    
2.  Select **Endpoint security > Microsoft Defender for Endpoint**.
    
3.  Set **Allow Microsoft Defender for Endpoint to enforce Endpoint Security Configurations** to **On**.
    
4.  Select **Save**.
    

### Create the compliance policy in Endpoint Manager

1.  In the Microsoft Endpoint Manager admin center, select **Devices**, and select **Compliance policies**.
    
2.  Select **+ Create policy**.
    
3.  In Platform, select **Windows 10 and later**, and select **Create**.
    
4.  Enter a Name and Description, select **Next**.
    
5.  In the Device Health settings, set **Require the device to be at or under the Device Threat Level** to your preferred level:
    
    -   Secured: This level is the most secure. The device can't have any existing threats and still access company resources. If any threats are found, the device is evaluated as noncompliant.
    -   Low: The device is compliant if only low-level threats exist. Devices with medium or high threat levels aren't compliant.
    -   Medium: The device is compliant if the threats found on the device are low or medium. If high-level threats are detected, the device is determined as noncompliant.
    -   High: This level is the least secure and allows all threat levels. So devices with high, medium, or low threat levels are considered compliant.
6.  Select **Next** until you can select **Create**, and Create to save your changes (and create the policy).
    

### Assign the policy in Endpoint Manager

1.  In Microsoft Endpoint Manager admin center, open the policy you created in the previous step, select **Properties**.
    
2.  Under the Assignments section, select **Edit**.
    
3.  Select **Assignments**.
    
4.  Include or exclude your Azure AD groups to assign them the policy.
    
5.  To deploy the policy to the groups, select **Review + Save** and then select **Save**. The user devices targeted by the policy are evaluated for compliance.
    

### Create an Azure AD Conditional Access policy

1.  In the Azure portal, select **Azure AD Conditional Access** from the Services menu, and select the drop-down **+ New policy**, and then select **Create new policy**.
    
2.  Enter a policy Name, and select **Users or workload entities**. Use the Include or Exclude options to add your groups for the policy.
    
3.  In the **Cloud apps or actions** area choose which apps to protect. For example, choose Select apps, and select Office 365 SharePoint Online and Office 365 Exchange Online.
    
4.  In the Conditions area, select to apply the policy to Client apps and browsers. When complete select **done**.
    
5.  In the Grant area, apply Conditional Access based on device compliance. For example, select **Grant access > Require device to be marked as compliant**. Choose **Select** to save your changes.
    
6.  Select **Enable policy** choice, and then **Create** to save your changes.

# Knowledge check

1. Which is a valid remediation level?

[X] Semi - require approval for any remediation

Correct. This is a valid remediation level.

Semi - user accounts only

Semi - files only

2. A security operations analyst needs to exclude a custom executable file c:\myapp\myapp.exe, which exclusion type should they use?

[X] File

Correct. File will exclude this specific file from automation

Extension

Folder

3. In advanced features, which setting should be turned on to block files even if a third-party antivirus is used?

[X] Enable EDR in block mode

Correct. EDR in block mode is used with third party antivirus

Allow or block file

Automated Investigation

# Summary and resources

You should have learned how Microsoft Defender for Endpoint provides automated investigation and remediation. You should also have learned how the automation configuration options allow for control of how the automation is applied to devices.

You should now be able to:

-   Configure advanced features of Microsoft Defender for Endpoint
-   Manage automation settings in Microsoft Defender for Endpoint

## Learn more

You can learn more by reviewing the following.

[Become a Microsoft Defender for Endpoint Ninja (formerly MDATP](https://nam06.safelinks.protection.outlook.com/?url=https%3A%2F%2Ftechcommunity.microsoft.com%2Ft5%2Fmicrosoft-defender-for-endpoint%2Fbecome-a-microsoft-defender-atp-ninja%2Fba-p%2F1515647&data=04%7C01%7Cbneeb%40microsoft.com%7C70ade848411b4dbb43bd08d8b1e6e51e%7C72f988bf86f141af91ab2d7cd011db47%7C1%7C0%7C637454952552234995%7CUnknown%7CTWFpbGZsb3d8eyJWIjoiMC4wLjAwMDAiLCJQIjoiV2luMzIiLCJBTiI6Ik1haWwiLCJXVCI6Mn0%3D%7C1000&sdata=%2FfCCxsoJg5FwJwrgGstqLGYHuABKDTOlvmPbT3zVQ6w%3D&reserved=0%3Fazure-portal%3Dtrue)

[Microsoft Tech Community Security Webinars](https://techcommunity.microsoft.com/t5/microsoft-security-and/security-community-webinars/ba-p/927888)