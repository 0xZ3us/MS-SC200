https://learn.microsoft.com/en-us/training/modules/construct-kusto-query-language-statements/

# Introduction

Kusto Query Language (KQL) is the query language used to perform analysis on data to create Analytics, Workbooks, and perform Hunting in Microsoft Sentinel. Understanding basic KQL statement structure provides the foundation to build more complex statements.

You're a Security Operations Analyst working at a company that is implementing Microsoft Sentinel. You're responsible for performing log data analysis to search for malicious activity, display visualizations, and perform threat hunting. To query log data, you use the Kusto Query Language (KQL).

To learn to write KQL, you start with the basic structure of a KQL statement. The basics include what table to query, how to apply a filter, and how to return specific columns.

# Understand the Kusto Query Language statement structure

A KQL query is a read-only request to process data and return results. The request is stated in plain text, using a data-flow model designed to make the syntax easy to read, write, and automate. The query uses schema entities organized in a hierarchy similar to SQL's: databases, tables, and columns.

The query consists of a sequence of query statements. At least one statement is a tabular expression statement that produces data arranged in a table-like mesh of columns and rows. The query's tabular expression statements produce the results of the query.

The tabular expression statement's syntax has tabular data flow from one tabular query operator to another. Starting with the data source, then flowing through a set of data transformation operators bound together by using the pipe (|) delimiter.

For example, the following query has a single statement, which is a tabular expression statement. The statement starts with a table called SecurityEvent. The EventID column's value filters the data (rows) and then the results are summarized by creating a new column for the count() by Account. Next, in the Prepare phase, the results are then limited to 10 rows.

