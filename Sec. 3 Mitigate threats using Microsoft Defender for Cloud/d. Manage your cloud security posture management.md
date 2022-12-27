https://learn.microsoft.com/en-us/training/modules/manage-cloud-security-posture-management/

# Introduction

Microsoft Defender for Cloud continually compares the configuration of your resources with requirements in industry standards, regulations, and benchmarks.

To understand how Security Posture Management evaluates your environment, it's important to understand security policies and initiatives.

## What are security policies and initiatives

Microsoft Defender for Cloud applies security initiatives to your subscriptions. These initiatives contain one or more security policies. Each of those policies results in a security recommendation for improving your security posture.

### What is a security policy?

An Azure Policy definition, created in Azure Policy, is a rule about specific security conditions that you want controlled. Built in definitions include things like controlling what type of resources can be deployed or enforcing the use of tags on all resources. You can also create your own custom policy definitions.

To implement these policy definitions (whether built-in or custom), you'll need to assign them. You can assign any of these policies through the Azure portal, PowerShell, or Azure CLI. Policies can be disabled or enabled from Azure Policy.

There are different types of policies in Azure Policy. Defender for Cloud mainly uses 'Audit' policies that check specific conditions and configurations then report on compliance. There are also "Enforce' policies that can be used to apply secure settings.

### What is a security initiative?

An Azure Policy initiative is a collection of Azure Policy definitions, or rules that are grouped together towards a specific goal or purpose. Azure initiatives simplify management of your policies by grouping a set of policies together, logically, as a single item.

A security initiative defines the desired configuration of your workloads and helps ensure you're complying with the security requirements of your company or regulators.

Like security policies, Defender for Cloud initiatives are also created in Azure Policy. You can use Azure Policy to manage your policies, build initiatives, and assign initiatives to multiple subscriptions or for entire management groups.

The default initiative automatically assigned to every subscription in Microsoft Defender for Cloud is Azure Security Benchmark. This benchmark is the Microsoft-authored, Azure-specific set of guidelines for security and compliance best practices based on common compliance frameworks. This widely respected benchmark builds on the controls from the Center for Internet Security (CIS) and the National Institute of Standards and Technology (NIST) with a focus on cloud-centric security.

Defender for Cloud offers the following options for working with security initiatives and policies:

-   View and edit the built-in default initiative - When you enable Defender for Cloud, the initiative named 'Azure Security Benchmark' is automatically assigned to all Defender for Cloud registered subscriptions. To customize this initiative, you can enable or disable individual policies within it by editing a policy's parameters. See the list of built-in security policies to understand the options available out-of-the-box.
    
-   Add your own custom initiatives - If you want to customize the security initiatives applied to your subscription, you can do so within Defender for Cloud. You'll then receive recommendations if your machines don't follow the policies you create. For instructions on building and assigning custom policies, see Using custom security initiatives and policies.
    
-   Add regulatory compliance standards as initiatives - Defender for Cloud's regulatory compliance dashboard shows the status of all the assessments within your environment, in the context of a particular standard or regulation (such as Azure CIS, NIST SP 800-53 R4, SWIFT CSP CSCF-v2020).
    

### What is a security recommendation?

Defender for Cloud uses the policies to periodically analyze the compliance status of your resources to identify potential security misconfigurations and weaknesses. It then provides you with recommendations on how to remediate those issues. Recommendations are the result of assessing your resources against the relevant policies and identifying resources that aren't meeting your defined requirements.

Defender for Cloud makes its security recommendations based on your chosen initiatives. When a policy from your initiative is compared against your resources and finds one or more that aren't compliant, it's presented as a recommendation in Defender for Cloud.

Recommendations are actions for you to take to secure and harden your resources. Each recommendation provides you with the following information:

-   A short description of the issue
-   The remediation steps to carry out in order to implement the recommendation
-   The affected resources

Azure Security Benchmark is an initiative that contains requirements.

For example, Azure Storage accounts must restrict network access to reduce their attack surface.

The initiative includes multiple policies, each with a requirement of a specific resource type. These policies enforce the requirements in the initiative.

To continue the example, the storage requirement is enforced with the policy "Storage accounts should restrict network access using virtual network rules".

