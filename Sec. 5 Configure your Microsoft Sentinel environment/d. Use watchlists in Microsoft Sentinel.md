https://learn.microsoft.com/en-us/training/modules/use-watchlists-azure-sentinel/

# Introduction

Microsoft Sentinel provides a table to store list data accessible to Kusto Query Language (KQL) queries. The Watchlists page in Microsoft Sentinel provides the management options to maintain the lists.

You're a Security Operations Analyst working at a company that has implemented Microsoft Sentinel. The Security Operations team members need to prioritize alerts that are impacting high-value target servers.

You must import a list of server names into Microsoft Sentinel, which can then be used by detection queries to set a priority field. You import a list of servers into the Watchlist page of Microsoft Sentinel. Once created, you instruct the Security Operations team to use the watch list in their KQL queries.

After completing this module, you'll be able to:

-   Create a watchlist with Microsoft Sentinel
-   Use KQL to access the watchlist with Microsoft Sentinel

# Plan for watchlists

Microsoft Sentinel watchlists enable collecting data from external data sources for correlation with the events in your Microsoft Sentinel environment. Once created, you can use watchlists in your search, detection rules, threat hunting, and response playbooks. Watchlists are stored in your Microsoft Sentinel workspace as name-value pairs and are cached for optimal query performance and low latency.

Common scenarios for using watchlists include:

-   Investigating threats and responding to incidents quickly with the rapid import of IP addresses, file hashes, and other data from CSV files. Once imported, you can use watchlist name-value pairs for joins and filters in alert rules, threat hunting, workbooks, notebooks, and general queries.
    
-   Importing business data as a watchlist. For example, import user lists with privileged system access, or terminated employees, and then use the watchlist to create allowlists and blocklists used to detect or prevent those users from logging in to the network.
    
-   Reducing alert fatigue. Create allowlists to suppress alerts from a group of users, such as users from authorized IP addresses that perform tasks that would normally trigger the alert, and prevent benign events from becoming alerts.
    
-   Enriching event data. Use watchlists to enrich your event data with name-value combinations derived from external data sources.

# Create a watchlist

To create a watchlist from the Azure portal perform these steps:

1.  Go to **Microsoft Sentinel > Configuration > Watchlist** and select **Add new**.
    
    ![Screen shot of creating a Sentinel Watchlist List.](https://learn.microsoft.com/en-us/training/wwl-sci/use-watchlists-azure-sentinel/media/watchlist-create.png)
    
2.  On the General page, provide the name, description, and alias for the watchlist, then select **Next**.
    
3.  On the Source page, select the dataset type, upload a file, then select **Next**.
    
     Note
    
    File uploads are currently limited to files of up to 3.8 MB in size.
    
4.  Next, review the information, verify that it's correct, then select **Create**. A notification appears once the watchlist is ready.
    

To use the watchlist data in KQL, use the KQL function _GetWatchlist('watchlist name').

```Kusto
_GetWatchlist('HighValueMachines')
```

# Manage watchlists

We recommend you edit an existing watchlist instead of deleting and recreating a watchlist. Log analytics has a five-minute SLA for data ingestion. If you delete and recreate a watchlist, you might see both the deleted and recreated entries in Log Analytics during this five-minute window. If you see these duplicate entries in Log Analytics for a longer period of time, submit a support ticket.

## Edit a watchlist item

Edit a watchlist to edit or add an item to the watchlist.

1.  In the Azure portal, go to Microsoft Sentinel and select the appropriate workspace.
    
2.  Under Configuration, select **Watchlist**.
    
3.  Select the watchlist you want to edit.
    
4.  On the details pane, select **Update watchlist > Edit watchlist items**.
    
5.  To edit an existing watchlist item,
    
    1.  Select the checkbox of that watchlist item.
        
    2.  Edit the item.
        
    3.  Select Save.
        
    4.  Select Yes at the confirmation prompt.
        
6.  To add a new item to your watchlist,
    
    1.  Select Add new.
        
    2.  Fill in the fields in the Add watchlist item panel.
        
    3.  At the bottom of that panel, select Add.
        

## Bulk update a watchlist

When you have many items to add to a watchlist, use bulk update. A bulk update of a watchlist appends items to the existing watchlist. Then, it de-duplicates the items in the watchlist where all the value in each column match.

If you've deleted an item from your watchlist file and upload it, bulk update won't delete the item in the existing watchlist. Delete the watchlist item individually. Or, when you have many deletions, delete and recreate the watchlist.

The updated watchlist file you upload must contain the search key field used by the watchlist with no blank values.

To bulk update a watchlist,

1.  In the Azure portal, go to Microsoft Sentinel and select the appropriate workspace.
    
2.  Under Configuration, select **Watchlist**.
    
3.  Select the watchlist you want to edit.
    
4.  On the details pane, select **Update watchlist > Bulk update**.
    
5.  Under Upload file, drag and drop or browse to the file to upload.
    
6.  If you get an error, fix the issue in the file. Then select Reset and try the file upload again.
    
7.  Select **Next: Review and update > Update**.

# Knowledge check

1. Which of the following operations is a typical scenario for using a Microsoft Sentinel watchlist?

Creating more alerts to help identify issues.

Export business data as a watchlist.

[X] Responding to incidents quickly with the rapid import of IP addresses.

Correct. This is a typical scenario for using Microsoft Sentinel watchlist.

2. How do you access a new watchlist named MyList in KQL?

_Watchlist('MyList ')

[X] _GetWatchlist('MyList')

Correct. This is the proper function.

_Getlist('MyList ')

# Summary and resources

You should have learned how Microsoft Sentinel provides a table to store list data accessible to Kusto Query Language (KQL) queries. And that the Watchlists page in Microsoft Sentinel provides the management options to maintain the lists.

You should now be able to:

-   Create a watchlist with Microsoft Sentinel
-   Use KQL to access the watchlist with Microsoft Sentinel

## Learn more

You can learn more by reviewing the following.

[Become a Microsoft Sentinel Ninja](https://techcommunity.microsoft.com/t5/azure-sentinel/become-an-azure-sentinel-ninja-the-complete-level-400-training/ba-p/1246310)

[Microsoft Tech Community Security Webinars](https://techcommunity.microsoft.com/t5/microsoft-security-and/security-community-webinars/ba-p/927888)