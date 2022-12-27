https://learn.microsoft.com/en-us/training/modules/build-multi-table-statements-kusto-query-language/

# Introduction

Kusto Query Language (KQL) is the query language used to perform analysis on data to create Analytics, Workbooks, and perform Hunting in Microsoft Sentinel. Understanding how to correlate data from different tables with a KQL statement provides the foundation to build detections in Microsoft Sentinel.

You're a Security Operations Analyst working at a company that is implementing Microsoft Sentinel. You're responsible for performing log data analysis to search for malicious activity, display visualizations, and perform threat hunting.

To query log data, you use the Kusto Query Language (KQL). Often a result set from a KQL statement needs to be combined or joined with another result set. You can use the union operator to combine two result sets. The join operator joins rows together based on a key value. You need to understand how the order of a KQL statement impacts your expected results.

# Use the union operator

The union operator takes two or more tables and returns the rows of all of them. Understanding how results are passed and impacted with the pipe character is essential.

Based on the time window set in the Query window:

-   Query 1 will return all rows of SecurityEvent and all rows of SigninLogs
    
-   Query 2 will return one row and column, which is the count of all rows of SecurityEvent and all rows of SigninLogs
    
-   Query 3 will return all rows of SecurityEvent and one row for SigninLogs.
    

Run each Query separately to see the results.

```Kusto
// Query 1

SecurityEvent 
| union SigninLogs  

// Query 2

SecurityEvent 
| union SigninLogs  
| summarize count() 
| project count_

// Query 3

SecurityEvent 
| union (SigninLogs | summarize count()| project count_)

```

The union operator supports wildcards to union multiple tables. The following KQL will create a count for the rows in all tables with names that start with Security.

```Kusto
union Security* 
| summarize count() by Type

```

# Use the join operator

The join operator merges the rows of two tables to form a new table by matching the specified columns' values from each table.

Syntax

LeftTable | join [JoinParameters] ( RightTable ) on Attributes

```Kusto
SecurityEvent 
| where EventID == "4624" 
| summarize LogOnCount=count() by EventID, Account 
| project LogOnCount, Account 
| join kind = inner (
     SecurityEvent 
     | where EventID == "4634" 
     | summarize LogOffCount=count() by EventID, Account 
     | project LogOffCount, Account 
) on Account

```

The first table specified in the join is considered the Left table. The table after the join keyword is the right table. The columns from the tables are designated, the `$left.Column` and the `$right.Column` to distinguish which tables columns you're referencing.

When joining tables, you use Join flavors to determine the joining behavior. It's essential to understand the impact of records on the left and right side based on the join flavor. The graphic below shows which records will be kept if there's or isn't a matching record in the other dataset. The **inner join** will only show records from the left side if there's a matching record on the right side. The right side will also require a left side record.

![Diagram of Example join types, showing where how joins work.](https://learn.microsoft.com/en-us/training/wwl-sci/build-multi-table-statements-kusto-query-language/media/kusto-query-language-m03-01.png)

| Join Flavor | Output Records  |
|---|---|
| kind=leftanti, kind=leftantisemi | Returns all the records from the left side that don't have matches from the right  |
| kind=rightanti, kind=rightantisemi | Returns all the records from the right side that don't have matches from the left.  |
| kind unspecified, kind=innerunique | Only one row from the left side is matched for each value of the on key. The output contains a row for each match of this row with rows from the right  |
| kind=leftsemi | Returns all the records from the left side that have matches from the right.  |
| kind=rightsemi | Returns all the records from the right side that have matches from the left.  |
| kind=inner | Contains a row in the output for every combination of matching rows from left and right.  |
| kind=leftouter (or kind=rightouter or kind=fullouter) | Contains a row for every row on the left and right, even if it has no match. The unmatched output cells contain nulls.  |

# Knowledge check

1. Which join flavor contains a row in the output for every combination of matching rows from left and right?

kind=leftouter

[X] kind=inner

Correct. Inner contains a row in the output for every combination of matching rows from left and right.

kind=fullouter

2. When you're using the join operator, how do you specify fields from each table?

`$1.columname` and `$2.columnname`

[X] `$left.columname` and `$right.columnname`

Correct. The $left and $right preceding the field name specifies the table.

`$inner.columname` and `$outer.columnname`

3. When you use union on two tables, do the two tables need matching columns?

[X] No.

Correct. The results contain all columns from both tables.

Yes.

Only when the project operator is used.

# Summary and resources

You should have learned how Kusto Query Language (KQL) is the query language used to perform analysis on data to create Analytics, Workbooks, and perform Hunting in Microsoft Sentinel. Understanding how to correlate data from different tables with a KQL statement provides the foundation to build detections in Microsoft Sentinel.

You should now be able to:

-   Create queries using unions to view results across multiple tables using KQL
    
-   Merge two tables with the join operator using KQL
    

## Learn more

You can learn more by reviewing the following.

[KQL quick reference](https://learn.microsoft.com/en-us/azure/data-explorer/kql-quick-reference)

[Microsoft Tech Community Security Webinars](https://techcommunity.microsoft.com/t5/microsoft-security-and/security-community-webinars/ba-p/927888)

[Become a Microsoft Sentinel Ninja](https://techcommunity.microsoft.com/t5/azure-sentinel/become-an-azure-sentinel-ninja-the-complete-level-400-training/ba-p/1246310)

