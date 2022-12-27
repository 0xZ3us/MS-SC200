https://learn.microsoft.com/en-us/training/modules/work-with-data-kusto-query-language/

# Introduction

Kusto Query Language (KQL) is the query language used to perform analysis on data to create Analytics, Workbooks, and perform Hunting in Microsoft Sentinel. Understanding how to work with fields containing structured and unstructured string data with a KQL statement provides the foundation for extracting data used in building detections in Microsoft Sentinel.

You're a Security Operations Analyst working at a company that is implementing Microsoft Sentinel. You're responsible for performing log data analysis to search for malicious activity, display visualizations, and perform threat hunting.

To query log data, you use the Kusto Query Language (KQL). Often fields in a table store structured and unstructured string data. You write KQL statements to extract and manipulate data stored in these fields. A typical scenario is a key-value pair stored in a field, and you need to query the specific value of a key.

# Extract data from unstructured string fields

Security log data is often contained in unstructured string fields and requires parsing to extract data. There are multiple ways of pulling information from string fields in KQL. The two primary operators used are extract and parse.

## extract

Extract gets a match for a regular expression from a text string. You may optionally convert the extracted substring to the indicated type.

```Kusto
print extract("x=([0-9.]+)", 1, "hello x=45.6|wo") == "45.6"

```

Arguments

-   regex: A regular expression.
    
-   captureGroup: A positive int constant indicating the capture group to extract. A "0" stands for the entire match, a "1" for the value matched by the first '('parenthesis')' in the regular expression, 2 or more for subsequent parentheses.
    
-   text: A string to search.
    
-   typeLiteral: An optional type literal (for example, typeof(long)). If provided, the extracted substring is converted to this type.
    

Returns

If regex finds a match in text: the substring matched against the indicated capture group captureGroup, optionally converted to typeLiteral.

If there's no match, or the type conversion fails: null.

The following example uses the extract function to pull out the Account Name from the Account field of the SecurityEvent table.

```Kusto
SecurityEvent
| where EventID == 4672 and AccountType == 'User'
| extend Account_Name = extract(@"^(.*\\)?([^@]*)(@.*)?$", 2, tolower(Account))
| summarize LoginCount = count() by Account_Name
| where Account_Name != ""
| where LoginCount < 10

```

## parse

Parse evaluates a string expression and parses its value into one or more calculated columns. The computed columns will have nulls for unsuccessfully parsed strings.

Syntax

`T | parse [kind=regex [flags=regex_flags] |simple|relaxed] Expression with * (StringConstant ColumnName [: ColumnType]) *`

Arguments

-   T: The input table.
    
-   kind:
    
    -   simple (the default): StringConstant is a regular string value and the match is strict. All string delimiters should appear in the parsed string, and all extended columns must match the required types.
        
    -   regex: StringConstant may be a regular expression and the match is strict. All string delimiters, which can be a regex for this mode, should appear in the parsed string, and all extended columns must match the required types.
        
    -   flags: Flags to be used in regex mode like U (Ungreedy), m (multi-line mode), s (match new line \n), i (case-insensitive) in RE2 flags.
        
    -   relaxed: StringConstant is a regular string value and the match is relaxed. All string delimiters should appear in the parsed string, but extended columns may partially match the required types. Extended columns that didn't match the required types will get the value null.
        
-   Expression: An expression that evaluates to a string.
    
-   ColumnName: The name of a column to assign a value to, extracted from the string expression.
    
-   ColumnType: Optional. The scalar value that indicates the type to convert the value to. The default is the string type.
    

Returns

The input table extended according to the list of columns that are provided to the operator.

The following statement demonstrates the parse operator, which evaluates a string expression and parses its value into one or more calculated columns. Use for structuring unstructured data.

