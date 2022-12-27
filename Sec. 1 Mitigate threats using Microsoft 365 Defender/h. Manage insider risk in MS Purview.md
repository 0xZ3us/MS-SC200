# Insider risk management overview

In March of 2019, a large auto manufacturer with state-of-the-art, proprietary operations and technology filed a lawsuit against four former employees and a competitor for corporate espionage. The lawsuit was filed after discovering that the employees had downloaded proprietary warehouse schematics and operational procedures before leaving the company and shared them with the competitor.

Trusting employees is key to fostering a dynamic and productive workplace. But with trust also comes risk. Companies need to be able to quickly identify and manage risk from insiders (employees or contractors with corporate access) to minimize the negative impact to their business. Insider threats and risks from illegal, inappropriate, unauthorized, or unethical behavior and actions are a major issue for all companies and can easily go undetected until it is too late. A survey by Crowd Research Partners in 2018 indicated that 90% of organizations feel vulnerable to insider risks and 53% confirmed insider risks against their organization in the previous 12 months. According to a Carnegie Mellon CERT study, 92% of insider threat cases were preceded by a negative work event, such as a termination, demotion, or dispute with a supervisor. And in 2016, Deloitte reported that 59% of employees who leave an organization voluntarily or involuntarily say they take sensitive data with them and that 51% of employees involved in an insider threat incident had a history of violating IT security policies leading up to the incident.

