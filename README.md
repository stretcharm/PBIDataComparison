# PBIDataComparison 
# PowerBI Data Comparison Tool

Here is a PowerBI Document designed to show differences in data from two simillar data sets

Its a common, but difficult requirment to check data sets against each other. To solve this problem 
I've build a some PowerBI documents that can be used to compare a SQL or file based data sets.

## Features

- Compare one or two servers
- Compare the same or different queries
- Compare two files
- Profile Summary
- Support Number, datetime or text datatypes
- Works with a record key and date
- Summary of differences with tooltips and drilldowns
- Idenitfy Missing data or different values
- Number Differences
- Dynamically Unpivots the data so it can be analysed for differences

## How to use the Tool

### File based Comparison

Set Parameters DataSetName, FilePath1, FilePath2, File1, File2, FileFormat1 and FileFormat2 

File Formats supported are Excel, Csv or Text
Files should have headers

If the file is Excel Specify ExcelSheet1 & ExcelSheet2

The files can be the same or different, but should provide the same date range and columns. 
If the column names are different alias one query so they have the same name. 

Data Set need to have 2 fields 
- RecordKey = Unique key for the data. This can be a composite key by concatinating the columns into a unique RecordKey
- RecordDate = Date of the Record or Dummy date like today if there is no Record Date

So either make sure your Data has a Columns named RecordKey & RecordDate or Rename/Create Columns in the PowerBI QueryEditor for Quer1Data and Query2Data
You can also adjust file columns in the QueryData1 & QueryData1

### SQL or Query based Comparison

Set Parameters DataSetName, Server1, Server2, Database1, Database2

Set the Select Query for the Data you want to Compare.

Query1 and Query2 can be the same or Different, but should Provide the same date range and columns. If the Column names are different alias one query so they have the same name.
If the are the same you can Simple set 
   let
       Source = Query1 
   in
       Source
in Query2

Data Set need to have 2 fields 
- RecordKey = Unique key for the data. This can be a composite key by concatinating the columns into a unique RecordKey
- RecordDate = Date of the Record or Dummy date like today if there is no Record Date

e.g.
```
    SELECT InbvoiceID as RecordKey,
           InvoiceDate as RecordDate
           Quantity,
           Amount
    FROM Invoice
```

### Unpivoted SQL or Query based Comparison

Set Parameters DataSetName, Server1, Server2, Database1, Database2

Set the Select Query for the Data you want to Compare.

Query1 and Query2 can be the same or Different, but should Provide the same date range and columns. If the Column names are different alias one query so they have the same name.
If the are the same you can Simple set 
   let
       Source = Query1 
   in
       Source
in Query2

Data Set need to have 2 fields 
- RecordKey = Unique key for the data. This can be a composite key by concatinating the columns into a unique RecordKey
- RecordDate = Date of the Record or Dummy date like today if there is no Record Date
- Attribute = The name of the data Attribute/element
- Value = The result of the Attribute Value

e.g.
```
    SELECT DataID as RecordKey,
           RecordedData as RecordDate
           IntegrityName as Attribute,
           IntegrityValue as [Value]
    FROM IntegrityData
```

### Using the PowerBI Report

Pages are filtered using the new Filter Panes

Various Drillthroughs or Tooltips are avilable depending on the visual

Once loaded you have these Pages or Sets of Pages
- Summary - Shows summary of the data 
- Profile - 2 Pages with the Data Set Profile in either a table or matrix
- Queries - Infomation about the queries and parameter settins
- Numbers - Pages with details for the Number Based values
- Text - Pages with details for the Text Based values
- DataTimes - Pages with details for the Datetime Based values
- Drillthroughs - Drillthroughs for Number, Datetime and Text values.

### Tips

Keep data sets small to start with then expand as large data sets take a long time to load.


### Compatibility
- PowerBI Desktop february 2019
- PowerBI Report Server Version January 2019







