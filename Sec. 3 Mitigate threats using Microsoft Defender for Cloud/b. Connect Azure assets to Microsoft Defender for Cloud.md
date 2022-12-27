https://learn.microsoft.com/en-us/training/modules/connect-azure-assets-to-azure-defender/

# Introduction

Resource protection in Microsoft Defender for Cloud can be automatically configured with autoprovisioning or may be manually deployed.

You're a Security Operations Analyst working at a company that is implementing cloud workload protection with Microsoft Defender for Cloud. Your job is to ensure Defender for Cloud automatically protects the Azure resources.

Your organization has a few Azure virtual machines that aren't part of the autoprovisioning scheme. You must manually configure protection for these Azure resources.

Learn how to connect your various Azure assets to Microsoft Defender for Cloud to detect threats.

# Explore and manage your resources with asset inventory

The asset inventory page of Microsoft Defender for Cloud provides a single page for viewing the security posture of the resources you've connected to Defender for Cloud.

Defender for Cloud periodically analyzes the security state of your Azure resources to identify potential security vulnerabilities. It then provides you with recommendations on how to remediate those vulnerabilities.

When any resource has outstanding recommendations, they'll appear in the inventory.

Use this view and its filters to address such questions as:

-   Which of my subscriptions with Microsoft Defender for Cloud enabled have outstanding recommendations?
    
-   Which of my machines with the tag 'Production' are missing the Log Analytics agent?
    
-   How many of my machines tagged with a specific tag have outstanding recommendations?
    
-   How many resources in a specific resource group have security findings from a vulnerability assessment service?
    

The asset management possibilities for this tool are substantial and continue to grow.

## Key features of asset inventory

The inventory page provides the following tools:

-   **Summaries** - Before you define any filters, a prominent strip of values at the top of the inventory view shows:
    
    -   Total resources: The total number of resources connected to Defender for Cloud.
        
    -   Unhealthy resources: Resources with active security recommendations. Learn more about security recommendations.
        
    -   Unmonitored resources: Resources with agent monitoring issues - they have the Log Analytics agent deployed, but the agent isn't sending data or has other health issues.
        
-   **Filters** - The multiple filters at the top of the page provide a way to quickly refine the list of resources according to the question you're trying to answer. For example, if you wanted to answer the question: Which of my machines with the tag 'Production' are missing the Log Analytics agent?
    
-   As soon as you've applied filters, the summary values are updated to relate to the query results.
    
-   Export options - Inventory provides the option to export the results of your selected filter options to a CSV file. You can also export the query itself to Azure Resource Graph Explorer to further refine, save, or modify the Kusto Query Language (KQL) query.
    
-   Asset management options - Inventory lets you perform complex discovery queries. When you've found the resources that match your queries, inventory provides shortcuts for operations such as:
    
    -   Assign tags to the filtered resources - select the checkboxes alongside the resources you want to tag.
        
    -   Onboard new servers to Defender for Cloud - use the Add non-Azure servers toolbar button.
        
    -   Automate workloads with Azure Logic Apps - use the Trigger Logic App button to run a logic app on one or more resources. Your logic apps have to be prepared in advance and accept the relevant trigger type (HTTP request).
        

## How does asset inventory work?

Asset inventory utilizes Azure Resource Graph (ARG), an Azure service that lets you query Defender for Cloud's security posture data across multiple subscriptions. ARG is designed to provide efficient resource exploration with the ability to query at scale. ARG uses the Kusto Query Language (KQL). Asset inventory can quickly produce deep insights by cross-referencing ASC data with other resource properties.

## How to use asset inventory

-   From Defender for Cloud's sidebar, select Inventory.
    
-   Use the Filter by name box to display a specific resource, or use the filters as described below.
    
-   Select the relevant options in the filters to create the specific query you want to perform.
    
-   To use the Security findings contain filter, enter free text from the ID, security check, or CVE name of a vulnerability finding to filter to the affected resources:
    

