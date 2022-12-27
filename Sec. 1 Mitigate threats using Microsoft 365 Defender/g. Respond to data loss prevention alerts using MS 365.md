# Introduction

Microsoft 365 provides data loss prevention (DLP) protection to identify, monitor, and automatically protect sensitive information.

You're a Security Operations Analyst working at a company that implemented Microsoft Purview Compliance solutions. Based on recent security incidents in your organization, you've been assigned the responsibility to advise the compliance team on the types of information they should protect.

To work with the compliance team, you need to learn about the data loss prevention components. These include sensitive info types, sensitivity labels, DLP policies, and policy alerts.

# Describe data loss prevention alerts

As a Security Operations Analyst, you need to understand Compliance-related terminology and alerts. The Data loss prevention (DLP) alerts will help you in your investigation to find the full scope of the incident. DLP alerts can be generated from Microsoft Purview Compliance or Microsoft Defender for Cloud Apps. You might not be the person creating the DLP Policies, but it's important for you to understand them so you can recommend changes.

To comply with business standards and industry regulations, organizations must protect sensitive information and prevent its inadvertent disclosure. Sensitive information can include financial data or personal information such as credit card numbers, social security numbers, or health records.

With a DLP policy, you can:

-   Identify sensitive information across many locations, such as Exchange Online, SharePoint Online, OneDrive, and Microsoft Teams.
    
-   For example, you can identify any document containing a credit card number that's stored in any OneDrive site, or you can monitor just the OneDrive sites of specific people.
    
-   Prevent the accidental sharing of sensitive information.
    
-   For example, you can identify any document or email containing a health record that's shared with people outside your organization, and then automatically block access to that document or block the email from being sent.
    
-   Monitor and protect sensitive information in the desktop versions of Excel, PowerPoint, and Word.
    
-   Just like in Exchange Online, SharePoint Online, and OneDrive, these Office desktop programs include the same capabilities to identify sensitive information and apply DLP policies. DLP provides continuous monitoring when people share content in these Office programs.
    
-   Help users learn how to stay compliant without interrupting their workflow.
    
-   You can educate your users about DLP policies and help them remain compliant without blocking their work. For example, if a user tries to share a document containing sensitive information, a DLP policy can send them an email notification and show them a policy tip in the context of the document library that allows them to override the policy if they have a business justification. The same policy tips also appear in Outlook on the web, Outlook, Excel, PowerPoint, and Word.
    
-   View DLP alerts and reports showing content that matches your organization’s DLP policies.
    

## Data loss prevention components

If you haven't worked with DLP, it's important to understand the underlying components.

### Sensitive information types

A sensitive information type is defined by a pattern that can be identified by a regular expression or a function. In addition, corroborative evidence such as keywords and checksums can be used to identify a sensitive information type. Confidence level and proximity are also used in the evaluation process.

Microsoft Purview Compliance comes with built-in Sensitive information types like Credit Card Numbers, Bank Accounts, and more. You can also create a custom sensitive info type matched on regular expressions, keywords, or an uploaded dictionary.

### Sensitivity labels

Sensitivity labels specify the classification of a document. The labels could be terms like public, private, or classified. With these labels, more functionality can be applied to the document, like encryption. Labels are applied to documents either manually by the user or automatically based on sensitive info types.

### Data loss prevention policy

A DLP policy contains a few basic things:

-   Where to protect the content: locations such as Exchange Online, SharePoint Online, and OneDrive sites, as well as Microsoft Teams chat and channel messages.
    
-   When and how to protect the content by enforcing rules comprised of:
    
    -   Conditions the content must match before the rule is enforced. For example, a rule might be configured to look only for content containing Social Security numbers that have been shared with people outside your organization.
        
    -   Actions that you want the rule to take automatically when content matching the conditions is found. For example, a rule might be configured to block access to a document and send both the user and compliance officer an email notification.
        

### Defender for Cloud App file policy

