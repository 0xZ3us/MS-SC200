https://learn.microsoft.com/en-us/training/modules/analyze-results-kusto-query-language/

# Introduction

Kusto Query Language (KQL) is the query language used to perform analysis on data to create Analytics, Workbooks, and perform Hunting in Microsoft Sentinel. Understanding how to summarize and visualize data with a KQL statement provides the foundation to build detections in Microsoft Sentinel.

You're a Security Operations Analyst working at a company that is implementing Microsoft Sentinel. You're responsible for performing log data analysis to search for malicious activity, display visualizations, and perform threat hunting. To query log data, you use the Kusto Query Language (KQL). You write KQL statements that aggregate and correlate data that allows for pattern detection. One such aggregation might be the number of failed logons. This information, combined with a predetermined threshold, can be used to generate an alert for "Account with over 10 failed logons in the past hour" as an example.

The KQL summarize operator performs the calculations. To quickly see a pattern, an analyst can visualize the results in a graph. The KQL render operator performs the visualization. Combining the summarize and render operators provides the foundation for advanced visualizations, including time bucketing and time slicing.

# Use the summarize operator

The count operator with its variations will create a new column with the calculated result for the specified fields.

The first statement below will return one column that is a unique list of Activity column values.

The second statement will return a count of SecurityEvent rows where EventID equals 4688, and the count is grouped by Process and Computer. Because of the by clause, the result set will contain three columns: Process, Computer, Count.

Run each Query separately to see the results.

```Kusto
SecurityEvent | summarize by Activity

SecurityEvent
| where EventID == "4688"
| summarize count() by Process, Computer

```

The example below is a partial list of the most common simple aggregate functions used with the summarize operator.

| Function(s) | Description  |
|---|---|
| count(), countif() | Returns a count of the records per summarization group  |
| dcount(), dcountif() | Returns an estimate for the number of distinct values taken by a scalar expression in the summary group.  |
| avg(), avgif() | Calculates the average of Expr across the group.  |
| max(), maxif() | Returns the maximum value across the group.  |
| min(), minif() | Returns the minimum value across the group.  |
| percentile() | Returns an estimate for the specified nearest-rank percentile of the population defined by Expr. The accuracy depends on the density of population in the region of the percentile.  |
| stdev(), stdevif() | Calculates the standard deviation of Expr across the group, considering the group as a sample.  |
| sum(), sumif() | Calculates the sum of Expr across the group.  |
| variance(), varianceif() | Calculates the variance of Expr across the group, considering the group as a sample. |

## count function example

An aggregate function column can be explicitly named by including the "fieldname=" before the aggregate function.

The KQL statement will return three columns: "cnt", "AccountType", and "Computer". The "cnt" field name will replace the default "count_" name.

```Kusto
SecurityEvent
| where TimeGenerated > ago(1h)
| where EventID == 4624
| summarize cnt=count() by AccountType, Computer

```

## <dcount> function example

The following example will return a count of unique IP Addresses.

```Kusto
SecurityEvent
| summarize dcount(IpAddress)

```

## Let's take a look at a real-world example

The following statement is a rule to detect MFA failures across multiple applications for the same account.

The where operator for ResultDescription will filter the result set for results including "MFA". Next, the statement "summarize" produces a distinct count of application names and group by User and IP Address. Finally, there's a check against a variable created (threshold) to see if the number exceeds the allowed amount.

```Kusto
let timeframe = 1d;

let threshold = 3;

SigninLogs
| where TimeGenerated >= ago(timeframe)
| where ResultDescription has "MFA"
| summarize applicationCount = dcount(AppDisplayName) by UserPrincipalName, IPAddress
| where applicationCount >= threshold

```
# Use the summarize operator to filter results

The arg_max() and arg_min() functions filter out top and bottom rows respectively.

## arg_max function

The following statement will return the most current row from the SecurityEvent table for the computer SQL12.NA.contosohotels.com. The * in the arg_max function requests all columns for the row.

```Kusto
SecurityEvent 
| where Computer == "SQL12.na.contosohotels.com"
| summarize arg_max(TimeGenerated,*) by Computer

```

## arg_min function

In this statement, the oldest SecurityEvent for the computer SQL12.NA.contosohotels.com will be returned as the result set.