![Screenshot of Defender for Cloud Security Findings](https://learn.microsoft.com/en-us/training/wwl-sci/connect-azure-assets-to-azure-defender/media/security-findings-contain-elements.png)

-   To use the Defender for Cloud filter, select one or more options (Off, On, or Partial):
    
    -   Off - Resources that aren't protected by a Defender for Cloud plan. You can right-click on any of these resources and upgrade them:
        
    -   On - Resources that are protected by a Defender for Cloud plan
        
    -   Partial - This option applies to subscriptions that have some but not all of the Defender for Cloud plans disabled.

# Configure auto provisioning

Microsoft Defender for Cloud collects data from your Azure virtual machines (VMs), virtual machine scale sets, IaaS containers, and non-Azure (including on-premises) machines to monitor for security vulnerabilities and threats.

Data collection is required to provide visibility into missing updates, misconfigured OS security settings, endpoint protection status, and health and threat protection. Data collection is only needed for compute resources (VMs, virtual machine scale sets, IaaS containers, and non-Azure computers). You can benefit from Defender for Cloud even if you don’t provision agents. However, you'll have limited security, and the capabilities listed above aren't supported.

Data is collected using:

-   The Log Analytics agent, which reads various security-related configurations and event logs from the machine and copies the data to your workspace for analysis. Examples of such data are operating system type and version, operating system logs (Windows event logs), running processes, machine name, IP addresses, and logged in user.
    
-   Security extensions, such as the Azure Policy Add-on for Kubernetes, which can also provide data to Security Center regarding specialized resource types.
    

![Screenshot of Auto provisioning settings.](https://learn.microsoft.com/en-us/training/wwl-sci/connect-azure-assets-to-azure-defender/media/auto-provisioning-options.png)

## Why use auto provisioning?

Any of the agents and extensions described on this page can be installed manually. However, auto provisioning reduces management overhead by installing all required agents and extensions on existing - and new - machines to ensure faster security coverage for all supported resources.

## How does auto provisioning work?

Defender for Clouds's auto provisioning settings has a toggle for each type of supported extension. When you enable auto provisioning of an extension, you assign the appropriate Deploy if not exists policy to ensure that the extension is provisioned on all existing and future resources of that type.

## Enable auto provisioning of the Log Analytics agent

When automatic provisioning is on for the Log Analytics agent, Defender for Cloud deploys the agent on all supported Azure VMs and any new ones created.

To enable auto provisioning of the Log Analytics agent:

1.  From Defender for Clouds's menu, select **Environment settings**.
    
2.  Select the relevant subscription.
    
3.  In the **Auto provisioning** page, set the status of auto provisioning for the Log Analytics agent to **On**.
    
4.  From the configuration options pane, define the workspace to use.
    

Connect Azure VMs to the default workspace(s) created by Defender for Cloud - Defender for Cloud creates a new resource group and default workspace in the same geolocation and connects the agent to that workspace. If a subscription contains VMs from multiple geolocations, Defender for Cloud creates multiple workspaces to ensure compliance with data privacy requirements.

The naming convention for the workspace and resource group is:

-   Workspace: DefaultWorkspace-[subscription-ID]-[geo]
-   Resource Group: DefaultResourceGroup-[geo]

Defender for Cloud automatically enables Defender for Cloud solution(s) on the workspace per the pricing tier set for the subscription.

Connect Azure VMs to a different workspace - From the dropdown list, select the workspace to store collected data. The dropdown list includes all workspaces across all of your subscriptions. You can use this option to collect data from virtual machines running in different subscriptions and store it all in your selected workspace.

If you already have an existing Log Analytics workspace, you might want to use the same workspace (requires read and write permissions on the workspace). This option is useful if you're using a centralized workspace in your organization and want to use it for security data collection. Learn more in Manage access to log data and workspaces in Azure Monitor.

If your selected workspace already has a Security or Defender for Cloud Free solution enabled, the pricing will be set automatically. If not, install a Defender for Cloud solution on the workspace.

## Enable auto provisioning of extensions

To enable automatic provisioning of an extension other than the Log Analytics agent:

1.  From Defender for Clouds's menu in the Azure portal, select **Environment settings**.
    
2.  Select the relevant subscription.
    
3.  Select **Auto provisioning**.
    
4.  If you're enabling auto provisioning for the **Microsoft Dependency agent**, ensure the Log Analytics agent is set to auto deploy too.
    
5.  Toggle the status to On for the relevant extension.
    
6.  Select **Save**. The Azure policy is assigned, and a remediation task is created.
    

## Windows security event options for the Log Analytics agent

Selecting a data collection tier in Defender for Cloud only affects the storage of security events in your Log Analytics workspace. The Log Analytics agent will still collect and analyze the security events required for Defender for Clouds’s threat protection, regardless of the level of security events you choose to store in your workspace. Choosing to store security events enables investigation, search, and auditing of those events in your workspace.

Defender for Cloud is required for storing Windows security event data. Storing data in Log Analytics might incur more charges for data storage.

### Information for Microsoft Sentinel users

Users of Microsoft Sentinel: note that security events collection within the context of a single workspace can be configured from either Microsoft Defender for Cloud or Microsoft Sentinel, but not both. If you're planning to add Microsoft Sentinel to a workspace that is already getting alerts from Microsoft Defender for Cloud, and its set to collect Security Events, you have two options:

-   Leave the Security Events collection in Defender for Cloud as is. You'll be able to query and analyze these events in Microsoft Sentinel and Defender for Cloud. However, you won't be able to monitor the connector's connectivity status or change its configuration in Microsoft Sentinel. If monitoring or customizing the connector is important to you, consider the second option.
    
-   Disable Security Events collection in Defender for Cloud (by setting Windows security events to None in the configuration of your Log Analytics agent). Then add the Security Events connector in Microsoft Sentinel. As with the first option, you'll be able to query and analyze events in both Microsoft Sentinel and Defender for Cloud, but you'll now be able to monitor the connector's connectivity status or change its configuration in - and only in - Microsoft Sentinel.
    

### What event types are stored for "Common" and "Minimal"?

These sets were designed to address typical scenarios. Make sure to evaluate which one fits your needs before implementing it.

To determine the events for the Common and Minimal options, we worked with customers and industry standards to learn about the unfiltered frequency of each event and their usage. We used the following guidelines in this process:

-   Minimal - Make sure that this set covers only events that might indicate a successful breach and important events that have a low volume. For example, this set contains user successful and failed logins (event IDs 4624, 4625), but it doesn’t contain sign outs, which is important for auditing, but not meaningful for detection and has relatively high volume. Most of the data volume of this set is the login events and process creation event (event ID 4688).
    
-   Common - Provide a full user audit trail in this set. For example, this set contains both user logins and user sign-outs (event ID 4634). We include auditing actions like security group changes, key domain controller Kerberos operations, and other events that are recommended by industry organizations.
    

Events with low volume were included in the Common set as the main motivation to choose it over all the events is to reduce the volume and not filter out specific events.

# Manual log analytics agent provisioning

To manually install the Log Analytics agent:

1.  Disable auto provisioning.
    
2.  Optionally, create a workspace.
    
3.  Enable Microsoft Defender for Cloud on the workspace on which you're installing the Log Analytics agent:
    
4.  From Defender for Cloud's menu, select **Environmental settings**.
    
5.  Set the workspace on which you're installing the agent. Make sure the workspace is in the same subscription you use in Defender for Cloud, and you have read/write permissions for the workspace.
    
6.  Select **Microsoft Defender for Cloud on**, and **Save**.
    

-   To deploy agents on new VMs using a Resource Manager template, install the Log Analytics agent:
    
    -   [Install the Log Analytics agent for Windows](https://learn.microsoft.com/en-us/azure/virtual-machines/extensions/oms-windows)
        
    -   [Install the Log Analytics agent for Linux](https://learn.microsoft.com/en-us/azure/virtual-machines/extensions/oms-linux)
        
-   To deploy agents on your existing VMs, follow the instructions in [Collect data about Azure Virtual Machines](https://learn.microsoft.com/en-us/azure/azure-monitor/learn/quick-collect-azurevm).
    
-   To use PowerShell to deploy the agents, use the instructions from the virtual machines documentation:
    
    -   [For Windows machines](https://learn.microsoft.com/en-us/azure/virtual-machines/extensions/oms-windows?toc=%2Fazure%2Fazure-monitor%2Ftoc.json%3Fazure-portal%3Dtrue)
        
    -   [For Linux machines](https://learn.microsoft.com/en-us/azure/virtual-machines/extensions/oms-linux?toc=%2Fazure%2Fazure-monitor%2Ftoc.json%3Fazure-portal%3Dtrue)

# Knowledge check

1. Which is a Windows security events configuration?

Reasonable

Maximum

[X] Minimal

Correct. Minimal is a configuration option.

2. What should you install on a new Azure Windows VM if you aren't using auto provisioning?

[X] Log Analytics Agent

Correct. You need to install the Log Analytics Agent.

Sysmon

Windows Firewall

3. Which of these selections is an auto provisioning extension?

[X] Policy Add-on for Kubernetes

Correct. Policy Add-on for Kubernetes is an extension.

Windows Events

Policy for Azure Policy

# Summary and resources

You should have learned how resource protection in Microsoft Defender for Cloud can be automatically configured with auto provisioning or manually deployed.

You should now be able to:

-   Explore Azure assets
-   Configure auto provisioning in Microsoft Defender for Cloud
-   Describe manual provisioning in Microsoft Defender for Cloud

## Learn more

You can learn more by reviewing the following.

[Become an Microsoft Defender for Cloud Ninja (microsoft.com)](https://techcommunity.microsoft.com/t5/azure-security-center/become-an-azure-security-center-ninja/ba-p/1608761)

[Microsoft Tech Community Security Webinars](https://techcommunity.microsoft.com/t5/microsoft-security-and/security-community-webinars/ba-p/927888)