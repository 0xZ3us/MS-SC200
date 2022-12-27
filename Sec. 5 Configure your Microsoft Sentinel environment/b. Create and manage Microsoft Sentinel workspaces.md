https://learn.microsoft.com/en-us/training/modules/create-manage-azure-sentinel-workspaces/

# Introduction

Deploying the Microsoft Sentinel environment involves designing a workspace configuration to meet your security and compliance requirements. The provisioning process includes creating a Log Analytics workspace and configuring the Microsoft Sentinel options.

You're a Security Operations Analyst working at a company that is implementing Microsoft Sentinel. You're responsible for setting up the Microsoft Sentinel environment to meet the company requirement to minimize cost, meet compliance regulations, and provide the most manageable environment for your security team to perform their daily job responsibilities.

You start by understanding the Microsoft Sentinel workspace's architecture. After you've decided on your workspace implementation options, you create your first Microsoft Sentinel workspace.

After completing this module, you'll be able to:

-   Describe Microsoft Sentinel workspace architecture
-   Install Microsoft Sentinel workspace
-   Manage a Microsoft Sentinel workspace

# Plan for the Microsoft Sentinel workspace

Before deploying Microsoft Sentinel, it's crucial to understand the workspace options. The Microsoft Sentinel solution is installed in a Log Analytics Workspace, and most implementation considerations are focused on the Log Analytics Workspace creation. The single most important option when creating a new Log Analytics Workspace is the region. The region specifies the location where the log data will reside.

The three implementation options:

-   Single-Tenant with a single Microsoft Sentinel Workspace
    
-   Single-Tenant with regional Microsoft Sentinel Workspaces
    
-   Multi-Tenant
    

## Single-tenant single workspace

The single-tenant with a single Microsoft Sentinel workspace will be the central repository for logs across all resources within the same tenant.

This workspace receives logs from resources in other regions within the same tenant. Because the log data (when collected) will travel across regions and stored in another region, this creates two possible concerns. First, it can incur a bandwidth cost. Second, if there's a data governance requirement to keep data in a specific region, the single workspace option wouldn't be an implementation option.

