---
external help file: Microsoft.SqlServer.Management.PSSnapins.dll-Help.xml
online version: 
schema: 2.0.0
ms.assetid: BF158CE2-233C-4309-A7CD-702EA19B0FA5
updated_at: 3/13/2017 4:14 PM
ms.date: 3/13/2017
content_git_url: https://github.com/MicrosoftDocs/sql-docs-powershell/blob/master/sqlserver-cmdlets/sqlserver/vlatest/Write-SqlTableData.md
original_content_git_url: https://github.com/MicrosoftDocs/sql-docs-powershell/blob/master/sqlserver-cmdlets/sqlserver/vlatest/Write-SqlTableData.md
gitcommit: https://github.com/MicrosoftDocs/sql-docs-powershell/blob/6eefe64a0ce19459190f09768267a4c79f9a6af9/sqlserver-cmdlets/sqlserver/vlatest/Write-SqlTableData.md
ms.topic: reference
author: stevestein
ms.author: sstein
keywords: powershell, cmdlet
manager: jhubbard
open_to_public_contributors: True
ms.service: sql-server
---

# Write-SqlTableData

## SYNOPSIS
Writes data to a table of a SQL database.

## SYNTAX

### ByPath (Default)
```
Write-SqlTableData [-Force] -InputData <PSObject> [-Passthru] [-Timeout <Int32>] [[-Path] <String[]>]
 [-InformationAction <ActionPreference>] [-InformationVariable <String>] [<CommonParameters>]
```

### ByName
```
Write-SqlTableData [-DatabaseName <String>] [-SchemaName <String>] [-TableName <String>]
 [-IgnoreProviderContext] [-SuppressProviderContextWarning] [-Force] -InputData <PSObject> [-Passthru]
 [-Timeout <Int32>] [[-ServerInstance] <String[]>] [-Credential <PSCredential>] [-ConnectionTimeout <Int32>]
 [-InformationAction <ActionPreference>] [-InformationVariable <String>] [<CommonParameters>]
```

### ByObject
```
Write-SqlTableData [-Force] -InputData <PSObject> [-Passthru] [-Timeout <Int32>] [-InputObject] <Table[]>
 [-InformationAction <ActionPreference>] [-InformationVariable <String>] [<CommonParameters>]
```

## DESCRIPTION
The **Write-SqlTableData** cmdlet inserts data into a table of a SQL database.
This cmdlet accepts the following input types the follow output formats: 

- **System.Data.DataSet**
- **System.Data.DataTable**
- **System.Data.DateRow** objects
- Collection of objects

If you provide a **DataSet**, only the first table in the dataset is written to the database.

You can use this cmdlet with the Windows PowerShell SQL provider.
This cmdlet can infer information such as server, database, schema, and table from its current path.

This cmdlet expects the table to exist.
By default, the cmdlet appends data to that table.
If you specify the *Force* parameter, the cmdlet generate missing objects, which include the database, the table schema, and the table itself.
This usage enables quick transfer of data into a database.
The cmdlet infers the schema of the table from the data.
The result may not be optimal.
For example, strings are mapped to NVARCHAR(MAX).

## EXAMPLES

### Example 1: Write information about processes to a table
```
PS C:\> (Get-Process | Select-Object -Property Id,ProcessName,StartTime,UserProcessorTime,WorkingSet,Description) | Write-SqlTableData -ServerInstance "MyServer\MyInstance" -DatabaseName "MyDatabase" -SchemaName "dbo" -TableName "TaskManagerDump" -Force
```

This example gets information about processes that run on a system and writes it to a table.

The command gets processes by using the Get-Process cmdlet.
The command passes the results by using the pipeline operator to the Select-Object cmdlet.
This cmdlet selects properties.
This selection avoids any problems with complex types.

This part of the command is in parentheses so that it sends the process objects to the current cmdlet in a batch.
The cmdlet passes the results to the current cmdlet.

The current cmdlet writes the data to \[MyDatabase\].\[dbo\].\[TaskManagerDump\] on MyServer\MyInstance.
Because you specify the *Force* parameter, if the database, schema, and table do not exist, this cmdlet creates them.

### Example 2: Write data to a table
```
PS C:\> cd SQLSERVER:\SQL\MyServer\MyInstance\Databases\MyDatabase\Tables
PS SQLSERVER:\SQL\MyServer\MyInstance\Databases\MyDatabase\Tables> $Table = Write-SqlTableData -TableName "KeyValuePairs" -SchemaName "dbo" -InputData @{ cca=10; cac='Hello'; aac=1.2 } -PassThru
PS SQLSERVER:\SQL\MyServer\MyInstance\Databases\MyDatabase\Tables> Read-SqlTableData -InputObject $Table
WARNING: Using provider context. Server = MyServer\MyInstance, Database = [MyDatabase]. 

Key Value
--- -----
aac   1.2
cac Hello
cca    10
```