File policies can be set to provide continuous compliance scans, legal eDiscovery tasks, DLP for sensitive content shared publicly, and many more use cases. Microsoft Defender for Cloud Apps can monitor any file type based on more than 20 metadata filters.

# Investigate data loss prevention alerts in Microsoft Purview

To view DLP Alerts from DLP Policies created in Microsoft Purview use the following steps:

1.  In the Microsoft Purview compliance portal, [https://compliance.microsoft.com](https://compliance.microsoft.com/) on the left menu pane under Solutions, select **Data loss prevention**.
    
2.  Select the **Alerts** tab to view the DLP alerts dashboard.
    
3.  Choose filters to refine the list of alerts. Choose Customize columns to list the properties you want to see. You can also choose to sort the alerts in ascending or descending order in any column.
    
4.  Select an alert to see details.
    
5.  Select the **Events** tab to view all of the events associated with the alert. You can choose a particular event to view its details.
    
6.  Select the **Sensitive Info Types** tab to view details about the sensitive information types detected in the content. Details include confidence and count.
    
7.  After you investigate the alert, choose Manage alert to change the status (Active, Investigating, Dismissed, or Resolved). You can also add comments and assign the alert to someone in your organization.
    
8.  To see the history of workflow management, choose Management log.
    
9.  After you take the required action for the alert, set the status of the alert to **Resolved**.

# Investigate data loss prevention alerts in Microsoft Defender for Cloud Apps

When a Defender for Cloud Apps File policy is created with a DLP-related configuration, file policy violation alerts can be investigated in the Alerts area of Defender for Cloud Apps.

To manage alerts:

From the Alerts page, select **Open** for the Resolution Status.

This section of the dashboard provides full visibility into any suspicious activity or violation of your established policies. It can help you safeguard the security posture you defined for your cloud environment.

![Screen shot of Defender for Cloud Apps Alerts Dashboard](https://learn.microsoft.com/en-us/training/wwl-sci/respond-to-data-loss-prevention-alerts-microsoft-365/media/cloud-apps-dlp-alerts.png)

For each alert, you need to investigate and determine the nature of the violation and the required response.

-   You can filter the alerts by Alert type or by Severity to process the most important ones first.
    
-   Select a specific alert. Depending on what type of alert it is, you'll see various actions that can be taken before resolving the alert.
    
-   You can filter based on App - The apps listed are ones for which activities were detected by Defender for Cloud Apps.
    
-   There are three types of violations you'll need to deal with when investigating alerts:
    
    -   **Serious violations** - Serious violations require an immediate response.
        
        -   Examples:
            
            -   For a suspicious activity alert, you might want to suspend the account until the user changes their password.
                
            -   For a data leak, you might want to restrict permissions or quarantine the file.
                
            -   If a new app is discovered, you might want to block access to the service on your proxy or firewall.
                
    -   **Questionable violations** - Questionable violations require further investigation.
        
        -   You can contact the user or the user's manager about the nature of the activity.
            
        -   Leave the activity open until you have more information.
            
    -   **Authorized violations or anomalous behavior** - Authorized violations or anomalous behavior can result from legitimate use.
        
        -   You can dismiss the alert.

Anytime you dismiss an alert, it's important to submit feedback about why you're dismissing the alert. The Defender for Cloud Apps team uses this feedback as an indication of the accuracy of the alert. This information is then used to fine-tune our machine-learning models for future alerts. You can follow these guidelines in deciding how to categorize the alert:

-   If legitimate use triggered the alert and it isn't a security issue, it could be one of these types:
    
    -   Benign positive: The alert is accurate, but the activity is legitimate. You can dismiss the alert and set the reason to Actual severity is lower or Not interesting.
        
    -   False positive: The alert is inaccurate. Dismiss the alert and set the reason to Alert isn't accurate.
        
-   If there's too much noise to determine the legitimacy and accuracy of an alert, dismiss it and set the reason to Too many similar alerts.
    
-   True positive: If the alert is related to an actual risky event that was either committed maliciously or unintentionally by an insider or outsider, you should set the event to Resolve after all appropriate action has been taken to remediate the event.
    

Even though you're interested in File policy alerts for DLP, the alerts list will show many different alert types. It's important to understand the different alert types because these non-DLP alerts could also provide insight into a security incident.

The following table provides a list of the types of alerts that can be triggered and recommends ways you can resolve them.

| Alert type | Description | Recommended resolution  |
|---|---|---|
| Activity policy violation | This type of alert is the result of a policy you created. | To work with this type of alert in bulk, we recommend that you work in the Policy center to mitigate them. Fine-tune the policy to exclude noisy entities by adding more filters and more granular controls. If the policy is accurate, the alert is warranted, and it's a violation you want to stop immediately, consider adding automatic remediation in the policy.  |
| File policy violation | This type of alert is the result of a policy you created. | To work with this type of alert in bulk, we recommend that you work in the Policy center to mitigate them. Fine-tune the policy to exclude noisy entities by adding more filters and more granular controls.  |
| Compromised account | This type of alert is triggered when Defender for Cloud Apps identifies an account that was compromised. This means there's a high probability that the account was used in an unauthorized way. | We recommend that you suspend the account until you can reach the user and make sure they change their password.  |
| Inactive account | This alert is triggered when an account hasn't been used in 60 days in one of your connected cloud apps. | Contact the user and the user's manager to determine whether the account is still active. If not, suspend the user and terminate the license for the app.  |
| New admin user | Alerts you to changes in your privileged accounts for connected apps. | Confirm that the new admin permissions are required for the user. If they aren't, recommend revoking admin privileges to reduce exposure.  |
| New admin location | Alerts you to changes in your privileged accounts for connected apps. | Confirm that the sign-in from this anomalous location was legitimate. If it's not, recommend revoking admin permissions or suspending the account to reduce exposure.  |
| New location | An informative alert about access to a connected app from a new location, and it's triggered only once per country/region. | Investigate the specific user's activity.  |
| New discovered service | This alert is an alert about Shadow IT. A new app was detected by Cloud Discovery. | Assess the risk of the service based on the app catalog.  |
| Suspicious activity | This alert lets you know that anomalous activity has been detected that isn't aligned with expected activities or users in your organization. | Investigate the behavior and confirm it with the user. This type of alert is a great place to start learning more about your environment and creating new policies with these alerts. For example, if someone suddenly uploads a large amount of data to one of your connected apps, you can set a rule to govern that type of anomalous behavior.  |
| Use of personal account | This alert lets you know that a new personal account has access to resources in your connected apps. | Remove the user's collaborations in the external account. |

# Knowledge Check

1. Which DLP component is used to classify a document?

Sensitive info types

Retention Policy

[X] Sensitivity label

Correct. The Sensitivity label is applied to a document.

2. In Defender for Cloud Apps, which types of Policy is used for DLP?

Access Policy

[X] File Policy

Correct. File Policy is used for DLP.

Activity Policy

3. Which DLP component has the logic to protect content in locations such as SharePoint Online?

Sensitive info types

Incorrect. Sensitive info types are used as the pattern match component

[X] DLP Policy

Correct. The DLP Policy specifies the location.

Sensitivity label

# Summary and resources

You should have learned how Microsoft 365 provides data loss prevention (DLP) protection to identify, monitor, and automatically protect sensitive information.

You should now be able to:

-   Describe data loss prevention (DLP) components for Microsoft 365
-   Investigate DLP alerts for Microsoft 365
-   Investigate DLP alerts for Microsoft Defender for Cloud Apps

## Learn more

You can learn more by reviewing the following.

[Become a Microsoft 365 Defender Ninja](https://techcommunity.microsoft.com/t5/microsoft-365-defender/become-a-microsoft-365-defender-ninja/ba-p/1789376)

[Microsoft Tech Community Security Webinars](https://techcommunity.microsoft.com/t5/microsoft-security-and/security-community-webinars/ba-p/927888)