```Kusto
let Traces = datatable(EventText:string)
[
"Event: NotifySliceRelease (resourceName=PipelineScheduler, totalSlices=27, sliceNumber=23, lockTime=02/17/2016 08:40:01, releaseTime=02/17/2016 08:40:01, previousLockTime=02/17/2016 08:39:01)",
"Event: NotifySliceRelease (resourceName=PipelineScheduler, totalSlices=27, sliceNumber=15, lockTime=02/17/2016 08:40:00, releaseTime=02/17/2016 08:40:00, previousLockTime=02/17/2016 08:39:00)",
"Event: NotifySliceRelease (resourceName=PipelineScheduler, totalSlices=27, sliceNumber=20, lockTime=02/17/2016 08:40:01, releaseTime=02/17/2016 08:40:01, previousLockTime=02/17/2016 08:39:01)",
"Event: NotifySliceRelease (resourceName=PipelineScheduler, totalSlices=27, sliceNumber=22, lockTime=02/17/2016 08:41:01, releaseTime=02/17/2016 08:41:00, previousLockTime=02/17/2016 08:40:01)",
"Event: NotifySliceRelease (resourceName=PipelineScheduler, totalSlices=27, sliceNumber=16, lockTime=02/17/2016 08:41:00, releaseTime=02/17/2016 08:41:00, previousLockTime=02/17/2016 08:40:00)"
];
Traces  
| parse EventText with * "resourceName=" resourceName ", totalSlices=" totalSlices:long * "sliceNumber=" sliceNumber:long * "lockTime=" lockTime ", releaseTime=" releaseTime:date "," * "previousLockTime=" previousLockTime:date ")" *  
| project resourceName, totalSlices, sliceNumber, lockTime, releaseTime, previousLockTime
```

# Extract data from structured string data

Strings fields may also contain structured data like JSON or Key-Value pairs. KQL provides easy access to these values for further analysis.

## Dynamic Fields

Within a Log Analytics table, there are field types defined as Dynamic. Dynamic fields contain a key-value pair such as:

Copy

```JSON
{"eventCategory":"Autoscale","eventName":"GetOperationStatusResult","operationId":"xxxxxxxx-6a53-4aed-bab4-575642a10226","eventProperties":"{\"OldInstancesCount\":6,\"NewInstancesCount\":5}","eventDataId":" xxxxxxxx -efe3-43c2-8c86-cd84f70039d3","eventSubmissionTimestamp":"2020-11-30T04:06:17.0503722Z","resource":"ch-appfevmss-pri","resourceGroup":"CH-RETAILRG-PRI","resourceProviderValue":"MICROSOFT.COMPUTE","subscriptionId":" xxxxxxxx -7fde-4caf-8629-41dc15e3b352","activityStatusValue":"Succeeded"}
```

To access the strings within a Dynamic field, use the dot notation. The DeviceDetail field from the SigninLogs table is of type dynamic. In this example, you could access the Operating System with the DeviceDetail.operatingSystem field name.

```Kusto
SigninLogs 
| extend OS = DeviceDetail.operatingSystem

```

The query example below shows the use of Dynamic fields with the SigninLogs table.

```Kusto
// Example query for SigninLogs showing how to break out packed fields.

SigninLogs 
| where TimeGenerated >= ago(1d)
| extend OS = DeviceDetail.operatingSystem, Browser = DeviceDetail.browser
| extend ConditionalAccessPol0Name = tostring(ConditionalAccessPolicies[0].displayName), ConditionalAccessPol0Result = tostring(ConditionalAccessPolicies[0].result)
| extend ConditionalAccessPol1Name = tostring(ConditionalAccessPolicies[1].displayName), ConditionalAccessPol1Result = tostring(ConditionalAccessPolicies[1].result)
| extend ConditionalAccessPol2Name = tostring(ConditionalAccessPolicies[2].displayName), ConditionalAccessPol2Result = tostring(ConditionalAccessPolicies[2].result)
| extend StatusCode = tostring(Status.errorCode), StatusDetails = tostring(Status.additionalDetails)
| extend State = tostring(LocationDetails.state), City = tostring(LocationDetails.city)
| extend Date = startofday(TimeGenerated), Hour = datetime_part("Hour", TimeGenerated)
| summarize count() by Date, Identity, UserDisplayName, UserPrincipalName, IPAddress, ResultType, ResultDescription, StatusCode, StatusDetails, ConditionalAccessPol0Name, ConditionalAccessPol0Result, ConditionalAccessPol1Name, ConditionalAccessPol1Result, ConditionalAccessPol2Name, ConditionalAccessPol2Result, Location, State, City
| sort by Date

```

## JSON

KQL provides functions to manipulate JSON stored in string fields. Many logs submit data in JSON format, which requires you to know how to transform JSON data to queryable fields.

The example below is a list of JSON related functions and operators.