Microsoft Defender for Cloud continually assesses your connected subscriptions. If it finds a resource that doesn't satisfy a policy, it displays a recommendation to fix that situation and harden the security of resources that aren't meeting your security requirements.

So, for example, if an Azure Storage account on any of your protected subscriptions isn't protected with virtual network rules, you'll see the recommendation to harden those resources.

So, (1) an initiative includes (2) policies that generate (3) environment-specific recommendations.

You're a Security Operations Analyst working at a company that uses Microsoft Defender for Cloud. You're responsible for regulatory compliance of your hybrid-cloud resources.

You need to improve the number of controls that pass the Azure Security Benchmark as displayed in Microsoft Defender for Cloud.

# Explore Secure Score

Defender for Cloud continually assesses your cross-cloud resources for security issues. It then aggregates all the findings into a single score so that you can tell, at a glance, your current security situation: the higher the score, the lower the identified risk level.

In the Microsoft Defender for Cloud Overview page, the secure score is shown as a percentage value and the underlying values are also clearly presented:

![Screenshot of Defender for Cloud Security Posture Secure Score.](https://learn.microsoft.com/en-us/training/wwl-sci/manage-cloud-security-posture-management/media/single-secure-score.png)

To increase your security, review Defender for Cloud's recommendations page and remediate the recommendation by implementing the remediation instructions for each issue. Recommendations are grouped into security controls. Each control is a logical group of related security recommendations, and reflects your vulnerable attack surfaces. Your score only improves when you remediate all of the recommendations for a single resource within a control. To see how well your organization is securing each individual attack surface, review the scores for each security control.

## Manage your security posture

On the Security posture page, you're able to see the secure score for your entire subscription, and each environment in your subscription. By default all environments are shown.

[![Screenshot of Defender for Cloud Security Posture Overview.](https://learn.microsoft.com/en-us/training/wwl-sci/manage-cloud-security-posture-management/media/security-posture-page.png)](https://learn.microsoft.com/en-us/training/wwl-sci/manage-cloud-security-posture-management/media/security-posture-page.png#lightbox)

The bottom half of the page allows you to view, and manage all of your individual subscriptions, accounts, and projects, by viewing their individual secure scores, number of unhealthy resources and even view their recommendations.

### How your secure score is calculated

To get all the possible points for a security control, all of your resources must comply with all of the security recommendations within the security control. For example, Defender for Cloud has multiple recommendations regarding how to secure your management ports. You'll need to remediate them all to make a difference to your secure score.

# Explore Recommendations

Defender for Cloud's recommendations is based on the Azure Security Benchmark. Azure Security Benchmark is the Microsoft-authored, Azure-specific set of guidelines for security and compliance best practices based on common compliance frameworks. This widely respected benchmark builds on the controls from the Center for Internet Security (CIS) and the National Institute of Standards and Technology (NIST) with a focus on cloud-centric security. Other recommendations are generated from regulator compliance initiatives.

## View your recommendations

Defender for Cloud analyzes the security state of your resources to identify potential vulnerabilities.

To view your Secure score recommendations:

-   Sign in to the Azure portal.
    
-   Navigate to Microsoft Defender for Cloud > Recommendations.
    

[![Screenshot of Defender for Cloud Secure Score Recommendations.](https://learn.microsoft.com/en-us/training/wwl-sci/manage-cloud-security-posture-management/media/recommendations-view.png)](https://learn.microsoft.com/en-us/training/wwl-sci/manage-cloud-security-posture-management/media/recommendations-view.png#lightbox)

Here you'll see the recommendations applicable to your environment(s). Recommendations are grouped into security controls.

-   Select Secure score recommendations.
    
    Secure score recommendations affect the secure score and are mapped to the various security controls. The All recommendations tab, allows you to see all of the recommendations including recommendations that are part of different regulatory compliance standards.
    
-   (Optional) Select a relevant environment(s).
    
-   Select the > to expand the control, and view a list of recommendations.
    
-   Select a specific recommendation to view the recommendation details page.
    
    For supported recommendations, the top toolbar shows any or all of the following buttons:
    
    -   **Enforce and Deny** (see Prevent misconfigurations with Enforce/Deny recommendations).
    -   **View policy definition** to go directly to the Azure Policy entry for the underlying policy.
    -   **Open query** - All recommendations have options to view the detailed information about the affected resources using Azure Resource Graph Explorer.
-   **Severity indicator.**
    
-   **Freshness interval** (where relevant).
    
-   **Count of exempted resources** if exemptions exist for a recommendation, the count shows the number of resources that have been exempted with a link to view the specific resources.
    
-   **Mapping to MITRE ATT&CK ® tactics and techniques** if a recommendation has defined tactics and techniques, select the icon for links to the relevant pages on MITRE's site. This applies only to Azure scored recommendations.
    
-   **Description** - A short description of the security issue.
    
-   When relevant, the details page also includes a table of **related recommendations**:
    

The relationship types are:

-   **Prerequisite** - A recommendation that must be completed before the selected recommendation
    
-   **Alternative** - A different recommendation, which provides another way of achieving the goals of the selected recommendation
    
-   **Dependent** - A recommendation for which the selected recommendation is a prerequisite For each related recommendation, the number of unhealthy resources is shown in the "Affected resources" column.
    
-   **Remediation steps** - A description of the manual steps required to remediate the security issue on the affected resources. For recommendations with the Fix option**, you can select View remediation logic before applying the suggested fix to your resources.
    
-   **Affected resources** - Your resources are grouped into tabs:
    
    -   **Healthy resources** – Relevant resources, which either aren't impacted or on which you've already remediated the issue.
        
    -   **Unhealthy resources** – Resources that are still impacted by the identified issue.
        
    -   **Not applicable resources** – Resources for which the recommendation can't give a definitive answer. The not applicable tab also includes reasons for each resource.
        
-   Action buttons to remediate the recommendation or trigger a logic app.
    

## Remediation steps

Recommendations give you suggestions on how to better secure your resources. You implement a recommendation by following the remediation steps provided in the recommendation.

After reviewing all the recommendations, decide which one to remediate first. We recommend that you prioritize the security controls with the highest potential to increase your secure score.

1.  From the list, select a recommendation.
    
2.  Follow the instructions in the Remediation steps section. Each recommendation has its own set of instructions.
    
3.  Once completed, a notification appears informing you whether the issue is resolved.
    

### Fix button

To simplify remediation and improve your environment's security (and increase your secure score), many recommendations include a Fix option.

To implement a Fix:

1.  From the list of recommendations that have the Fix action icon, select a recommendation.
    
2.  From the Unhealthy resources tab, select the resources that you want to implement the recommendation on, and select Remediate.
    
3.  In the confirmation box, read the remediation details and implications.
    
4.  Insert the relevant parameters if necessary, and approve the remediation.
    
5.  Once completed, a notification appears informing you if the remediation succeeded.

# Measure and enforce regulatory compliance

Microsoft Defender for Cloud continually compares the configuration of your resources with requirements in industry standards, regulations, and benchmarks. The regulatory compliance dashboard provides insights into your compliance posture based on how you're meeting specific compliance requirements.

![Screenshot of the Regulatory compliance dashboard.](https://learn.microsoft.com/en-us/training/wwl-sci/manage-cloud-security-posture-management/media/compliance-dashboard.png)

## How are regulatory compliance standards represented in Defender for Cloud?

Industry standards, regulatory standards, and benchmarks are represented in Defender for Cloud's regulatory compliance dashboard. Each standard is an initiative defined in Azure Policy.

To see compliance data mapped as assessments in your dashboard, add a compliance standard to your management group or subscription from within the Security policy page.

When you've assigned a standard or benchmark to your selected scope, the standard appears in your regulatory compliance dashboard with all associated compliance data mapped as assessments. You can also download summary reports for any of the standards that have been assigned.

Microsoft tracks the regulatory standards themselves and automatically improves its coverage in some of the packages over time. When Microsoft releases new content for the initiative, it will appear automatically in your dashboard as new policies mapped to controls in the standard.

## What regulatory compliance standards are available in Defender for Cloud?

By default, every subscription has the **Azure Security Benchmark** assigned. This is the Microsoft-authored, Azure-specific guidelines for security and compliance best practices based on common compliance frameworks.

Available regulatory standards:

-   PCI-DSS v3.2.1:2018
-   SOC TSP
-   NIST SP 800-53 R4
-   NIST SP 800 171 R2
-   UK OFFICIAL and UK NHS
-   Canada Federal PBMM
-   Azure CIS 1.1.0
-   HIPAA/HITRUST
-   SWIFT CSP CSCF v2020
-   ISO 27001:2013
-   New Zealand ISM Restricted
-   CMMC Level 3
-   Azure CIS 1.3.0
-   NIST SP 800-53 R5
-   FedRAMP H
-   FedRAMP M

## Add a regulatory standard to your dashboard

### Prerequisites

To add standards to your dashboard:

-   The subscription must have Defender for Cloud's enhanced security features enabled
-   The user must have owner or policy contributor permissions

### Add a standard

1.  From Defender for Cloud's menu, select Regulatory compliance to open the regulatory compliance dashboard. Here you can see the compliance standards currently assigned to the currently selected subscriptions.
    
2.  From the top of the page, select Manage compliance policies. The Policy Management page appears.
    
3.  Select the subscription or management group for which you want to manage the regulatory compliance posture.
    
4.  To add the standards relevant to your organization, expand the Industry & regulatory standards section and select Add more standards.
    
5.  From the Add regulatory compliance standards page, you can search for any of the available standards:
    
6.  Select Add and enter all the necessary details for the specific initiative such as scope, parameters, and remediation.
    
7.  From Defender for Cloud's menu, select Regulatory compliance again to go back to the regulatory compliance dashboard.
    
    Your new standard appears in your list of Industry & regulatory standards.

# Understand Workbooks

Azure Monitor Workbooks provide a flexible canvas for data analysis and the creation of rich visual reports within the Azure portal. They allow you to tap into multiple data sources from across Azure, and combine them into unified interactive experiences.

Within Microsoft Defender for Cloud, you can access the built-in workbooks to track your organization’s security posture. You can also build custom workbooks to view a wide range of data from Defender for Cloud or other supported data sources.

## Workbooks gallery in Microsoft Defender for Cloud

With the integrated Azure Workbooks functionality, Microsoft Defender for Cloud makes it straightforward to build your own custom, interactive workbooks. Defender for Cloud also includes a gallery with the following workbooks ready for your customization:

-   **Secure Score Over Time** workbook - Track your subscriptions' scores and changes to recommendations for your resources
-   **System Updates** workbook - View missing system updates by resources, OS, severity, and more
-   **Vulnerability Assessment Findings** workbook - View the findings of vulnerability scans of your Azure resources
-   **Compliance Over Time** workbook - View the status of a subscription's compliance with the regulatory or industry standards you've selected
-   **Active Alerts** workbook - view active alerts by severity, type, tag, MITRE ATT&CK tactics, and location.

![Screenshot of the Workbooks gallery in Defender for Cloud.](https://learn.microsoft.com/en-us/training/wwl-sci/manage-cloud-security-posture-management/media/workbooks-gallery-microsoft-defender-for-cloud.png)

# Knowledge check

1. To automatically remediate a recommendation, select which option?

Respond

Remediate

Incorrect. The fix option will start the process to automatically remediate.

[X] Fix

Correct. The fix option will start the process to automatically remediate.

2. By default, which security policy is assigned to each subscription?

SOC TSP

Incorrect. Azure Security Benchmark is the default.

[X] Azure Security Benchmark

Correct. Azure Security Benchmark is the default.

ISO 27001:2013

3. Defender for Cloud initiatives are defined in?

[X] Azure Policy

Correct. Azure Policy is used to define initiatives.

Secure Score

Workbooks

# Summary and resources

Microsoft Defender for Cloud provides a hybrid cloud security posture management.

Security posture management includes:

-   Security recommendations
-   Secure Score
-   Regulatory Compliance
-   Azure Security Benchmark

You should now be able to:

-   Review your regulator compliance
-   Review your Secure Score
-   Implement security recommendations

## Learn more

You can learn more by reviewing the following.

[Become a Microsoft Defender for Cloud Ninja (microsoft.com)](https://techcommunity.microsoft.com/t5/azure-security-center/become-an-azure-security-center-ninja/ba-p/1608761)

[Microsoft Tech Community Security Webinars](https://techcommunity.microsoft.com/t5/microsoft-security-and/security-community-webinars/ba-p/927888)