---
external help file: Microsoft.SqlServer.Management.PSSnapins.dll-Help.xml
online version: 
schema: 2.0.0
ms.assetid: B8007141-926D-4E64-9ABA-EFA5DA2CF447
updated_at: 3/13/2017 4:14 PM
ms.date: 3/13/2017
content_git_url: https://github.com/MicrosoftDocs/sql-docs-powershell/blob/live/sqlserver-cmdlets/sqlserver/vlatest/Read-SqlViewData.md
original_content_git_url: https://github.com/MicrosoftDocs/sql-docs-powershell/blob/live/sqlserver-cmdlets/sqlserver/vlatest/Read-SqlViewData.md
gitcommit: https://github.com/MicrosoftDocs/sql-docs-powershell/blob/6eefe64a0ce19459190f09768267a4c79f9a6af9/sqlserver-cmdlets/sqlserver/vlatest/Read-SqlViewData.md
ms.topic: reference
author: stevestein
ms.author: sstein
keywords: powershell, cmdlet
manager: jhubbard
open_to_public_contributors: True
ms.service: sql-server
---

# Read-SqlViewData

## SYNOPSIS
Reads data from the view of a SQL database.

## SYNTAX

### ByPath (Default)
```
Read-SqlViewData [-TopN <Int64>] [-ColumnName <String[]>] [-ColumnOrder <String[]>]
 [-ColumnOrderType <OrderType[]>] [-OutputAs <OutputTypeSingleTable>] [[-Path] <String[]>]
 [-InformationAction <ActionPreference>] [-InformationVariable <String>] [<CommonParameters>]
```

### ByName
```
Read-SqlViewData [-ViewName <String>] [-TopN <Int64>] [-ColumnName <String[]>] [-ColumnOrder <String[]>]
 [-ColumnOrderType <OrderType[]>] [-OutputAs <OutputTypeSingleTable>] [-DatabaseName <String>]
 [-SchemaName <String>] [-IgnoreProviderContext] [-SuppressProviderContextWarning]
 [[-ServerInstance] <String[]>] [-Credential <PSCredential>] [-ConnectionTimeout <Int32>]
 [-InformationAction <ActionPreference>] [-InformationVariable <String>] [<CommonParameters>]
```

### ByObject
```
Read-SqlViewData [-TopN <Int64>] [-ColumnName <String[]>] [-ColumnOrder <String[]>]
 [-ColumnOrderType <OrderType[]>] [-OutputAs <OutputTypeSingleTable>] [-InputObject] <ScriptSchemaObjectBase[]>
 [-InformationAction <ActionPreference>] [-InformationVariable <String>] [<CommonParameters>]
```

## DESCRIPTION
The **Read-SqlViewData** cmdlet reads data stored in the view of a SQL database.
You can select which columns to read, limit the number of rows, and sort and order columns.

You can use this cmdlet with the Windows PowerShell SQL provider.
This cmdlet can infer information such as server, database, schema, and table from its current path.

This cmdlet supports the follow output formats: 

- DataSet.
An object of type **System.Data.DataSet** that contains one table. 
- DataTable.
An object of type **System.Data.DataTable**.
The **TableName** property of this object is the same as the table that this cmdlet queries. 
- DataRows.
A collection of **System.Data.DateRow** objects.

## EXAMPLES

### Example 1: Get two rows from a view
```
PS C:\> Read-SqlViewData -ServerInstance "MyServer\MyInstance" -DatabaseName "MyDatabase" -SchemaName "dbo" -ViewName "MyView" -TopN 2
Id Name   Amount
-- ----   ------
10 AAAAA  -1.2
11 BBBBB  1.2
```

This command gets the first two rows from the database view \[MyDatabase\].\[dbo\].\[MyView\] on the MyServer\MyInstance instance.
The *TopN* parameter specifies the number of rows.

### Example 2: Display a whole table
```
PS C:\> cd SQLSERVER:\sql\MyServer\MyInstance\Databases\MyDatabase\Views\dbo.MyView
PS SQLSERVER:\sql\MyServer\MyInstance\Databases\MyDatabase\Views\dbo.MyView> Read-SqlViewData
Id Name Amount
-- ---- ------
10 AAAA -1.2
11 BBBB 1.2
12 CCCC -1.0
13 DDDD -2.0
```

The first command changes the location to be a view in the SQLSERVER provider.
The command prompt reflects the new location.
For more information, type `Get-Help about_Providers`.

The second command displays the whole table.
Because the command uses its context, it does not specify any parameters.

### Example 3: Display selected sorted columns
```
PS C:\> cd SQLSERVER:\sql\MyServer\MyInstance\Databases\MyDatabase\Views\dbo.MyView
PS SQLSERVER:\sql\MyServer\MyInstance\Databases\MyDatabase\Views\dbo.MyView> Read-SqlViewData -TopN 3 -ColumnName "Id","Name" -ColumnOrder "Id","Name" -ColumnOrderType DESC,ASC
Id Name
-- ----
12 CCCC
11 BBBB
10 AAAA
```

The first command changes the location to be a view in the SQLSERVER provider.
The command prompt reflects the new location.