| Function | Description  |
|---|---|
| parse-json() or todynamic() | Interprets a string as a JSON value and returns the value as dynamic. Use either of these functions to refer to a field: JsonField.Key or JsonField["Key"]  |
| mv-expand | is applied on a dynamic-typed array or property bag column so that each value in the collection gets a separate row. All the other columns in an expanded row are duplicated. mv_expand is the easiest way to process JSON arrays.  |
| mv-apply | Applies a subquery to each record and returns the union of the results of all subqueries. Apply a query to each value in an array. |

Run each query separately to see the results.

```Kusto
SigninLogs
| extend Location =  todynamic(LocationDetails)
| extend City =  Location.city
| extend City2 = Location["city"]
| project Location, City, City2


SigninLogs
| mv-expand Location = todynamic(LocationDetails)

SigninLogs
| mv-apply Location = todynamic(LocationDetails) on 
( where Location.city == "Canberra")

```

# Integrate external data

The externaldata operator returns a table whose schema is defined in the query itself. And whose data is read from an external storage artifact, such as a blob in Azure Blob Storage or an Azure Data Lake Storage file.

Syntax

Copy

```
 externaldata ( ColumnName : ColumnType [, ...] )
  [ StorageConnectionString [, ...] ]
  [with ( PropertyName = PropertyValue [, ...] )]
```

Arguments

-   ColumnName, ColumnType: The arguments define the schema of the table. The syntax is the same as the syntax used when defining a table in. create table.
    
-   StorageConnectionString: Storage connection strings that describe the storage artifacts holding the data to return.
    
-   PropertyName, PropertyValue, ...: More properties that describe how to interpret the data retrieved from storage, as listed under ingestion properties.
    

Currently, supported properties are:

ARGUMENTS

| Property | Type | Description  |
|---|---|---|
| format | string | Data format. If not specified, an attempt is made to detect the data format from file extension (defaults to CSV). Any of the ingestion data formats are supported.  |
| ignoreFirstRecord | bool | If set to true, indicates that the first record in every file is ignored. This property is useful when querying CSV files with headers.  |
| ingestionMapping | string | A string value that indicates how to map data from the source file to the actual columns in the operator result set. See data mappings. |

Returns

The externaldata operator returns a data table of the given schema with data parsed from the specified storage artifact, indicated by the storage connection string.

 Note

This example is not available in the demo environment.

```Kusto
Users
| where UserID in ((externaldata (UserID:string) [
    @"https://storageaccount.blob.core.windows.net/storagecontainer/users.txt" 
      h@"?...SAS..." // Secret token needed to access the blob
    ]))
| ...

```
# Create parsers with functions

Parsers are functions that define a virtual table with already parsed unstructured strings fields such as Syslog data.

In the Logs window, you create a query, select the Save button, enter the Name, and select Save As Function from the drop-down. In this case, if we name the function "PrivLogins", I can then access the table using the name PrivLogins.

```Kusto
SecurityEvent
| where EventID == 4672 and AccountType == 'User'

```

```Kusto
PrivLogins
```

# Knowledge check

1. Which KQL statement should you use to parse external data into a virtual table?

parse_json

extract

[X] externaldata

Correct. Use the externaldata operator to create a virtual table from an external source.

2. A Dynamic field contains which of the following items?

Calculated data.

[X] Key-value pair data.

Correct. The properties in the field are accessed with the dot notation.

External data.

3. To create a virtual table, save your KQL as a which type?

Module.

[X] Function.

Correct. Functions then can be referenced in other KQL statements.

Definition.

# Summary and resources

You should have learned how Kusto Query Language (KQL) is the query language used to perform analysis on data to create Analytics, Workbooks, and perform Hunting in Microsoft Sentinel.

You should now be able to:

-   Extract data from unstructured string fields using KQL
-   Extract data from structured string data using KQL
-   Create Functions using KQL

## Learn more

You can learn more by reviewing the following.

[KQL quick reference](https://learn.microsoft.com/en-us/azure/data-explorer/kql-quick-reference)

[Microsoft Tech Community Security Webinars](https://techcommunity.microsoft.com/t5/microsoft-security-and/security-community-webinars/ba-p/927888)

[Become an Microsoft Sentinel Ninja](https://techcommunity.microsoft.com/t5/azure-sentinel/become-an-azure-sentinel-ninja-the-complete-level-400-training/ba-p/1246310)