The first command changes the location to be a location in the SQLSERVER provider.
The command prompt reflects the new location.
For more information, type `Get-Help about_Providers`.

The second command writes a Windows PowerShell hash table to the table named KeyValuePairs.
This command does not require the *ServerInstance* parameter because the cmdlet can get that value from the provider context.
Because this command obtains information from context, it displays a message.
To suppress this message, specify the *SuppressProviderContextWarning* parameter.

This command specifies the *Passthru* parameter.
Therefore, it returns a reference to the modified table, which is stored in the $Table variable.

The final command displays the contents of the $Table variable by using the [Read-SqlTableData](./Read-SqlTableData.md) cmdlet.

### Example 3: Import data from a file to a table
```
PS C:\> (Import-Csv -Path ".\a.csv" -Header "Id","Name","Amount") | Write-SqlTableData -ServerInstance "MyServer\MyInstance" -DatabaseName "MyDatabase" -SchemaName "dbo" -TableName "CSVTable" -Force
PS C:\> Read-SqlTableData -ServerInstance "MyServer\MyInstance" -DatabaseName "MyDatabase" -SchemaName "dbo" -TableName "CSVTable"
Id Name  Amount
-- ----  ------
10 AAAA  -1.2
11 BBBB   1.2
12 CCCC  -1.0
```

The first command imports the contents of a file by using the Import-Csv cmdlet.
The file contains the following content: 

10,AAAA,-1.2
11,BBBB,1.2
12,CCCC,-1.0

The command passes the results to the current cmdlet.
Like a previous example, the command uses parentheses to pass the results to the current cmdlet as a batch.
The command writes the data to \[MyDatabase\].\[dbo\].\[CSVTable\].
Like a previous example, if objects do not exist, specifying *Force* means that this cmdlet creates them.

The second command displays the contents of the $Table variable by using **Read-SqlTableData**.

This example runs completely from the file prompt.
It cannot use context information.
Therefore, you must specify all relevant parameters.

## PARAMETERS

### -Force
Indicates that this cmdlet creates missing SQL Server objects.
These include the database, schema, and table.
You must have appropriate credentials to create these objects.

If you do not specify this parameter for missing objects, the cmdlet returns an error.

```yaml
Type: SwitchParameter
Parameter Sets: (All)
Aliases: 

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -InputData
Specifies the data to write to the database.

Typical input data is a **System.Data.DataTable**, but you can specify **System.Data.DataSet** or **System.Data.DateRow** objects.

```yaml
Type: PSObject
Parameter Sets: (All)
Aliases: 

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -Passthru
Indicates that this cmdlet returns an **SMO.Table** object.
This object represents the table that includes the added data.
You can operate on the table after the write operation.

```yaml
Type: SwitchParameter
Parameter Sets: (All)
Aliases: 

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Timeout
Specifies a time-out value, in seconds, for the write operation.
If you do not specify a value, the cmdlet uses a default value.

```yaml
Type: Int32
Parameter Sets: (All)
Aliases: 

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Path
Specifies the full path in the context of the SQL Provider of the table where this cmdlet writes data.

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

### -DatabaseName
Specifies the name of the database that contains the table.

The cmdlet supports quoting the value.
You do not have to quote or escape special characters.

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


If you run this cmdlet in the context of a database or a child item of a database, the cmdlet ignores this parameter value.
Specify the *IgnoreProviderContext* parameter for the cmdlet to use the value of the *SchemaName* parameter anyway.

The cmdlet supports quoting the value.
You do not have to quote or escape special characters.

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

### -TableName
Specifies the name of the table from which this cmdlet reads.

If you run this cmdlet in the context of a database or a child item of a database, the cmdlet ignores this parameter value.
Specify the *IgnoreProviderContext* parameter for the cmdlet to use the value of the *TableName* parameter anyway.

The cmdlet supports quoting the value.
You do not have to quote or escape special characters.

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
Indicates that this cmdlet does not use the current context to override the values of the *ServerInstance*, *DatabaseName*, *SchemaName*, and *TableName* parameters.
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
Specifies an array of SQL Server Management Objects (SMO) objects that represent the table to which this cmdlet writes.

```yaml
Type: Table[]
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

[Read-SqlTableData](xref:sqlserver/vlatest/Read-SqlTableData.md)