The second command displays two columns in the order specified by the *ColumnOrder* parameter.
The command specifies how many rows to display and the sort order for the columns.
Sorting is performed on the server.

## PARAMETERS

### -TopN
Specifies the number of rows of data that this cmdlet returns.
If you do not specify this parameter, the cmdlet returns all the rows.

```yaml
Type: Int64
Parameter Sets: (All)
Aliases: First

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ColumnName
Specifies an array of names of columns that this cmdlet returns.

```yaml
Type: String[]
Parameter Sets: (All)
Aliases: ColumnToReturn

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ColumnOrder
Specifies an array of names of columns by which this cmdlet sorts the columns that it returns.

```yaml
Type: String[]
Parameter Sets: (All)
Aliases: OrderBy

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ColumnOrderType
Specifies an array of order types for columns that this cmdlet returns.
The acceptable values for this parameter are:

- ASC.
Ascending. 
- DESC.
Descending.

The values that you specify for this parameter match the columns that you specify in the *ColumnOrder* parameter.
This cmdlet ignores any extra values.

```yaml
Type: OrderType[]
Parameter Sets: (All)
Aliases: 

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -OutputAs
Specifies the type of output.
The acceptable values for this parameter are:

- DataSet 
- DataTable 
- DataRows

```yaml
Type: OutputTypeSingleTable
Parameter Sets: (All)
Aliases: As

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Path
Specifies the path of the view that this cmdlet reads.

```yaml
Type: String[]
Parameter Sets: ByPath
Aliases: 

Required: False
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -InformationAction
Specifies how this cmdlet responds to an information event.

The acceptable values for this parameter are:

- Continue
- Ignore
- Inquire
- SilentlyContinue
- Stop
- Suspend

```yaml
Type: ActionPreference
Parameter Sets: (All)
Aliases: infa

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -InformationVariable
Specifies an information variable.

```yaml
Type: String
Parameter Sets: (All)
Aliases: iv

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ViewName
Specifies the name of the view from which this cmdlet reads.

If you run this cmdlet in the context of a database or a child item of a database, the cmdlet ignores this parameter value.
Specify the *IgnoreProviderContext* parameter for the cmdlet to use the value of the *ViewName* parameter anyway.

```yaml
Type: String
Parameter Sets: ByName
Aliases: Name

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -DatabaseName
Specifies the name of the database that contains the view.

If you run this cmdlet in the context of a database or a child item of a database, the cmdlet ignores this parameter value.
Specify the *IgnoreProviderContext* parameter for the cmdlet to use the value of the *DatabaseName* parameter anyway.

```yaml
Type: String
Parameter Sets: ByName
Aliases: 

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -SchemaName
Specifies the name of the schema for the view.

If you run this cmdlet in the context of a database or a child item of a database, the cmdlet ignores this parameter value.
Specify the *IgnoreProviderContext* parameter for the cmdlet to use the value of the *SchemaName* parameter anyway.

```yaml
Type: String
Parameter Sets: ByName
Aliases: 

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -IgnoreProviderContext
Indicates that this cmdlet does not use the current context to override the values of the *ServerInstance*, *DatabaseName*, *SchemaName*, and *ViewName* parameters.
If you do not specify this parameter, the cmdlet ignores the values of these parameters, if possible, in favor of the context in which you run the cmdlet.

```yaml
Type: SwitchParameter
Parameter Sets: ByName
Aliases: 

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -SuppressProviderContextWarning
Indicates that this cmdlet suppresses the warning message that states that the cmdlet uses the provider context.

```yaml
Type: SwitchParameter
Parameter Sets: ByName
Aliases: 

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ServerInstance
Specifies the name of an instance of SQL Server.
For the default instance, specify the computer name.
For named instances, use the format ComputerName\InstanceName.

If you run this cmdlet in the context of a database or a child item of a database, the cmdlet ignores this parameter value.
Specify the *IgnoreProviderContext* parameter for the cmdlet to use the value of the *ServerInstance* parameter anyway.

```yaml
Type: String[]
Parameter Sets: ByName
Aliases: 

Required: False
Position: 1
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -Credential
Specifies a **PSCredential** object for the connection to SQL Server.
To obtain a credential object, use the **Get-Credential** cmdlet.
For more information, type `Get-Help Get-Credential`.

```yaml
Type: PSCredential
Parameter Sets: ByName
Aliases: 

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ConnectionTimeout
Specifies the number of seconds to wait for a server connection before a time-out failure.
The time-out value must be an integer between 0 and 65534.
If 0 is specified, connection attempts do not time out.

```yaml
Type: Int32
Parameter Sets: ByName
Aliases: 

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -InputObject
Specifies an array of SQL Server Management Objects (SMO) objects that represent the view that this cmdlet reads.

```yaml
Type: ScriptSchemaObjectBase[]
Parameter Sets: ByObject
Aliases: 

Required: True
Position: 1
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### CommonParameters
This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable. For more information, see about_CommonParameters (http://go.microsoft.com/fwlink/?LinkID=113216).

## INPUTS

## OUTPUTS

## NOTES

## RELATED LINKS