![Diagram of K Q L Statement showing data, condition and evidence.](https://learn.microsoft.com/en-us/training/wwl-sci/construct-kusto-query-language-statements/media/kql-pipe.png)

 Important

It is essential to understand how the results flow through the pipe "|". Everything on the left of the pipe is processed then passed to the right of the pipe.

## Access the Log Analytics demo environment

Microsoft provides access to an environment to practice writing KQL statements. The only requirement is to have an account to log into Azure. There are no charges to your Azure account to access this environment. You can execute the KQL statements in this module in the demo environment.

You can access the demo environment at [https://aka.ms/lademo](https://aka.ms/lademo)

 Important

The log analytics demo database is a dynamic environment. The events recorded in the tables in that environment are continuously updating with different security events. This is similar to what a person would experience in a real-world security operations setting. As a result, finite queries in this training may show no results depending on the state of the demo database at the time the query is run. For example, a query on the _SecurityEvent_ table for "discardEventID = 4688" within the last day may show no results if that particular event last took place three days ago. Therefore, you may need to adjust variables in the scripts listed in this training ad hoc depending on what data is in the demo database at the time you run the script in order for the query to show results. These script adjustments are similar to what you would perform in the real world and should help you learn how the specific parts of the script function.

![Screenshot of the Log Analytics Demo Environment.](https://learn.microsoft.com/en-us/training/wwl-sci/construct-kusto-query-language-statements/media/log-analytics-demo-2.png)

The Query window has three primary sections:

-   The left area is a reference list of the tables in the environment.
    
-   The middle top area is the Query editor.
    
-   The bottom area is the Query Results.
    

Before running a query, adjust the time range to scope the data. To change the result columns displayed, select the Columns box, and choose the required columns.

# Use the search operator

The search operator provides a multi-table/multi-column search experience. Although the search operator is easy to use, when compared to the where operator it's inefficient. Even with this inefficiency, you can use search to find data when unsure which table or column to filter.

The first statement will search for "err" across all tables. The second statement will search for "err" in tables SecurityEvent, SecurityAlert, and tables starting with A.

Try each of these queries separately to see the results.

 Tip

For the first search query, you may need to adjust the Time range to "Last hour" in the query window to avoid an error.

```Kusto
search "err"

search in (SecurityEvent,SecurityAlert,A*) "err"

```

# Use the where operator

The where operator filters a table to the subset of rows that satisfy a predicate.

Try each of these queries separately to see the results.

```Kusto
SecurityEvent
| where TimeGenerated > ago(1d)

SecurityEvent
| where TimeGenerated > ago(1h) and EventID == "4624"

SecurityEvent
| where TimeGenerated > ago(1h)
| where EventID == 4624
| where AccountType =~ "user"

SecurityEvent | where EventID in (4624, 4625)

```

# Use the let statement

Let statements bind names to expressions. For the rest of the scope, where the let statement appear, the name refers to its bound value. Let statements improve modularity and reuse since they allow you to break a potentially complex expression into multiple parts. Each part is bound to a name through the let statement, and together they compose the whole. Let statements allow for the creation of user-defined functions and views. The views are expressions whose results look like a new table.

## Declare and reuse variables

Let statements allow for the creation of variables to be used in later statements. In this example, timeOffSet and discardEventId are created and used as part of the SecurityEvent "where" clause.

```Kusto
let timeOffset = 7d;
let discardEventId = 4688;

SecurityEvent
| where TimeGenerated > ago(timeOffset*2) and TimeGenerated < ago(timeOffset)
| where EventID != discardEventId

```

 Tip

"ago()" is a function that will take the current Date and Time and subtract the value provided.

## Declare dynamic tables or lists

Let statements allow for the creation of dynamic tables or lists.

```Kusto
let suspiciousAccounts = datatable(account: string) [
    @"\administrator", 
    @"NT AUTHORITY\SYSTEM"
];
SecurityEvent | where Account in (suspiciousAccounts)
```

```Kusto
let LowActivityAccounts =
    SecurityEvent 
    | summarize cnt = count() by Account 
    | where cnt < 1000;
LowActivityAccounts | where Account contains "SQL"
```

# Use the extend statement

The extend operator will create calculated columns and append the new columns to the result set.

The KQL example below uses the extend operator to create a new column, StartDir containing the directory a process was started in. The StartDir column is a calculated column containing the results of a substring function.

```Kusto

SecurityEvent
| where ProcessName != "" and Process != ""
| extend StartDir =  substring(ProcessName,0, string_size(ProcessName)-string_size(Process))

```

# Use the order by operator

Sort the rows of the input table by one or more columns.

The order by operator can utilize any column or multiple columns by using a comma separator. Each column can be ascending or descending. The default order for a column is descending.

```Kusto
SecurityEvent
| where ProcessName != "" and Process != ""
| extend StartDir =  substring(ProcessName,0, string_size(ProcessName)-string_size(Process))
| order by StartDir desc, Process asc

```

# Use the project operators

The project operators control what columns to include, add, remove, or rename in the result set of a statement.

There are multiple types of project operators. The following table is a list of the variations.

| Operator | Description  |
|---|---|
| project | Select the columns to include, rename or drop, and insert new computed columns.  |
| project-away | Select what columns from the input to exclude from the output.  |
| project-keep | Select what columns from the input to keep in the output.  |
| project-rename | Select the columns to rename in the resulting output.  |
| project-reorder | Set the column order in the resulting output. |

## Project operator

Select the columns to include, rename or drop, and insert new computed columns.

 Tip

The project operator will limit the size of the result set, which will increase performance

Run each Query separately to see the results.

```Kusto
SecurityEvent
| project Computer, Account


SecurityEvent
| where ProcessName != "" and Process != ""
| extend StartDir =  substring(ProcessName,0, string_size(ProcessName)-string_size(Process))
| order by StartDir desc, Process asc
| project Process, StartDir

```

## Project-away operator

Select what columns from the input to exclude from the output.

This example builds from our previous extend and order by operators. The project-away will remove the unnecessary column from the result set. In this example, we'll remove the ProcessName column.

```Kusto
SecurityEvent
| where ProcessName != "" and Process != ""
| extend StartDir =  substring(ProcessName,0, string_size(ProcessName)-string_size(Process))
| order by StartDir desc, Process asc
| project-away ProcessName

```

# Knowledge check

1. What does the search operator do?

[X] Searches across tables and isn't column-specific.

Correct. The search will search across all columns in tables specified

Searches only data in the last hour.

Searches in columns specified.

2. What are project operators?

Project operators filter a table to the subset of rows that satisfy a predicate.

Project operators create summarized columns and append them to the result set.

[X] Project operators add, remove, or rename columns in a result set.

Correct. project operators control what columns to include, add, remove or rename in the result set of a statement.

# Summary and resources

You should have learned how basic KQL statement structure provides the foundation to build more complex statements.

You should now be able to:

-   Construct KQL statements
-   Search log files for security events using KQL
-   Filter searches based on event time, severity, domain, and other relevant data using KQL

## Learn more

You can learn more by reviewing the following.

[KQL quick reference | Microsoft Docs](https://learn.microsoft.com/en-us/azure/data-explorer/kql-quick-reference)

[Microsoft Tech Community Security Webinars](https://techcommunity.microsoft.com/t5/microsoft-security-and/security-community-webinars/ba-p/927888)

[Become a Microsoft Sentinel Ninja](https://techcommunity.microsoft.com/t5/azure-sentinel/become-an-azure-sentinel-ninja-the-complete-level-400-training/ba-p/1246310)