[![Infographic that describes the path to malicious insider risk.](https://learn.microsoft.com/en-us/training/wwl/m365-compliance-insider-manage-insider-risk/media/path-to-insider-risk.png)](https://learn.microsoft.com/en-us/training/wwl/m365-compliance-insider-manage-insider-risk/media/path-to-insider-risk.png#lightbox)

[The path has five key indicators: predisposition, stressor, concerning behavior, planning and preparation, and finally risk. Key statistics from studies by Deloitte, Stanford, and Carnegie Melon found the following: 51% of employees involved in an insider threat incident had a history of violating IT security policies leading up to the incident. 92% of insider threat cases were preceded by a negative work event, such as a termination, demotion, or dispute with a supervisor. Unmet expectations were identified in 21.6% of sabotage incidents (promotion, financial rewards, recognition, etc.) 97% of insider threat cases involved an employee whose behavior a supervisor had flagged, but the organization had failed to follow up. 59% of employees who leave an organization voluntarily or involuntarily say they take sensitive data with them.](https://learn.microsoft.com/en-us/training/wwl/m365-compliance-insider-manage-insider-risk/media/path-to-insider-risk.png#lightbox)

The financial impact of insider threats is substantial, as companies suffer market, legal, reputational, and productivity losses. According to the Ponemon Institute, the average cost of an insider incident arising from negligence is over USD307,000. If the insider is malicious, it's over USD750,000. Aside from financial loss, the impacts of insider risk can include damage to brand and reputation, competitive disadvantage, noncompliance with regulations, and loss of market share.

Traditional approaches to identifying insider risks such as user behavior analytics, monitoring user activity, and data loss prevention can suffer from limitations such as complex deployment scenarios, limited insights, and a lack of workload integration beyond SecOps.

The insider risk management solution in Microsoft Purview leverages the Microsoft Graph, security services and connectors to human resources (HR) systems like SAP, to obtain real-time native signals such as file activity, communications sentiment, abnormal user behaviors, and resignation date. A set of configurable policy templates tailored specifically for risks – such as digital IP theft, confidentiality breach, and HR violations – use machine learning and intelligence to correlate these signals to identify hidden patterns and risks that traditional or manual methods might miss. These built-in policy templates allow you to identify and mitigate risky activities while balancing employee privacy versus organization risk with privacy-by-design architecture. Finally, end-to-end integrated workflows ensure that the right people across security, HR, legal, and compliance are involved to quickly investigate and take action once a risk has been identified.

Watch the video below to learn how insider risk management can help your organization prevent, detect, and contain risks while prioritizing your organization values, culture, and employee experience:

[Video](https://www.microsoft.com/en-us/videoplayer/embed/RE4xnQE?postJsllMsg=true)

 Note

This feature is a capability included with:

-   Microsoft 365 E5
-   Microsoft 365 E5 Compliance
-   Microsoft 365 E5 Insider Risk Management

Please review [Microsoft 365 licensing guidance for security & compliance](https://learn.microsoft.com/en-us/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance) to identify required licenses for your organization.

## Risk Pain Points in the Modern Workplace

Managing and minimizing risk in your organization starts with understanding the types of risks found in the modern workplace. Some risks are driven by external factors such as bad actors who try to steal employee credentials through brute force or phishing attacks. Other risks are driven by internal events and employee activities that can be eliminated and avoided. Some examples of internal risks from employees include:

[![Infographic displaying a list of the range of risks posed by insiders.](https://learn.microsoft.com/en-us/training/wwl/m365-compliance-insider-manage-insider-risk/media/broad-range-of-risks.png)](https://learn.microsoft.com/en-us/training/wwl/m365-compliance-insider-manage-insider-risk/media/broad-range-of-risks.png#lightbox)

[Possible risks include: data spillage, confidentiality violations, IP theft, workplace violence, fraud, policy violations, insider trading, conflicts of interest, sensitive data leaks, workplace harassment, security violations, and regulatory compliance violations.](https://learn.microsoft.com/en-us/training/wwl/m365-compliance-insider-manage-insider-risk/media/broad-range-of-risks.png#lightbox)

-   Intellectual property (IP) theft
-   Espionage
-   Leaks of sensitive business assets
-   Confidentiality violations
-   Sabotage
-   Fraud
-   Insider trading
-   Code-of-conduct violations
-   Regulatory compliance violations

Insider risks vary by industry. In healthcare, internal fraud is the most frequently cited type of risk, while sabotage represents the greatest risk to IT businesses.

The path leading to a malicious insider risk varies. It may be an employee who has a history of violating IT security policies, a negative work event such as termination or a dispute with a supervisor, or employees who take sensitive data before leaving the company voluntarily or involuntarily.

[![Infographic that shows some examples of common insider risks including their cause and potential impact.](https://learn.microsoft.com/en-us/training/wwl/m365-compliance-insider-manage-insider-risk/media/examples-common-insider-risks.png)](https://learn.microsoft.com/en-us/training/wwl/m365-compliance-insider-manage-insider-risk/media/examples-common-insider-risks.png#lightbox)

[Causes of insider risk may include espionage (state-sponsored and corporate), or manipulation of an insider by an adversary to gain access or information for intelligence, blackmail, or economic advantage. Fraud, where an insider establishes a family business as a vendor and then awards the company millions of dollars in contracts. Loss of sensitive business assets (intentional or unintentional) where an insider steals intellectual property, such as patents, trade secrets, or research and development information. Sabotage, where an insider deletes backups and erases the production database before leaving the company. Physical violence, where an employee exhibits inappropriate behavior that negatively impacts employee productivity. Potential impacts of these events include financial loss, brand damage, a competitive disadvantage, noncompliance with applicable regulations, or a loss of market share.](https://learn.microsoft.com/en-us/training/wwl/m365-compliance-insider-manage-insider-risk/media/examples-common-insider-risks.png#lightbox)

## Common insider risk scenarios

The insider risk management solution in Microsoft Purview can help you detect, investigate, and take action to mitigate internal risks in your organization in common scenarios, such as:

-   **Data theft by departing employee.** When employees leave an organization, either voluntarily or as the result of termination, there is often legitimate concerns that company, customer, and employee data are at risk. Employees may innocently assume that project data isn't proprietary, or they may be tempted to take company data for personal gain and in violation of company policy and legal standards.
-   **Leak of sensitive or confidential information.** In most cases, employees try their best to properly handle sensitive or confidential information. But occasionally employees make mistakes and information is accidentally shared outside your organization or in violation of your information protection policies. Sometimes employees may intentionally leak or share sensitive and confidential information with malicious intent and for potential personal gain.
-   **Actions and behaviors that violate corporate policies.** Employee-to-employee communications are often a source of inadvertent or malicious violations of corporate policies. These violations can include offensive language, threats, and cyber-bullying between employees. This type of activity contributes to a hostile work environment and can result in legal actions against both employees and the larger organization.

## Insider risk management workflow

Using policy templates with pre-defined conditions and comprehensive activity signaling across the Microsoft 365 service, you can use actionable insights to quickly identify and resolve risky behavior.

Identifying and resolving internal risk activities and compliance issues with Microsoft Purview Insider Risk Management uses the following workflow:

[![Infographic shows the flow of an insider risk case: policy, alert triage, investigate, and action. This is a collaboration by Compliance, Human Resources, Legal, and Security.](https://learn.microsoft.com/en-us/training/wwl/m365-compliance-insider-manage-insider-risk/media/insider-risk-management-workflow.png)](https://learn.microsoft.com/en-us/training/wwl/m365-compliance-insider-manage-insider-risk/media/insider-risk-management-workflow.png#lightbox)

**1. Policies.** Insider risk management policies determine which employees are in-scope and which types of risk indicators are configured for alerts.

**2. Alerts.** Insider risk management alerts are automatically generated by risk indicators defined in insider risk management policies. These alerts give compliance analysts and investigators an all-up view of the current risk status and allow your organization to triage and take actions for discovered risks.

**3. Triage.** Reviewers can quickly identify insider risk alerts and examine each to evaluate and triage. Alerts are resolved by opening a new case, assigning the alert to an existing case, or dismissing the alert.

**4. Investigate.** Cases are manually created from alerts in the situations where further action is needed to address an issue for an employee.

**5. Action.** After investigating the details of a case, you can take action by sending the employee a notice, resolving the case as benign, or escalating to a data or employee investigation.

## Learn more

-   [Crowd Research Partners, Insider Threat Report](https://crowdresearchpartners.com/portfolio/insider-threat-report/)
-   [Carnegie Mellon CERT study: The "Big Picture" of Insider IT Sabotage Across U.S. Critical Infrastructures](https://resources.sei.cmu.edu/asset_files/TechnicalReport/2008_005_001_14981.pdf)
-   [Carnegie Mellon University: Insider Threats in Healthcare](https://insights.sei.cmu.edu/insider-threat/2019/02/insider-threats-in-healthcare-part-7-of-9-insider-threats-across-industry-sectors.html)

# Introduction to managing insider risk policies

## Components of a policy

Insider risk management policies are created using pre-defined templates and policy conditions. The conditions define the risk indicators that correspond to particular risk activities that can be identified and examined in Microsoft Purview feature areas. These conditions also include the users added to the policy, which services are prioritized, and the monitoring time period.

## Policy dashboard

The **Policy dashboard** allows you to quickly see the policies in your organization and the current status of alerts associated with each policy.

-   **Policy name:** The name assigned to the policy in the policy wizard.
-   **Active alerts:** The number of active alerts for each policy.
-   **Confirmed alerts:** The total number of alerts that resulted in cases from the policy in the last 365 days.
-   **Actions taken on alerts:** The total number of alerts that were confirmed or dismissed for the last 365 days.
-   **Policy effectiveness:** The percentage determined by total confirmed alerts divided by total actions taken on alerts (which is the sum of alerts that were confirmed or dismissed over the past year).
-   **Active:** The status of the policy.

[![Screenshot of the Policies tab where new policies can be created.](https://learn.microsoft.com/en-us/training/wwl/m365-compliance-insider-manage-insider-risk/media/policy-template.png)](https://learn.microsoft.com/en-us/training/wwl/m365-compliance-insider-manage-insider-risk/media/policy-template.png#lightbox)

[The Policies tab lists existing policies and the number active alerts, number confirmed alerts, number of actions taken, and effectiveness percentage for each policy.](https://learn.microsoft.com/en-us/training/wwl/m365-compliance-insider-manage-insider-risk/media/policy-template.png#lightbox)

## Policy templates

Insider risk management templates contain pre-defined policy conditions that define the types of risk indicators monitored by a policy. Before you can create a policy, you need to assign a template to it in the policy creation wizard. Currently, you can choose from one of the following types of templates.

### Departing employee data theft

This policy template prioritizes the risk indicators that are associated with data theft by departing employees and focuses detection and alerts to this risk area. Indicators may include activities such as downloading files from SharePoint Online, copying files to portable devices such as USB drives, printing files, and copying data to personal cloud messaging and storage services near an employee's resignation and end dates.

### Data leaks

Data leaks include accidental oversharing of information outside your organization or data theft with malicious intent. This policy template prioritizes detection of suspicious SharePoint Online data downloads, file and folder sharing, copying files to portable devices such as USB drives, printing files, and copying data to personal cloud messaging and storage services.

## Policy settings

Insider risk settings apply to all insider risk management policies, regardless of the template you chose when creating a policy. Settings are configured using the **Insider risk settings** control located at the top of all insider risk management tabs. These settings control privacy, indicators, monitoring windows, and intelligent detections.

### Privacy

Protecting the privacy of users that have policy matches is important and can help promote objectivity in data investigation and analysis reviews for insider risk alerts. For users with insider risk policy matches, you can choose one of the following settings:

-   **Show anonymized versions of usernames:** Usernames are anonymized to prevent admins, data investigators, and reviewers from seeing who is associated with policy alerts. For example, a user 'Grace Taylor' would appear with a randomized pseudonym such as 'AnonIS8-988' in all areas of the insider risk management experience. Choosing this setting anonymizes all users with current and past policy matches and applies to all policies. If you choose to turn off this setting, usernames and user profile information will be displayed for all users that have current or past policy matches.
-   **Do not show anonymized versions of usernames:** Usernames and user profile information such as name, title, alias, and organization or department is displayed for the user for all insider risk management alerts and cases.

[![Screenshot of the Privacy tab in Settings. The option Show anonymized versions of usernames is checked and Do not show anonymized versions of usernames is unchecked.](https://learn.microsoft.com/en-us/training/wwl/m365-compliance-insider-manage-insider-risk/media/privacy-setting.png)](https://learn.microsoft.com/en-us/training/wwl/m365-compliance-insider-manage-insider-risk/media/privacy-setting.png#lightbox)

### Indicators

Each policy template is based on specific indicators that correspond to particular risk activities and alerts are triggered by policies when users perform activities related to these indicators. To define the indicators that are enabled in all policies, navigate to **Settings> Indicators** and select one or more indicators. You must select one or more indicators before you can receive alerts for risky activity defined in your policies.

[![Screenshot of the Indicators tab in Settings.](https://learn.microsoft.com/en-us/training/wwl/m365-compliance-insider-manage-insider-risk/media/indicator-setting.png)](https://learn.microsoft.com/en-us/training/wwl/m365-compliance-insider-manage-insider-risk/media/indicator-setting.png#lightbox)

[Select all is chosen, which includes the following settings: sharing files from SharePoint Online, Sharing folders from SharePoint Online, Sharing SharePoint Online sites, Downloading content from SharePoint Online, Emailing outside the organization, Copying sensitive or classified files to USB, Copying sensitive or classified files to cloud, Printing sensitive or classified documents, Use of offensive language in email, Past policy violations, and Measure anomalous activity.](https://learn.microsoft.com/en-us/training/wwl/m365-compliance-insider-manage-insider-risk/media/indicator-setting.png#lightbox)

### Policy timeframes

Policy timeframes allow you to define past and future review periods that are triggered after policy matches based on events and activities for the insider risk management policy templates. You can choose from the following timeframes for all policy templates:

-   **Activation window:** The number of days, 1 to 30, that the window activates _after_ a triggering event occurs for any user assigned to the policy. For example, assume you've configured an insider risk management policy and set the **Activation window** to 30 days. Several months have passed since you configured the policy and a triggering event occurs for one of the users included in the policy. The triggering event activates the Activation window and the policy is active for that user for the next 30 days.
-   **Past activity detection:** The number of days, 0 to 90, that the window activates _before_ a triggering event occurs for any user assigned to the policy. For example, assume you've configured an insider risk management policy and set the Past activity detection to 90 days. Several months have passed since you configured the policy and a triggering event occurs for one of the users included in the policy. The triggering event activates the Past activity detection and the policy gathers historic activities for that user for 90 days prior to the triggering event.

[![Screenshot of the Policy timeframes tab in Settings. It shows the activation window is set to 30 days and past activity detection is set to 90 days.](https://learn.microsoft.com/en-us/training/wwl/m365-compliance-insider-manage-insider-risk/media/insider-risk-settings-timeframes.png)](https://learn.microsoft.com/en-us/training/wwl/m365-compliance-insider-manage-insider-risk/media/insider-risk-settings-timeframes.png#lightbox)

### Intelligent detections

In certain circumstances, you may want to define certain file types to ignore or to enforce a detection level for files to help define a minimum bar for alerts. When using offensive language policies, you may need to increase or decrease the detection sensitivity to control the amount of reported policy matches. Intelligent detection settings enable you to control file type exclusions, file volume limits, and the offensive language detection sensitivity.

#### Anomaly detections

Anomalous detections include settings for file type exclusions and file volume limits.

-   **File type exclusions:** To exclude specific file types from all insider risk management policy matching, enter file type extensions separated by commas. For example, to exclude certain types of music files from policy matches you may enter **aac,mp3,wav,wma** in the **File type exclusions** field. Files with these extensions would be ignored by all insider risk management policies.
-   **File volume cut off limit:** To define a minimum file level before activity alerts are reported in insider risk policies, enter the number of files. For example, you would enter '10' if you do not want to generate insider risk alerts when a user downloads 10 files or less, even if your policies consider this an anomaly.

#### Offensive language detections

To adjust the sensitivity of the offensive language classifier for policies using the **Offensive language in email** template, choose one of the following settings:

-   **Low:** The lowest sensitivity level with the broadest range for detection offensive language and sentiment. The probability of false positives for offensive language matching is elevated.
-   **Medium:** The mid-level sensitivity level with a balanced range for detection offensive language and sentiment. The probability of false positives for offensive language matching is average.
-   **High:** The highest sensitivity level with a narrow range for detection offensive language and sentiment. The probability of false positives for offensive language matching is low.

[![Screenshot of the Intelligent detections tab in Settings.](https://learn.microsoft.com/en-us/training/wwl/m365-compliance-insider-manage-insider-risk/media/intelligent-decisions-setting.png)](https://learn.microsoft.com/en-us/training/wwl/m365-compliance-insider-manage-insider-risk/media/intelligent-decisions-setting.png#lightbox)

[It includes a file type exclusions field, a numeric file volume cut off limits setting, and an offensive language detection slider that is set to high.](https://learn.microsoft.com/en-us/training/wwl/m365-compliance-insider-manage-insider-risk/media/intelligent-decisions-setting.png#lightbox)

# Create and manage insider risk policies

## Prerequisites & permissions

Before you can begin creating insider risk policies, there are several requirements that need to be met.

### Turn on audit logging

Insider risk management uses audit logs for user insights and activities configured in policies. The audit logs are a summary of all activities associated with an insider risk management policy or anytime a policy is modified. For step-by-step instructions to turn on auditing, see [Turn Office 365 audit log search on or off](https://learn.microsoft.com/en-us/microsoft-365/compliance/turn-audit-log-search-on-or-off). After you turn on auditing, a message is displayed that says the audit log is being prepared and that you can run a search in a couple of hours after the preparation is complete.

### Assign permissions

A global administrator will need to assign you and other compliance officers to the **Insider Risk Management** or **Insider Risk Management Admin** role group by using the **Permissions** module in the Microsoft Purview compliance portal. Once you have been assigned to one of these roles, you have the ability to assign additional users to specific role groups to manage different sets of insider risk management features.

Depending on the structure of your compliance management team, you have options to assign users to specific role groups to manage different sets of insider risk management features. You have the ability to choose from the following role group options when configuring insider risk management:

-   **Insider Risk Management.** Use this role group to manage insider risk management for your organization in a single group. By adding all user accounts for designated administrators, analysts, and investigators, you can configure insider risk management permissions in a single group. This role group contains all the insider risk management permission roles. This is the easiest way to quickly get started with insider risk management and is a good fit for organizations that do not need separate permissions defined for separate groups of users.
-   **Insider Risk Management Admin.** Use this role group to initially configure insider risk management and later to segregate insider risk administrators into a defined group. Users in this role group can create, read, update, and delete insider risk management policies, global settings, and role group assignments.
-   **Insider Risk Management Analysts.** Use this group to assign permissions to users that will act as insider risk case analysts. Users in this role group can access all insider risk management alerts, cases, and notices templates. They cannot access the insider risk Content Explorer.
-   **Insider Risk Management Investigators.** Use this group to assign permissions to users that will act as insider risk data investigators. Users in this role group can access all insider risk management alerts, cases, notices templates, and the Content Explorer for all cases.

## Potential dependencies

Two of the insider risk management templates have dependencies that must be configured for policy indicators to generate relevant activity alerts. This step might be optional depending on the policy you plan to configure for your organization.

### Departing employee data theft template

If you configure a policy using the Departing employee data theft template, you'll need to configure a Microsoft 365 Human Resources (HR) data connector so that you can import user and log data from 3rd-party risk management and human resources platforms. HR connectors allow you to pull in human resources data from CSV files, including user termination and last employment dates. This data helps drive alert indicators in insider risk management policies and is an important part of configuring full risk management coverage in your organization.

The following requirements must be met before you can set up an HR connector:

-   A global administrator will need to consent to allow the Office 365 Import service to access data in your organization.
    
-   The user who creates the HR connector will need to be assigned the Mailbox Import Export role in Exchange Online.
    
-   You have to have a system in place for retrieving and exporting the data from your organization's HR system and add it to a CSV file. Once the requirements have been met, you can set up your HR connector.
    
    Briefly, the steps for creating the connector involve the following:
    
    1.  Creating an app in Azure Active Directory.
    2.  Generating the CSV file from your organization's HR system.
    3.  Creating an HR connector in the Microsoft Purview compliance portal.
    4.  Running a script that will upload the HR data in the CSV file to the Microsoft cloud.
    
    For more details, see the [Set up a connector to import HR data](https://learn.microsoft.com/en-us/microsoft-365/compliance/import-hr-data) topic.
    

### Data leaks template

Insider risk management supports using DLP policies to help identify the intentional or accidental exposure of sensitive information to unwanted parties. When configuring an insider risk management policy with the Data leaks template, you have to assign a specific DLP policy. This policy helps drive the alert indicators for sensitive information and is an important part of configuring full risk management coverage in your organization.

 Note

To reduce noise, alerts will only fire when a high volume DLP policy qualifying event is triggered. For example, an alert will fire if the policy detects 10 or more credit card numbers in an email or document, but not less. See the [Create, test, and tune a DLP policy](https://learn.microsoft.com/en-us/microsoft-365/compliance/create-test-tune-dlp-policy) topic to learn how to configure DLP policies for your organization.

## Creating a new insider risk policy

Insider risk management policies include assigned users and define which types of risk indicators are configured for alerts. Before activities can trigger alerts, a policy must be configured.

To create a new insider risk management policy, you use the policy wizard in the **Insider risk management** solution in the Microsoft Purview compliance portal. Briefly, you create a new policy by stepping through the policy wizard and policy settings to configure the following items:

-   **Policy template**
-   **Users or groups** the policy will apply to (optionally, assign higher risk scores to detected activity based on where the related content is located, what sensitive info is included, and what sensitivity labels are applied)
-   **Alert indicators** (**Indicators** need to be enabled under **Policy Settings** before they can be selected when creating a policy)
-   **Duration** (time frame) for monitoring

For more information, see [Create an insider risk policy](https://learn.microsoft.com/en-us/microsoft-365/compliance/insider-risk-management-configure?step-5-required-create-an-insider-risk-management-policy%3Fazure-portal=true).

## Learn more

-   [Compare Microsoft 365 Enterprise Plans](https://www.microsoft.com/microsoft-365/compare-microsoft-365-enterprise-plans?rtc=1%3Fazure-portal%3Dtrue)
-   [Enable permissions for insider risk management](https://learn.microsoft.com/en-us/microsoft-365/compliance/insider-risk-management-configure?step-1-required-enable-permissions-for-insider-risk-management%3Fazure-portal=true)
-   [Create, test, and tune a DLP policy](https://learn.microsoft.com/en-us/microsoft-365/compliance/create-test-tune-dlp-policy)

# Knowledge check

1. A healthcare employee left work with an unencrypted work laptop, which was stolen days later in a burglary. Data containing sensitive information for 100 patients is on the laptop. This is an example of which type of internal risk?

[X] Regulatory compliance violation

If your business handles the personal, medical, sensitive, or classified data of individuals or government organizations, the law requires you to follow strict compliance regulations.

Sabotage

Data leak

2. Which one of the following apply to Microsoft Insider Risk Management policies and templates?

Insider risk settings for **Privacy** and **Policy Indicators** can be configured to apply for a specific policy.

Insider risk settings apply to all insider risk management policies regardless of the template chosen when creating a policy.

Microsoft Insider Risk Management policies and templates are for malicious intent violations.

[X] Each policy must have a template assigned in the policy creation wizard before the policy is created.

Insider risk management templates are pre-defined policy conditions that define the types of risk indicators monitored by a policy. Each policy must have a template assigned before creation.

# Investigate insider risk alerts

## Alert dashboard

The insider risk Alert dashboard allows you to view and take action on alerts generated by insider risk policies. The Alert dashboard displays information from the previous 30 days for the following widgets:

-   Alerts to review: The total number of alerts needing review and triage are listed, including a breakdown by alert severity.
-   Open alerts over the past 30 days: The total number of alerts created by policy matches over the last 30 days, sorted by high, medium, and low alert severity levels.
-   Average time to resolve alerts: A summary of useful alert statistics:
    -   Average time to resolve high severity alerts, listed in hours, days, or months.
    -   Average time to resolve medium severity alerts, listed in hours, days, or months.
    -   Average time to resolve low severity alerts, listed in hours, days, or months.

[![Screenshot of the Alerts tab that shows 3 alerts currently need review in addition to a chart of the open alerts over the past 30 days, and a list of each alert.](https://learn.microsoft.com/en-us/training/wwl/m365-compliance-insider-manage-insider-risk/media/resolve-alerts.png)](https://learn.microsoft.com/en-us/training/wwl/m365-compliance-insider-manage-insider-risk/media/resolve-alerts.png#lightbox)

 Note

Insider risk management uses built-in alert throttling to help protect and optimize your risk investigation and review experience. This throttling guards against issues that might result in an overload of policy alerts, such as misconfigured data connectors or DLP policies. As a result, there might be a delay in displaying new alerts for a user.

## Alert status and severity

As alerts start showing up, you can review them and investigate each by clicking on it and analyzing the signals in the Alert details pane. Once you have analyzed an alert, you can assign it to one of the following statuses:

-   **Confirmed.** Creates a case to further investigate the alert.
-   **Dismissed.** Identifies it as a false positive.
-   **Needs review.** The alert requires further analysis to define an action.
-   **Resolved.** The case to which this alert was assigned has been closed.

Alert risk scores are automatically calculated from several risk activity attributes that include:

-   The type of risk activity.
-   The number and frequency of the activity occurrence.
-   The history of user risk activity.
-   The addition of activity risks that may boost the seriousness of the activity.

The alert risk score drives the programmatic assignment of a risk severity level for each alert and cannot be customized. If alerts remain untriaged and risk activities continue to be added to the alert, the risk severity level can increase. Risk analysts and investigators can use the alert risk severity to help triage alerts in accordance to your organization's risk policies and standards.

The alert risk severity levels are:

-   **High severity:** The activity and indicators for the alert pose significant risk. The associated risk activities are serious, repetitive, and correlate strongly to other significant risk factors.
-   **Medium severity:** The activity and indicators for the alert pose a moderate risk. The associated risk activities are moderate, frequent, and have some correlation to other risk factors.
-   **Low severity:** The activity and indicators for the alert pose a minor risk. The associated risk activities are minor, more infrequent, and do not correlate to other significant risk factors.

## Filtering and searching alerts

Depending on the number and type of active insider risk management policies in your organization, reviewing a large queue of alerts can be challenging. Using filters can help analysts and investigators sort alerts by several attributes. Selecting the **Filter** control on the **Alerts** dashboard lets you filter alerts by one or more of the following attributes:

-   **Status:** Select one or more status values to filter the alert list. The options are **Confirmed**, **Dismissed**, **Needs review**, and **Resolved**.
-   **Severity:** Select one or more alert risk severity levels to filter the alert list. The options are **High**, **Medium**, and **Low**.
-   **Time detected:** Select the **start** and **end** dates for when the alert was created.
-   **Policy:** Select one or more policies to filter the alerts generated by the selected policies.

To search the alert name for a specific word, select the **Search** control and type the word to search. The search results display any policy alert containing the word defined in the search.

# Take action on insider risk alerts through cases

## Case overview

Alerts can be assigned to a case so that you can conduct a detailed investigation from the **Cases** section in the insider risk management console. You can review the individual signals that triggered the case in a timeline, review the affected content, add notes, or invite additional contributors in the investigation in order to reach a conclusion.

A case investigation may end up with a notice being sent to the offending employee. Other cases might require you to create an eDiscovery case which will enable you to collect, preserve, review, analyze and export data related to the user in question in order to conclude whether there was an actual threat and its scope. In most cases, the eDiscovery case will be managed by a different person with the necessary roles and privileges to manage eDiscovery (Premium) cases.

Once an investigation has concluded and the necessary actions have been taken, the case can be closed by resolving the case as either benign or a confirmed policy violation with specific actions taken.

To learn more about eDiscovery (Premium) cases, see [Overview of eDiscovery (Premium) in Microsoft Purview](https://learn.microsoft.com/en-us/microsoft-365/compliance/overview-ediscovery-20).

## Case dashboard

The insider risk management **Cases dashboard** allows you to view and take action on cases. The **Cases dashboard** displays information from the previous 30 days for the following widgets:

-   **Active cases:** The total number of active cases under investigation.
-   **Cases over the past 30 days:** The total number of cases created, sorted by **Active** and **Closed** status.
-   **Statistics:** Average time of active cases, listed in hours, days, or months.

The case queue lists all active and closed cases for your organization, in addition to the current state of the following case attributes:

-   **Case name:** The name of the case, defined when an alert is confirmed and the case is created.
-   **Status:** The status of the case, either **Active** or **Closed**.
-   **User:** The employee for the case.
-   **Time case opened:** The time that has passed since the case was opened.
-   **Total policy alerts:** The number of policy matches included in the case. This number may increase if new alerts are added to the case.
-   **Last updated:** The time that has passed since there has been an added case note or change in the case state.
-   **Last updated by:** The name of the insider risk management analyst or investigator that last updated the case.

[![Screenshot of the Case tabs in Insider Risk Management.](https://learn.microsoft.com/en-us/training/wwl/m365-compliance-insider-manage-insider-risk/media/active-cases.png)](https://learn.microsoft.com/en-us/training/wwl/m365-compliance-insider-manage-insider-risk/media/active-cases.png#lightbox)

[The Case tab shows 2 currently active cases, the number of active and closed cases over the past 30 days, and a list of each case including its name, status, the user, the time opened, and the total number of policy alerts.](https://learn.microsoft.com/en-us/training/wwl/m365-compliance-insider-manage-insider-risk/media/active-cases.png#lightbox)

The Search control is used to search case names for specific text and use the case filter to sort cases by the following attributes:

-   **Status**
-   **Time case opened**, start date, and end date
-   **Last updated**, start date, and end date

## Working with cases

Selecting a case opens the case management tools and allows analysts and investigators to dig into the details of cases. Let's examine each of the tabs available to you.

### Case overview

The **Case overview** tab summarizes the alert activity and risk level history for the case.

The **Alerts** widget shows the policy matches for the case, the status of the alert, the alert risk severity, and when the alert was detected.

The **Risk level history** chart displays the user risk level over the last 30 days. The line chart allows analysts and investigators to quickly see the trend in overall user risk over time.

The **Risk activity content** widget summarizes the types of data and content contained in alerts added to the case. This widget gives an all-up view of the entire data and content set at risk in the case.

The **Case details** pane summarizes the case details for risk analysts and investigators and includes the following areas:

-   **Case name:** The name of the case, prefixed with an autogenerated case sequence number and the name of the risk associated with the policy template that the first confirmed alert matches.
-   **Case status:** The current status of the case, either **Active** or **Closed**.
-   **User's risk score:** The current calculated risk level of the user for the case. This score is calculated every 24 hours and uses the alert risk scores from all active alerts associated to the user.
-   **Alerts confirmed:** List of alerts for the user confirmed for the case.
-   **Content at risk:** List of content, sorted by content sources and types. For example, for case alert content in SharePoint Online, you may see folder or file names listed that are associated with the risk activity for alerts in the case.

### Alerts

The **Alerts** tab summarizes the status, severity, and time detected for current alerts included in the case. New alerts may be added to an existing case and added to the **Alert** queue as they are assigned. Selecting an alert from the queue displays the **Alert detail** page. The **Search** control can be used to search alert names for specific text while the **Filter** control can be used to sort cases by the following attributes:

-   **Status**
-   **Severity**
-   **Time detected**, start date, and end date

### User activity

The **User activity** tab is one of the most powerful tools for internal risk analysis and investigation for cases in the insider risk management solution. This tab is structured to enable quick review of a case, including a historical timeline of all alerts, alerts details, the current risk score for the user in the case, and controls to take effective action to contain the risks in the case.

[![Screenshot of the User activity tab that shows a timeline of activities, case details, and user details.](https://learn.microsoft.com/en-us/training/wwl/m365-compliance-insider-manage-insider-risk/media/user-activity.png)](https://learn.microsoft.com/en-us/training/wwl/m365-compliance-insider-manage-insider-risk/media/user-activity.png#lightbox)

-   **Date and window time filters:** By default, the last six months of alerts confirmed in the case are displayed in the User activity chart. You can filter the chart view with either the slider controls at both ends of the chart window, or by defining specific start and end dates in the chart filter control.
-   **Risk alert activity and details:** Risk activities are displayed as colored bubbles in the User activity chart. Bubbles are created for different categories of risk and the bubble size is proportional to the number of risk activities for the category. Selecting a bubble displays the following details for each risk activity:
    -   **Date** of the risk activity.
    -   **Risk activity category**. For example, Email(s) with attachments sent outside the organization or File(s) downloaded from SharePoint Online.
    -   **Risk score** for the alert. This score is the numerical score for the alert risk severity level.
    -   **Number of events** associated with the alert. Links to each file or email associated with the risk activity is also available.
-   **Risk activity legend:** Across the bottom of the user activity chart, a color-coded legend helps you quickly determine risk category for each alert.
-   **Risk activity chronology:** The full chronology of all risk alerts associated with the case are listed, including all the details available in the corresponding alert bubble.
-   **Case actions:** Options for resolving the case are on the case action toolbar. You can resolve a case, send an email notice to the employee, or escalate the case for a data or employee investigation.

### Content explorer

The **Content explorer** tab grants users with two roles access: The **Content Explorer List viewer** membership allows you to see each item and its location in list view and the data classification **list viewer** role is pre-assigned to this role group. The **Content Explorer Content viewer** membership on the otherhand allows you to view the contents of each item in the list. The data classification **content viewer** role is pre-assigned to this role group to review copies of all individual files and email messages associated with risk alerts. For example, if an alert is created when an employee downloads hundreds of files from SharePoint Online to a USB device and the activity triggers a policy alert, all the downloaded files for the alert are captured and copied to the insider risk management case from original storage sources.

[![Screenshot of the Content explorer tab that lists the emails and files flagged by the policy alert as well as an overview of case details in a pane on the far right.](https://learn.microsoft.com/en-us/training/wwl/m365-compliance-insider-manage-insider-risk/media/content-explorer.png)](https://learn.microsoft.com/en-us/training/wwl/m365-compliance-insider-manage-insider-risk/media/content-explorer.png#lightbox)

**Content explorer** is a powerful tool with basic and advanced search and filtering features that shows a current snapshot of the items that have a sensitivity label, a retention label or have been classified as a sensitive information type in your organization.

To learn more about using the content explorer, see [Insider risk management content explorer](https://learn.microsoft.com/en-us/microsoft-365/compliance/insider-risk-management-content-explorer).

### Case notes

The **Case notes** tab enables risk analysts and investigators to comment, feedback, and add insight about their work for the case. Notes are permanent additions to a case and cannot be edited or deleted after the note is saved. When a case is created from an alert, the comments entered in the **Confirm alert and create insider risk case** dialog are automatically added as a case note.

### Contributors

The **Contributors** tab in the case is where risk analysts and investigators can add other reviewers to the case. By default, all users assigned the **Insider Risk Management Analysts** and **Insider Risk Management Investigators** roles are listed as contributors for each active and closed case. All insider risk management cases must be managed with appropriate access controls in place to maintain confidentiality and integrity of the investigation. To help maintain access control of cases, users are assigned one of two types of access to cases:

-   **Permanent access**. Permanent access is automatically granted to users with the **Insider Risk Management Analysts** and **Insider Risk Management Investigators** roles when the case is created from an alert. Permanent access grants full control of the case for the lifetime of the case and grants the ability to add other case contributors.
-   **Temporary access**. Temporary access is only granted to users by contributors that have permanent access for the case. Typically, this access level is granted to users that needs to add notes to a case. Contributors with temporary access have all case management control except:
    -   Permission to confirm or dismiss alerts
    -   Permission to edit the contributors for cases
    -   Permission to view files and messages in the Content Explorer

## Case actions

Risk analysts and investigators can take action on a case in one of several methods, depending on the severity of the case, the history of risk of the employee, and the risk guidelines of your organization. In some situations, you may need to escalate a case to an employee or data investigation to collaborate with other areas of your organization and to dive deeper into risk activities. Insider risk management is tightly integrated with other Microsoft Purview features such as eDiscovery (Premium) to help you with end-to-end resolution management.

### Send a notice

In most cases, employee actions that create policy match alerts are inadvertent or accidental. Sending a reminder notice to the employee via email is an effective method for documenting case review and action, as well as a method to remind employees of corporate policies or point them to refresher training. Notices are generated from notice templates that you create for your insider risk management infrastructure. It's important to remember that sending a notice to an employee _does not_ resolve the case as **Closed**. In some cases, you may want to leave a case open after sending a notice to an employee to look for additional risk activities without opening a new case. If you want to resolve a case after sending a notice, you must select the **Resolve case** as a follow-on step after sending a notice.

### Escalate for investigation

Cases may need to be escalated in situations where additional legal review is needed for the employee's risk activity. This escalation opens a new eDiscovery (Premium) case in your Microsoft 365 organization. eDiscovery (Premium) provides an end-to-end workflow to preserve, collect, review, analyze, and export content that's responsive to your organization's internal and external legal investigations. It also lets your legal team manage the entire legal hold notification workflow to communicate with custodians involved in a case. Assigning a reviewer as a custodian in an eDiscovery (Premium) case created from an insider risk management case helps your legal team take appropriate action and manage content preservation. After the insider risk management case has been escalated to a new employee investigation case, you can review the new case in the **eDiscovery> Advanced** area in the Microsoft Purview compliance portal.

### Resolve the case

After risk analysts and investigators have completed their review and investigation, a case can be resolved to take action on all the alerts currently included in the case. Resolving a case adds a resolution classification, changes the case status to **Closed**, and automatically adds the resolution action added to the case notes queue on the **Case notes** dashboard. Cases are resolved as either:

-   **Benign:** The classification for cases where policy match alerts are evaluated as low risk, non-serious, or false positive.
-   **Confirmed policy violation:** The classification for cases where policy match alerts are evaluated as risky, serious, or the result of malicious intent.

## Insider risk management notice templates

**Insider risk management notice templates** allow you to send email messages to employees when their activities generate a policy match and alert. Notices serve as simple reminders to employees to be more careful or to provide links or information for refresher training or corporate policy resources. Notices can be an important part of your internal compliance training program and can help create a documented audit trail for employees with recurring risk activities.

The **Notices templates dashboard** displays a list of configured notice templates and allows you to create new notice templates. The notice templates are listed in reverse date order with the most recent notice template listed first.

[![Screenshot of the Notice templates tab that shows two existing templates: Employee code of conduct reminder and Confidentiality obligation reminder.](https://learn.microsoft.com/en-us/training/wwl/m365-compliance-insider-manage-insider-risk/media/notice-templates.png)](https://learn.microsoft.com/en-us/training/wwl/m365-compliance-insider-manage-insider-risk/media/notice-templates.png#lightbox)

If you'd like to create more than a simple text-based email message for notifications, you can create a more detailed message by [using the HTML in the message body field](https://learn.microsoft.com/en-us/microsoft-365/compliance/insider-risk-management-notices?html-for-notices%3Fazure-portal=true) of a notice template.

[Learn more about creating, updating, and deleting notice templates.](https://learn.microsoft.com/en-us/microsoft-365/compliance/insider-risk-management-notices)

### Explore how to minimize internal risks

View a [video version](https://www.microsoft.com/videoplayer/embed/RE4yghe) of the interactive guide (captions available in more languages).

[![Cover for an interactive guide that says Minimize internal risks with Microsoft Purview Insider Risk Management.](https://learn.microsoft.com/en-us/training/wwl/m365-compliance-insider-manage-insider-risk/media/minimize-internal-risks-with-insider-risk-management-in-microsoft-365.png)](https://mslearn.cloudguides.com/guides/Minimize%20internal%20risks%20with%20insider%20risk%20management%20in%20Microsoft%20365)

# Summary and knowldge check

Insider threats and risks from illegal, inappropriate, unauthorized, or unethical behavior and actions are a major issue for all companies and can easily go undetected until it is too late. From IP theft to data leaks to many other scenarios, protecting the data within an organization from inadvertent or malicious actions is paramount for any organization. Microsoft's insider risk management policies can help organizations minimize threats while achieving the right balance between keeping their data protected and their people productive.

Now that you have completed this module, you should be able to:

-   Explain how Microsoft Purview Insider Risk Management can help prevent, detect, and contain internal risks in an organization
-   Describe the types of built-in, pre-defined policy templates.
-   List the prerequisites that need to be met before creating insider risk policies.
-   Explain the types of actions you can take on an insider risk management case.

## Check your knowledge

1. If you want to define past and future review periods that are triggered after policy matches based on events and activities for the insider risk management policy templates, which policy setting do you select?

Indicators

[X] Policy timeframes

Depending on the template, you select the timeframes available are activation window and past activity detection.

Intelligent detections

2.  Configuring a Microsoft Human Resources (HR) data connector is a dependency for which insider risk management template?

[X] Departing employee's data theft template

If you configure a policy using the Departing employee data theft template, you'll need to configure a Microsoft 365 HR data connector so that you can import user and log data from 3rd-party risk management and human resources platforms. HR connectors allow you to pull in human resources data from CSV files, including user termination and last employment dates.

Data leaks

Offensive language in email

3. You create a new policy by stepping through the policy wizard and policy settings. Which of the following is optional when creating a new policy?

The users or groups the policy will apply to

Alert indicators

[X] Specify content to prioritize

This is optional, you can assign the sources to prioritize for risky user activity such as SharePoint sites.

4.  You want to search for insider risk alerts that occurred in the past 30 days and are high severity risks. The easiest way to accomplish this is to do which of the following?

From the Alerts dashboard search for “last 30 days.”

Click “Export” to download a CSV file with all alerts. Import this into Excel and use the filter function.

[X] From the Alerts dashboard, select the Filter control.

You can filter alerts by one of more attributes including Status, Severity, Time detected, and Policy.

5. Which of the case actions opens a new eDiscovery (Premium) case in your Microsoft O365 investigation?

[X] Escalate for investigation

Escalate the case for employee investigation in situations where additional legal review is needed for the employee's risk activity. This escalation opens a new eDiscovery (Premium) case in your Microsoft 365 organization. eDiscovery (Premium) provides an end-to-end workflow to preserve, collect, review, analyze, and export content that's responsive to your organization's internal and external legal investigations.

Send a notice

Resolve the case