```Kusto
SecurityEvent 
| where Computer == "SQL12.na.contosohotels.com"
| summarize arg_min(TimeGenerated,*) by Computer

```

## Revisiting the result pipe

The order results pass through the pipe character matters. Review the following two KQL statements. What is the difference between the result sets?

Run each Query separately to see the results.

```Kusto
// Statement 1

SecurityEvent
| summarize arg_max(TimeGenerated, *) by Account
| where EventID == "4624"

// Statement 2

SecurityEvent
| where EventID == "4624"
| summarize arg_max(TimeGenerated, *) by Account

```

Statement 1 will have Accounts for which the last activity was a Logon.

The SecurityEvent table will first be summarized and return the most current row for each Account. Then only rows with EventID equal to 4624 (Login) will be returned.

Statement 2 will have the most recent Logon for Accounts that have logged in.

The SecurityEvent table will be filtered to only include EventID = 4624. Then these results will be summarized for the most current Logon row by Account.

# Use the summarize operator to prepare data

The make_ functions return a dynamic (JSON) array based on the specific function's purpose.

## make_list() function

The function returns a dynamic (JSON) array of all the values of Expression in the group.

This KQL query will first filter the EventID with the where operator. Next, for each Computer, the results are a JSON array of Accounts. The resulting JSON array will include duplicate accounts.

```Kusto
SecurityEvent
| where EventID == "4624"
| summarize make_list(Account) by Computer

```

![Screenshot of a make_list function results.](https://learn.microsoft.com/en-us/training/wwl-sci/analyze-results-kusto-query-language/media/make-list-results.png)

## make_set() function

Returns a dynamic (JSON) array containing distinct values that Expression takes in the group.

This KQL query will first filter the EventID with the where operator. Next, for each Computer, the results are a JSON array of unique Accounts.

```Kusto
SecurityEvent
| where EventID == "4624"
| summarize make_set(Account) by Computer

```

![Screenshot of a Make_set function results.](https://learn.microsoft.com/en-us/training/wwl-sci/analyze-results-kusto-query-language/media/make-set-results.png)

# Use the render operator to create visualizations

The render operator generates a visualization of the query results.

The supported visualizations are:

-   `areachart`
-   `barchart`
-   `columnchart`
-   `piechart`
-   `scatterchart`
-   `timechart`

```Kusto
SecurityEvent 
| summarize count() by Account
| render barchart

```

## Use the summarize operator to create time series

The bin() function rounds values down to an integer multiple of the given bin size. Used frequently in combination with summarize by .... If you have a scattered set of values, the values are grouped into a smaller set of specific values. Combining the generated time series and pipe to a render operator with a type of timechart provides a time-series visualization.

```Kusto
SecurityEvent 
| summarize count() by bin(TimeGenerated, 1d) 
| render timechart

```

# Knowledge check

1. The `dcount()` function will do which of the following?

Return a day count on the expression difference provided to the function.

Return a difference count on the expression provided to the function.

[X] Return a distinct count on the expression provided to the function.

Correct. `dcount` provides a distinct count.

2. The `arg_max()` function will do which of the following?

Returns the maximum value for each column passed to the function.

Returns a JSON Array of maximum values for each column passed to the function.

[X] Returns a row selected based on the row having the max value for an expression.

Correct. The `arg_max` function returns a row selected based on the row having the max value for an expression.

3. The `bin()` function provides the most value to which type of chart?

`scatterchart`

[X] `timechart`

Correct. `Bin()` will round down values to an integer multiple of the given bin size. The `timechart` displays a time series based on the bin size.

`barchart`

# Summary and resources

You should have learned how Kusto Query Language (KQL) is the query language used to perform analysis on data to create Analytics, Workbooks, and perform Hunting in Microsoft Sentinel.

You should now be able to:

-   Summarize data using KQL statements
-   Render visualizations using KQL statements

## Learn more

You can learn more by reviewing the following.

[KQL quick reference](https://learn.microsoft.com/en-us/azure/data-explorer/kql-quick-reference)

[Microsoft Tech Community Security Webinars](https://techcommunity.microsoft.com/t5/microsoft-security-and/security-community-webinars/ba-p/927888)

[Become a Microsoft Sentinel Ninja](https://techcommunity.microsoft.com/t5/azure-sentinel/become-an-azure-sentinel-ninja-the-complete-level-400-training/ba-p/1246310)