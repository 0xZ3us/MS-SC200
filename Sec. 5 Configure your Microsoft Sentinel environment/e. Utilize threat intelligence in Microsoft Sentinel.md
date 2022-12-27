https://learn.microsoft.com/en-us/training/modules/utilize-threat-intelligence-azure-sentinel/

# Introductions

Microsoft Sentinel provides a table to store indicator data accessible to Kusto Query Language (KQL) queries. The Threat intelligence page in Microsoft Sentinel provides the management options to maintain the indicators.

You're a Security Operations Analyst working at a company that implemented Microsoft Sentinel. You receive threat indicators from threat intelligence providers and your threat hunting team. The Indicators include IP addresses, domains, and file hashes that can be utilized by many components within Microsoft Sentinel.

The indicators from the threat intelligence providers are automatically imported into the workspace using connectors. You're tasked with adding the indicators from the threat hunting team. You use the Threat Intelligence page to add the indicators for use by the detection KQL queries.

After completing this module, you'll be able to:

-   Manage threat indicators in Microsoft Sentinel
-   Use KQL to access threat indicators in Microsoft Sentinel

# Define threat intelligence

Cyber threat intelligence (CTI) can come from many sources. Sources include open-source data feeds, threat intelligence-sharing communities, paid intelligence feeds, and security investigations within organizations. CTI can range from written reports on a threat actor's motivations, infrastructure, and techniques, to specific observations of IP addresses, domains, and file hashes. CTI provides essential context for unusual activity, so security personnel can act quickly to protect people and assets.

The most utilized CTI in SIEM solutions like Microsoft Sentinel is threat indicator data, sometimes called Indicators of Compromise (IoCs). Threat indicators associate URLs, file hashes, IP addresses, and other data with known threat activity like phishing, botnets, or malware. This form of threat intelligence is often called tactical threat intelligence, because security products and automation can use it in large scale to protect and detect potential threats. Microsoft Sentinel can help detect, respond to, and provide CTI context for malicious cyber activity.

You can integrate threat intelligence (TI) into Microsoft Sentinel through the following activities:

-   Use Data connectors to various TI platforms to import threat intelligence into Microsoft Sentinel.
    
-   View and manage the imported threat intelligence in Logs and the new Threat Intelligence area of Microsoft Sentinel.
    
-   Use the built-in Analytics rule templates to generate security alerts and incidents using your imported threat intelligence.
    
-   Visualize critical information about your threat intelligence in Microsoft Sentinel with the Threat Intelligence workbook.
    
-   Perform threat hunting with your imported threat intelligence.
    

![Screenshot of Threat Intelligence uses in Microsoft Sentinel.](https://learn.microsoft.com/en-us/training/wwl-sci/utilize-threat-intelligence-azure-sentinel/media/sentinel-data-flow.png)

# Manage your threat indicators

With the Threat Intelligence area, accessible from the Microsoft Sentinel menu, you can also view, sort, filter, and search your imported threat indicators without even writing a Logs query. This area also allows you to create threat indicators directly within the Microsoft Sentinel interface and perform everyday threat intelligence administrative tasks. These tasks include indicator tagging and creating new indicators related to security investigations. Let's look at two of the most common tasks, creating new threat indicators and tagging indicators for easy grouping and reference.

1.  Open the [Azure portal](https://portal.azure.com/) and navigate to the Microsoft Sentinel service.
    
2.  Choose the workspace to which you've imported threat indicators using either threat intelligence data connector.
    
3.  Select **Threat intelligence** from the **Threat management** section of the Microsoft Sentinel menu.
    
4.  Select the **Add new** button from the top menu of the page.
    
5.  Choose the indicator type, then complete the required fields marked with a red asterisk (*) on the New indicator panel. Select **Apply**.
    

Tagging threat indicators is an easy way to group them to make them easier to find. Typically, you might apply a tag to indicators related to a particular incident or indicators representing threats from a known actor or a well-known attack campaign. You can tag threat indicators individually or multi-select indicators and tag them all at once. Since tagging is free-form, a recommended practice is to create standard naming conventions for threat indicator tags. You can apply multiple tags to each indicator.

# View your threat indicators with KQL

The indicators reside in the _ThreatIntelligenceIndicator_ table. This table is the basis for queries performed by other Microsoft Sentinel features such as Analytics and Workbooks. Here's how to find and view your threat indicators in the ThreatIntelligenceIndicator table.

To view your threat indicators with KQL. Select **Logs** from the General section of the Microsoft Sentinel menu. Then run a query on the ThreatIntelligenceIndicator table.

```Kusto
ThreatIntelligenceIndicator
```

# Knowledge check

1. In Threat Intelligence, indicators are considered as which of the following?

Strategic

Operational

[X] Tactical

Correct. Indicators are considered Tactical Threat Intelligence.

2. Which of these items is an example of a Threat indicator?

Threat Actor Name

[X] Domain Name

Correct. This indicator can be used to query against your log data.

Threat Campaign

3. What table do you query in KQL to view your indicators?

Indicator

TI Indicator

[X] ThreatIntelligenceIndicator

Correct. This is the proper table.

# Summary and resources

You should have learned how Microsoft Sentinel provides a table to store indicator data accessible to Kusto Query Language (KQL) queries. And how the Threat intelligence page in Microsoft Sentinel provides the management options to maintain the indicators.

You should now be able to:

-   Manage threat indicators in Microsoft Sentinel
-   Use KQL to access threat indicators in Microsoft Sentinel

## Learn more

You can learn more by reviewing the following.

[Become a Microsoft Sentinel Ninja](https://techcommunity.microsoft.com/t5/azure-sentinel/become-an-azure-sentinel-ninja-the-complete-level-400-training/ba-p/1246310)

[Microsoft Tech Community Security Webinars](https://techcommunity.microsoft.com/t5/microsoft-security-and/security-community-webinars/ba-p/927888)