![Diagram of a Single Tenant Sentinel Workspace.](https://learn.microsoft.com/en-us/training/wwl-sci/create-manage-azure-sentinel-workspaces/media/single-tenant-workspace.png)

Single-Tenants with a single workspace trade-off include:

| Pros | Cons  |
|---|---|
| Central Pane of Glass | May not meet Data Governance Requirements  |
| Consolidates all security logs and information | Can incur bandwidth cost for cross region  |
| Easier to query all information |   |
| Azure Log Analytics RBAC to control data access |   |
| Microsoft Sentinel RBAC for service RBAC |  |

## Single-tenant with regional Microsoft Sentinel workspaces

The single-tenant with regional Microsoft Sentinel workspaces will have multiple Sentinel workspaces requiring the creation and configuration of multiple Microsoft Sentinel and Log Analytics workspaces.

![Diagram of a Sentinel Single Tenant Regional Workspace.](https://learn.microsoft.com/en-us/training/wwl-sci/create-manage-azure-sentinel-workspaces/media/single-tenant-regional-workspace.png)

| Pros | Cons  |
|---|---|
| No cross-region bandwidth costs | No central pane of glass. You aren't looking in one place to see all the data.  |
| May be required to meet Data Governance requirements | Analytics, Workbooks, etc. must be deployed multiple times.  |
| Granular data access control |   |
| Granular retention settings |   |
| Split billing |  |

To query data across workspaces, use the workspace() function before the table name.

```Kusto
TableName

| union workspace("WorkspaceName").TableName

```

## Multi-tenant workspaces

If you're required to manage a Microsoft Sentinel workspace, not in your tenant, you implement Multi-Tenant workspaces using Azure Lighthouse. This security configuration grants you access to the tenants. The tenant configuration within the tenant (regional or multi-regional) is the same consideration as before.

![Diagram of Sentinel Multi-Tenant Workspaces.](https://learn.microsoft.com/en-us/training/wwl-sci/create-manage-azure-sentinel-workspaces/media/multi-tenant-workspaces.png)

## Use the same log analytics workspace as Microsoft Defender for Cloud

Use the same workspace for both Microsoft Sentinel and Microsoft Defender for Cloud, so that all logs collected by Microsoft Defender for Cloud can also be ingested and used by Microsoft Sentinel. The default workspace created by Microsoft Defender for Cloud won't appear as an available workspace for Microsoft Sentinel.

# Create a Microsoft Sentinel workspace

After designing the workspace architecture, log in to the Azure portal. At the search bar, search for Sentinel, then select **Microsoft Sentinel**. The Microsoft Sentinel Workspaces shows a list of the current workspaces. Select the **+ add** button to start the creation process.

## Microsoft Sentinel installation prerequisites

To enable Microsoft Sentinel, you need contributor permissions to the subscription in which the Microsoft Sentinel workspace resides. To use Microsoft Sentinel, you need either contributor or reader permissions on the resource group that the workspace belongs.

## Create and configure a Log Analytics Workspace

1.  The next page, **Add Microsoft Sentinel to a workspace** will display a list of available Log Analytics workspaces to add Microsoft Sentinel. Select the **+ create a new workspace** button to start the "Create Log Analytics workspace" process.
    
2.  The Basics tab includes the following options:

| Option | Description  |
|---|---|
| Subscription | Select the Subscription  |
| Resource Group | Select or create a Resource Group  |
| Name | Name is the name of the Log Analytics workspace and will also be the name of your Microsoft Sentinel Workspace  |
| Region | The region is the location the log data will be stored. |

3.   Important
    
    The Name will be the name of the Microsoft Sentinel workspace. The Microsoft Sentinel name will default to the Log Analytics Workspace Name. The Region is the location where ingested data is stored. The data location impacts data governance requirements. Workspaces can't move from region to region; you will need to recreate the workspace if the region option needs to be changed.
    
4.  Select the **Review + Create** button and then select the **Create** button.
    

## Add Microsoft Sentinel to the workspace

The "Add Microsoft Sentinel to Workspace" screen will now appear after you've completed the previous steps.

1.  Wait for the newly created "Log Analytics Workspace" to appear in the list. This operation could take a few minutes.
    
2.  Select the newly created Log Analytics workspace. And select the **Add** button.
    

The new Microsoft Sentinel workspace will now be the active screen. The Microsoft Sentinel left navigation has four areas:

-   General
-   Threat management
-   Content management
-   Configuration

The Overview tab displays a standard dashboard of information about the ingested data, alerts, and incidents.

## Microsoft Sentinel sharing a Log Analytics Workspace

Considering that Microsoft Sentinel workspace uses a Log Analytics workspace, you have the option to enable the Sentinel workspace in a Log Analytics workspace that is used by other solutions. The most common scenario is sharing the Log Analytics workspace used by Microsoft Defender for Cloud. Sharing the workspace enables one central workspace to query security data.

## Microsoft Defender for Cloud

When creating your Microsoft Sentinel workspace, you aren't allowed to use the **Default** Microsoft Defender for Cloud Log Analytics workspace. You need to manually create a Log Analytics workspace then update the Microsoft Defender for Cloud tier. Now you can select the manually created Log Analytics workspace for use with Microsoft Defender for Cloud.

# Manage workspaces across tenants using Azure Lighthouse

If you're required to manage a Microsoft Sentinel workspace not in your tenant, implementing Azure Lighthouse will provide the option to enable your access to the tenant. Once Azure Lighthouse is onboarded, use the directory + subscription selector on the Azure portal to select all the subscriptions containing workspaces you manage.

![Diagram of multiple tenants managed by Azure Lighthouse.](https://learn.microsoft.com/en-us/training/wwl-sci/create-manage-azure-sentinel-workspaces/media/azure-delegated-tenant.jpg)

Azure Lighthouse allows greater flexibility to manage resources for multiple customers without having to sign in to different accounts in different tenants. For example, a service provider may have two customers with different responsibilities and access levels. By using Azure Lighthouse, authorized users can sign in to the service provider's tenant to access these resources.

# Understand Microsoft Sentinel permissions and roles

Microsoft Sentinel uses Azure role-based access control (Azure RBAC) to provide built-in roles that can be assigned to users, groups, and services in Azure.

Use Azure RBAC to create and assign roles within your security operations team to grant appropriate access to Microsoft Sentinel. The different roles give you fine-grained control over what users of Microsoft Sentinel can see and do. Azure roles can be assigned in the Microsoft Sentinel workspace directly, or in a subscription or resource group that the workspace belongs to, which Microsoft Sentinel will inherit.

## Microsoft Sentinel-specific roles

All Microsoft Sentinel built-in roles grant read access to the data in your Microsoft Sentinel workspace:

-   **Microsoft Sentinel Reader**: can view data, incidents, workbooks, and other Microsoft Sentinel resources.
    
-   **Microsoft Sentinel Responder**: can, in addition to the above, manage incidents (assign, dismiss, etc.)
    
-   **Microsoft Sentinel Contributor**: can, in addition to the above, create and edit workbooks, analytics rules, and other Microsoft Sentinel resources.
    
-   **Microsoft Sentinel Automation Contributor**: allows Microsoft Sentinel to add playbooks to automation rules. It isn't meant for user accounts.
    

For best results, these roles should be assigned to the resource group that contains the Microsoft Sentinel workspace. The roles then apply to all the resources that deploy to support Microsoft Sentinel, if those resources are in the same resource group.

## Additional roles and permissions

Users with particular job requirements may need to be assigned other roles or specific permissions in order to accomplish their tasks.

-   Working with playbooks to automate responses to threats
    
    Microsoft Sentinel uses playbooks for automated threat response. Playbooks are built on Azure Logic Apps, and are a separate Azure resource. You might want to assign to specific members of your security operations team the ability to use Logic Apps for Security Orchestration, Automation, and Response (SOAR) operations. You can use the Logic App Contributor role to assign explicit permission for using playbooks.
    
-   Giving Microsoft Sentinel permissions to run playbooks
    
    Microsoft Sentinel uses a special service account to run incident-trigger playbooks manually or to call them from automation rules. The use of this account (as opposed to your user account) increases the security level of the service.
    
    In order for an automation rule to run a playbook, this account must be granted explicit permissions to the resource group where the playbook resides. At that point, any automation rule will be able to run any playbook in that resource group. To grant these permissions to this service account, your account must have Owner permissions on the resource groups containing the playbooks.
    
-   Connecting data sources to Microsoft Sentinel
    
    For a user to add data connectors, you must assign the user write permissions on the Microsoft Sentinel workspace. Also, note the required other permissions for each connector, as listed on the relevant connector page.
    
-   Guest users assigning incidents
    
    If a guest user needs to be able to assign incidents, then in addition to the Microsoft Sentinel Responder role, the user will also need to be assigned the role of Directory Reader. This role isn't an Azure role but an Azure Active Directory role, and that regular (non-guest) users have this role assigned by default.
    
-   Creating and deleting workbooks
    
    To create and delete a Microsoft Sentinel workbook, the user requires either the Microsoft Sentinel Contributor role or a lesser Microsoft Sentinel role plus the Azure Monitor role of Workbook Contributor. This role isn't necessary for using workbooks, but only for creating and deleting.
    

## Azure roles and Azure Monitor Log Analytics roles

In addition to Microsoft Sentinel-dedicated Azure RBAC roles, other Azure and Log Analytics Azure RBAC roles can grant a wider set of permissions. These roles include access to your Microsoft Sentinel workspace and other resources.

-   Azure roles grant access across all your Azure resources. They include Log Analytics workspaces and Microsoft Sentinel resources:
    
    -   Owner
        
    -   Contributor
        
    -   Reader
        
-   Log Analytics roles grant access across all your Log Analytics workspaces:
    
    -   Log Analytics Contributor
        
    -   Log Analytics Reader
        

For example, a user who is assigned with the Microsoft Sentinel Reader and Azure Contributor (not Microsoft Sentinel Contributor) roles can edit data in Microsoft Sentinel. If you want to only grant permissions to Microsoft Sentinel, you should carefully remove the user's prior permissions. Make sure you don't break any needed permission role for another resource.

## Microsoft Sentinel roles and allowed actions

The following table summarizes the roles and allowed actions in Microsoft Sentinel.

| Roles | Create and run playbooks | Create and edit workbooks, analytic rules, and other Microsoft Sentinel resources | Manage incidents such as dismissing and assigning | View data incidents, workbooks, and other Microsoft Sentinel resources  |
|---|---|---|---|---|
| Microsoft Sentinel Reader | No | No | No | Yes  |
| Microsoft Sentinel Responder | No | No | Yes | Yes  |
| Microsoft Sentinel Contributor | No | Yes | Yes | Yes  |
| Microsoft Sentinel Contributor and Logic App Contributor | Yes | Yes | Yes | Yes |

## Custom roles and advanced Azure RBAC

If the built-in Azure roles don't meet the specific needs of your organization, you can create your own custom roles. Just like built-in roles, you can assign custom roles to users, groups, and service principals for management-group, subscription, and resource-group scopes.

# Manage Microsoft Sentinel settings

Microsoft Sentinel Environment Settings are managed in two areas. In Microsoft Sentinel and in the Log Analytics workspace where Microsoft Sentinel resides. In Microsoft Sentinel, the left navigation has an option for Settings. The Settings includes tabs for Pricing, Settings, and Workspace Settings—the Settings changes over time based on the current and in-preview feature set. Most Microsoft Sentinel Environment settings are managed in the Log Analytics workspace. Other areas within the Microsoft Sentinel portal will transfer you to the Log Analytics portal. An example would be specific data connector configurations that are performed in the log analytics workspace.

## Configure log retention

Data retention at the workspace level can be configured from 30 to 730 days (two years) for all workspaces unless they're using the legacy Free pricing tier. To adjust the retention days, select the workspace settings in the Microsoft Sentinel Settings area. The next screen is in the Log Analytics portal. Select the "Usage and estimated costs" tab. At the top of the page, select the "Retention" button. A window will open, allowing for the adjustment of the retention days.

![Screenshot of setting the data retention.](https://learn.microsoft.com/en-us/training/wwl-sci/create-manage-azure-sentinel-workspaces/media/retention.png)

# Configure logs

There are three primary log types in Microsoft Sentinel:

-   Analytics Logs
-   Basic Logs
-   Archive Logs

Data in each table in a Log Analytics workspace is retained for a specified period of time after which it's either removed or archived with a reduced retention fee. Set the retention time to balance your requirement for having data available with reducing your cost for data retention.

To access archived data, you must first retrieve data from it in an Analytics Logs table using one of the following methods:

-   Search Jobs
-   Restore

![Diagram of different Workspace Log Types.](https://learn.microsoft.com/en-us/training/wwl-sci/create-manage-azure-sentinel-workspaces/media/workspace-plan-overview.png)

## Analytical Logs

By default, all tables in a workspace are of type Analytics Logs, which are available to all features of a Log Analytics workspace and any other services that use the workspace.

## Basic Logs

You can configure certain tables as **Basic Logs** to reduce the cost of storing high-volume verbose logs you use for debugging, troubleshooting and auditing, but not for analytics and alerts. Tables configured for Basic Logs have a lower ingestion cost in exchange for reduced features. Basic logs are only **retained for 8 days**.

### KQL language limits

Queries against Basic Logs are optimized for simple data retrieval using a subset of KQL language, including the following operators:

-   where
-   extend
-   project
-   project-away
-   project-keep
-   project-rename
-   project-reorder
-   parse
-   parse-where

The following KQL isn't supported:

-   join
-   union
-   aggregates (summarize)

### Table support Basic Logs

All tables in your Log Analytics are Analytics tables, by default. You can configure particular tables to use Basic Logs. You can't configure a table for Basic Logs if Azure Monitor relies on that table for specific features.

You can currently configure the following tables for Basic Logs:

-   All tables created with the Data Collection Rule (DCR)-based custom logs API.
-   ContainerLogV2, which Container Insights uses and which include verbose text-based log records.
-   AppTraces, which contain freeform log records for application traces in Application Insights.

 Note

Basic Logs are currently in _Preview_. The supported/eligible tables documentation will be updated with current information when the feature is _Generally Available_.

### Configure log type

To adjust the log type for an **eligible** table, select the workspace settings in the Microsoft Sentinel Settings area.  
The next screen is in the Log Analytics portal.

1.  Select the "Tables" tab.
2.  Select the table then **...** at the end of the row.
3.  Select Manage table
4.  Change the _Table plan_.
5.  Select **Save**

## Archive Logs

Archiving lets you keep older, less used data in your workspace at a reduced cost. Each workspace has a default retention policy that's applied to all tables. You can set a different retention policy on individual tables.

![Diagram of the Retention archive process.](https://learn.microsoft.com/en-us/training/wwl-sci/create-manage-azure-sentinel-workspaces/media/retention-archive.png)

During the interactive retention period, data is available for monitoring, troubleshooting and analytics. When you no longer use the logs, but still need to keep the data for compliance or occasional investigation, archive the logs to save costs. You can access archived data by running a search job or restoring archived logs.

### Configure table retention

To adjust the retention days for a table, select the workspace settings in the Microsoft Sentinel Settings area.  
The next screen is in the Log Analytics portal.

1.  Select the "Tables" tab.
2.  Select the table then **...** at the end of the row.
3.  Select Manage table
4.  Change the _Total retention period_.
5.  Select **Save**

# Knowledge check

1. Where is your log data stored?

Microsoft Sentinel Workspace

Azure Lighthouse

[X] Log Analytics workspace

Correct. Log Analytics workspace is where the data resides

2. Which Microsoft Sentinel security role can create workbooks?

Microsoft Sentinel Responder

Microsoft Sentinel Reader

[X] Microsoft Sentinel Contributor

Correct. The Contributor role can create workbooks.

3. Why is it important to set the region when creating the Log Analytics workspace?

[X] Specifies where the log data will be stored.

Correct. Region is the data center where your log data is stored

Specifies the timezone the data will be displayed in.

Specifies the log retention period

# Summary and resources

You should have learned how the Microsoft Sentinel provisioning process includes creating a Log Analytics workspace and configuring the Microsoft Sentinel options.

You should now be able to:

-   Describe Microsoft Sentinel workspace architecture
-   Provision a Microsoft Sentinel workspace
-   Manage a Microsoft Sentinel workspace

## Learn more

You can learn more by reviewing the following.

[Become a Microsoft Sentinel Ninja](https://techcommunity.microsoft.com/t5/azure-sentinel/become-an-azure-sentinel-ninja-the-complete-level-400-training/ba-p/1246310)

[Microsoft Tech Community Security Webinars](https://techcommunity.microsoft.com/t5/microsoft-security-and/security-community-webinars/ba-p/927888)