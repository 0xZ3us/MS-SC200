https://learn.microsoft.com/en-us/training/modules/intro-to-azure-sentinel/

# Introduction

Imagine that you work as a security operations center (SOC) analyst. Your organization wants to advance its security-management capabilities. The business has already started moving some workloads to the public cloud.

You've been asked to evaluate _security information and event management_ (SIEM) solutions that can help in both an on-premises and a multiple-cloud environment. You've heard about Microsoft Sentinel and want to find out whether it could be the right SIEM solution for your business.

Ideally, you'd select a service that provides the features and functionality that you need, with minimal administration and a flexible pricing model.

Microsoft Sentinel offers exactly those benefits.

In this module, you'll explore Microsoft Sentinel and discover why and when to use it. You'll investigate the key features and capabilities of Microsoft Sentinel, including how and when to deploy it.

## Learning objectives

By the end of this module, you'll be able to:

-   Identify the various components and functionality of Microsoft Sentinel.
-   Identify use cases where Microsoft Sentinel would be a good solution.

# What is Microsoft Sentinel? 

Let's start with a few definitions and a look at _security information and event management_ (SIEM) systems and Microsoft Sentinel.

## What is security information and event management (SIEM)?

A SIEM system is a tool that an organization uses to collect, analyze, and perform security operations on its computer systems. Those systems can be hardware appliances, applications, or both.

In its simplest form, a SIEM system enables you to:

-   Collect and query logs.
-   Do some form of correlation or anomaly detection.
-   Create alerts and incidents based on your findings.

A SIEM system might offer functionality such as:

-   **Log management**: The ability to collect, store, and query the log data from resources within your environment.
    
-   **Alerting**: A proactive look inside the log data for potential security incidents and anomalies.
    
-   **Visualization**: Graphs and dashboards that provide visual insights into your log data.
    
-   **Incident management**: The ability to create, update, assign, and investigate incidents that have been identified.
    
-   **Querying data**: A rich query language, similar to that for log management, that you can use to query and understand your data.
    

## What is Microsoft Sentinel?

Microsoft Sentinel is a cloud-native SIEM system that a security operations team can use to:

-   Get security insights across the enterprise by collecting data from virtually any source.
-   Detect and investigate threats quickly by using built-in machine learning and Microsoft threat intelligence.
-   Automate threat responses by using playbooks and by integrating Azure Logic Apps.

Unlike with traditional SIEM solutions, to run Microsoft Sentinel, you don't need to install any servers either on-premises or in the cloud. Microsoft Sentinel is a service that you deploy in Azure. You can get up and running with Sentinel in just a few minutes in the Azure portal.

Microsoft Sentinel is tightly integrated with other cloud services. Not only can you quickly ingest logs, but you can also use other cloud services natively (for example, authorization and automation).

Microsoft Sentinel helps you enable end-to-end security operations including collection, detection, investigation, and response:

![This diagram shows the end-to-end functionality of Microsoft Sentinel.](https://learn.microsoft.com/en-us/training/modules/intro-to-azure-sentinel/media/02-end-to-end.svg)

Let's take a look at the key components in Microsoft Sentinel.

# How Microsoft Sentinel works

As you've already learned, Microsoft Sentinel helps you enable end-to-end security operations. It starts with log ingestion and continues through to automated response to security alerts.

Here are the key features and components of Microsoft Sentinel.

## Data connectors

The first thing to do is to have your data ingested into Microsoft Sentinel. Data connectors enable you to do just that. You can add some services, such as Azure activity logs, just by selecting a button. Others, such as syslog, require a little configuration. There are data connectors that cover all scenarios and sources, including but not limited to:

-   syslog
-   Common Event Format (CEF)
-   Trusted Automated eXchange of Indicator Information (TAXII) (for threat intelligence)
-   Azure
-   AWS services

[![This screenshot shows a partial list of data connectors in the Microsoft Sentinel UI in the Azure portal.](https://learn.microsoft.com/en-us/training/modules/intro-to-azure-sentinel/media/03-data-connectors.png)](https://learn.microsoft.com/en-us/training/modules/intro-to-azure-sentinel/media/03-data-connectors.png#lightbox)

## Log retention

After it's been ingested into Microsoft Sentinel, your data is stored by using Log Analytics. The benefits of using Log Analytics include the ability to use the Kusto Query Language (KQL) to query your data. KQL is a rich query language that gives you the power to dive into and gain insights from our data.

[![This screenshot shows the Log Analytics interface in the Azure portal.](https://learn.microsoft.com/en-us/training/modules/intro-to-azure-sentinel/media/03-log-analytics.png)](https://learn.microsoft.com/en-us/training/modules/intro-to-azure-sentinel/media/03-log-analytics.png#lightbox)

## Workbooks

You use workbooks to visualize your data within Microsoft Sentinel. Think of workbooks as dashboards. Each component in the dashboard is built by using an underlying KQL query of your data. You can use the built-in workbooks within Microsoft Sentinel, edit them to meet your own needs, or create your own workbooks from scratch. If you've used Azure Monitor workbooks, this feature will be familiar to you because it's Sentinel's implementation of Monitor workbooks.

[![This screenshot shows an example of a workbook in Microsoft Sentinel.](https://learn.microsoft.com/en-us/training/modules/intro-to-azure-sentinel/media/03-workbooks.png)](https://learn.microsoft.com/en-us/training/modules/intro-to-azure-sentinel/media/03-workbooks.png#lightbox)

## Analytics alerts

So far, you have your logs and some data visualization. Now it would be great to have some proactive analytics across your data, so you're notified when something suspicious occurs. You can enable built-in analytics alerts within your Sentinel workspace. There are various types of alerts, some of which you can edit to your own needs. Other alerts are built on machine-learning models that are proprietary to Microsoft. You can also create custom, scheduled alerts from scratch.

[![This screenshot shows some of the built-in analytics alerts available in a Microsoft Sentinel workbook.](https://learn.microsoft.com/en-us/training/modules/intro-to-azure-sentinel/media/03-analytics-alerts.png)](https://learn.microsoft.com/en-us/training/modules/intro-to-azure-sentinel/media/03-analytics-alerts.png#lightbox)

## Threat hunting

We won't dive deeply into threat hunting in this module. However, if SOC analysts need to hunt for suspicious activity, there are some built-in hunting queries that they can use. Analysts can also create their own queries. Sentinel also integrates with Azure Notebooks. It provides example notebooks for advanced hunters who want to use the full power of a programming language to hunt through their data.

[![This screenshot shows the threat-hunting interface in Microsoft Sentinel.](https://learn.microsoft.com/en-us/training/modules/intro-to-azure-sentinel/media/03-hunting.png)](https://learn.microsoft.com/en-us/training/modules/intro-to-azure-sentinel/media/03-hunting.png#lightbox)

## Incidents and investigations

An incident is created when an alert that you've enabled is triggered. In Microsoft Sentinel, you can do standard incident management tasks like changing status or assigning incidents to individuals for investigation. Microsoft Sentinel also has investigation functionality, so you can visually investigate incidents by mapping entities across log data along a timeline.

[![This screenshot shows an incident-investigation graph within Microsoft Sentinel.](https://learn.microsoft.com/en-us/training/modules/intro-to-azure-sentinel/media/03-investigate-incidents.png)](https://learn.microsoft.com/en-us/training/modules/intro-to-azure-sentinel/media/03-investigate-incidents.png#lightbox)

## Automation playbooks

With the ability to respond to incidents automatically, you can automate some of your security operations and make your SOC more productive. Microsoft Sentinel integrates with Azure Logic Apps, enabling you to create automated workflows, or _playbooks_, in response to events. This functionality could be used for incident management, enrichment, investigation, or remediation. These capabilities are often referred to as _security orchestration, automation, and response (SOAR)_.

[![This screenshot shows an example use of Azure Logic Apps to remediate a security incident.](https://learn.microsoft.com/en-us/training/modules/intro-to-azure-sentinel/media/03-logic-apps.png)](https://learn.microsoft.com/en-us/training/modules/intro-to-azure-sentinel/media/03-logic-apps.png#lightbox)

As the SOC Analyst, you now start to see how Microsoft Sentinel might help you achieve your goals. For example, you could:

-   Ingest data from your cloud and on-premises environments.
-   Perform analytics on that data.
-   Manage and investigate any incidents that occur.
-   Perhaps even respond automatically by using playbooks.

In other words, Microsoft Sentinel gives you an end-to-end solution for your security operations.

# When to use Microsoft Sentinel

Microsoft Sentinel is a solution for performing security operations on your cloud and on-premises environments.

Use Microsoft Sentinel if you want to:

-   Collect event data from various sources.
-   Perform security operations on that data to identify suspicious activity.

Security operations could include:

-   Visualization of log data.
-   Anomaly detection.
-   Threat hunting.
-   Security incident investigation
-   Automated response to alerts and incidents.

Microsoft Sentinel offers other capabilities that could help you decide whether it's the right fit for you:

-   Cloud-native SIEM. There are no servers to provision, so scaling is effortless.
-   Integration with the Azure Logic Apps service and its hundreds of connectors.
-   Benefits of Microsoft research and machine learning.
-   Key log sources provided for free.
-   Support for hybrid cloud and on-premises environments.
-   SIEM and a data lake all in one.

When you began investigating Microsoft Sentinel, your organization had some clear requirements:

-   Support for data from multiple cloud environments
-   Features and functionality required for a security operations center (SOC), without too much administrative overhead

You've found that Microsoft Sentinel could be a good fit. It offers data connectors for syslog, Amazon Web Services (AWS), and other sources, and the ability to scale effortlessly without provisioning servers. During your analysis, you also realized that your organization should make automation a key part of its SOC strategy. Automation wasn't something the organization had considered before, but now you'll look into using automation playbooks.

If you're collecting infrastructure or application logs for performance monitoring, consider also using Azure Monitor and Log Analytics for that purpose.

And perhaps you want to understand the security posture of your environment, make sure that you're compliant with policy, and check for security misconfigurations. If so, consider also using Microsoft Defender for Cloud. You can ingest Defender for Cloud alerts as a data connector for Microsoft Sentinel.

# Knowledge check

1. What does Microsoft Sentinel provide?

A solution for checking your security posture in the cloud

[X] An end-to-end solution for security operations

Yes, Microsoft Sentinel gives you an end-to-end solution for security operations. The solution includes visibility, analytics, hunting, incident management, and automation.

A solution for securely storing keys and secrets in the cloud

2. Which language is used to query data within Microsoft Sentinel?

SQL

GraphQL

[X] KQL

Kusto Query Language (KQL) is a language used for querying data in Log Analytics, which is where Microsoft Sentinel holds its data.

3. Which Azure service stores the log data that is ingested into Microsoft Sentinel?

Azure Data Factory

[X] Log Analytics

Log Analytics is the underlying service that stores the log data for Microsoft Sentinel.

Azure Monitor

4. Within Microsoft Sentinel, which Azure product is used to run automated playbooks in response to alerts?

Log Analytics

Azure Monitor

[X] Azure Logic Apps

Azure Logic Apps is a serverless, no-code solution for automating workflows. It integrates with hundreds of other services, making it a powerful solution for security orchestration, automation, and response (SOAR).

# Summary

You've learned how Microsoft Sentinel can meet the requirements of the SOC analyst's organization:

-   Support for data connectors for cloud and hybrid services.
-   Features and functionality that you need, with minimal administration.

You explored what a SIEM solution is, and what Microsoft Sentinel and its key components have to offer. You also learned when to use Microsoft Sentinel and when other Azure products might complement Microsoft Sentinel to improve the security of your environment.

You now understand how Microsoft Sentinel helps you to perform end-to-end security operations.

## Learn more

Learn more about Microsoft Sentinel from the following articles:

-   [Microsoft Sentinel documentation](https://learn.microsoft.com/en-us/azure/sentinel)
-   [Quickstart: On-board Microsoft Sentinel](https://learn.microsoft.com/en-us/azure/sentinel/quickstart-onboard)
-   [Microsoft Sentinel pricing](https://azure.microsoft.com/pricing/details/azure-sentinel)
-   [Permissions in Microsoft Sentinel](https://learn.microsoft.com/en-us/azure/sentinel/roles)
-   [Tutorial: Visualize and monitor your data](https://learn.microsoft.com/en-us/azure/sentinel/tutorial-monitor-your-data)
-   [Quickstart: Get started with Microsoft Sentinel](https://learn.microsoft.com/en-us/azure/sentinel/quickstart-get-visibility)
-   [Extend Microsoft Sentinel across workspaces and tenants](https://learn.microsoft.com/en-us/azure/sentinel/extend-sentinel-across-workspaces-tenants#cross-workspace-monitoring?azure-portal=true)