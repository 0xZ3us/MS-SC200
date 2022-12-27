https://learn.microsoft.com/en-us/training/modules/query-logs-azure-sentinel/

# Introduction

Microsoft Sentinel collects log data that is stored in tables. The Logs page in Microsoft Sentinel provides a user interface to build and view query results using the Kusto Query Language (KQL). KQL is the query language used to perform data analysis to create analytics, workbooks, and perform hunting with Microsoft Sentinel.

You're a Security Operations Analyst working at a company that is implementing Microsoft Sentinel. You must explore the tables available in your workspace. The Logs page using Microsoft Sentinel allows you to write Kusto Query Language (KQL) statements to view data stored in the tables. When you connect log data to the Microsoft Sentinel workspace, the connectors will write data to specific tables.

You need to have a basic understanding of the provided tables and their intended purpose. For example, the "SecurityEvents" table is designed for Windows Security Event log data. With this knowledge, you'll be able to query the required tables to use in your search for malicious activity.

After completing this module, you'll be able to:

-   Use the Logs page to view data tables with Microsoft Sentinel
-   Query the most used tables using Microsoft Sentinel

# Query logs in the logs page

KQL is the language used to query the log data in the Log Analytics workspace. In Microsoft Sentinel, the Logs page provides access to the query window. The query window allows you to run queries, save queries, run saved queries, create a new alert rule, and export. The left side provides a list of tables and related table fields. To run a query, enter the query text and press the run button. Query results appear in the bottom section of the form.

# Understand Microsoft Sentinel tables

Microsoft Sentinel has Analytic Rules that will generate Alerts and Incidents based on querying the tables within Log Analytics. The primary tables to manage alerts and incidents are SecurityAlert and SecurityIncident. Microsoft Sentinel provides tables to be a repository of indicators and watchlists.

 Note

Some of the Sentinel Data Connectors will ingest alerts directly.

The table below is the Microsoft Sentinel feature related tables.

| Table | Description  |
|---|---|
| SecurityAlert | Contains Alerts Generated from Sentinel Analytical Rules. Also, it could include Alerts created directly from a Sentinel Data Connector  |
| SecurityIncident | Alerts can generate Incidents. Incidents are related to Alert(s).  |
| ThreatIntelligenceIndicator | Contains user-created or data connector ingested Indicators such as File Hashes, IP Addresses, Domains  |
| Watchlist | A Microsoft Sentinel watchlist contains imported data. |

# Understand common tables

When Sentinel ingests data from the Data Connectors, the following table lists the most commonly used tables.

| Table | Description  |
|---|---|
| AzureActivity | Entries from the Azure Activity log that provides insight into any subscription-level or management group level events that have occurred in Azure.  |
| AzureDiagnostics | Stores resource logs for Azure services that use Azure Diagnostics mode. Resource logs describe the internal operation of Azure resources.  |
| AuditLogs | Audit log for Azure Active Directory. Includes system activity information about user and group management, managed applications, and directory activities.  |
| CommonSecurityLog | Syslog messages using the Common Event Format (CEF).  |
| McasShadowItReporting | Microsoft Cloud App Security logs  |
| OfficeActivity | Audit logs for Office 365 tenants collected by Microsoft Sentinel. Including Exchange, SharePoint and Teams logs.  |
| SecurityEvent | Security events collected from windows machines by Azure Security Center or Microsoft Sentinel  |
| SigninLogs | Azure Activity Directory Sign-in logs  |
| Syslog | Syslog events on Linux computers using the Log Analytics agent.  |
| Event | Sysmon Events collected from a Windows host.  |
| WindowsFirewall | Windows Firewall Events |

# Understand Microsoft 365 Defender tables

The Microsoft 365 Defender Sentinel Data Connector can populate tables with raw data collected from the Microsoft 365 Defender solutions.

| Table name | Description  |
|---|---|
| AlertEvidence | Files, IP addresses, URLs, users, or devices associated with alerts  |
| CloudAppEvents | Events involving accounts and objects in Office 365 and other cloud apps and services  |
| DeviceEvents | Multiple event types, including events triggered by security controls such as Windows Defender Antivirus and exploit protection  |
| DeviceFileCertificateInfo | Certificate information of signed files obtained from certificate verification events on endpoints  |
| DeviceFileEvents | File creation, modification, and other file system events  |
| DeviceImageLoadEvents | DLL loading events  |
| DeviceInfo | Machine information, including OS information  |
| DeviceLogonEvents | Sign-ins and other authentication events on devices  |
| DeviceNetworkEvents | Network connection and related events  |
| DeviceNetworkInfo | Network properties of devices, including physical adapters, IP and MAC addresses, as well as connected networks and domains  |
| DeviceProcessEvents | Process creation and related events  |
| DeviceRegistryEvents | Creation and modification of registry entries  |
| EmailEvents | Microsoft 365 email events, including email delivery and blocking events  |
| EmailPostDeliveryEvents | Security events that occur post-delivery, after Microsoft 365 has delivered the emails to the recipient mailbox  |
| EmailUrlInfo | Information about URLs on emails  |
| EmailAttachmentInfo | Information about files attached to Office 365 emails  |
| IdentityDirectoryEvents | Events involving an on-premises domain controller running Active Directory (AD). This table covers a range of identity-related events and system events on the domain controller.  |
| IdentityLogonEvents | Authentication events on Active Directory and Microsoft online services  |
| IdentityQueryEvents | Queries for Active Directory objects, such as users, groups, devices, and domains |

# Knowledge check

1. Which table stores Defender for Endpoint logon events?

[X] DeviceLogonEvents

Correct. The Defender for Endpoint data is stored in tables starting with Device

OfficeActivity

SigninLogs

2. What table contains logs from Windows hosts collected directly to Microsoft Sentinel?

[X] SecurityEvent

Correct. Logs from Windows events are stored in this table.

AuditLogs

SecurityAlert

3. Which table stores Alerts from Microsoft Defender for Endpoint?

SecurityIncident

DeviceEvents

Incorrect. This stores Defender for Endpoint data for information about various event types

[X] SecurityAlert

Correct. The Alerts will reside in the SecurityAlert table.

# Summary and resources

You should have a basic understanding of the provided tables and their intended purpose in Microsoft Sentinel.

You should now be able to:

-   Use the Logs page to view tables with Microsoft Sentinel
-   Query the most used tables with Microsoft Sentinel

## Learn more

You can learn more by reviewing the following.

[Become a Microsoft Sentinel Ninja](https://techcommunity.microsoft.com/t5/azure-sentinel/become-an-azure-sentinel-ninja-the-complete-level-400-training/ba-p/1246310)

[Microsoft Tech Community Security Webinars](https://techcommunity.microsoft.com/t5/microsoft-security-and/security-community-webinars/ba-p/927888)