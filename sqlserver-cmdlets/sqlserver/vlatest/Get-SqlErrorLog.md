---
external help file: Microsoft.SqlServer.Management.PSSnapins.dll-Help.xml
online version: 
schema: 2.0.0
ms.assetid: 94CC05EC-8323-4D77-B640-3BFBC18D7260
updated_at: 3/13/2017 4:14 PM
ms.date: 3/13/2017
content_git_url: https://github.com/MicrosoftDocs/sql-docs-powershell/blob/master/sqlserver-cmdlets/sqlserver/vlatest/Get-SqlErrorLog.md
original_content_git_url: https://github.com/MicrosoftDocs/sql-docs-powershell/blob/master/sqlserver-cmdlets/sqlserver/vlatest/Get-SqlErrorLog.md
gitcommit: https://github.com/MicrosoftDocs/sql-docs-powershell/blob/6eefe64a0ce19459190f09768267a4c79f9a6af9/sqlserver-cmdlets/sqlserver/vlatest/Get-SqlErrorLog.md
ms.topic: reference
author: stevestein
ms.author: sstein
keywords: powershell, cmdlet
manager: jhubbard
open_to_public_contributors: True
ms.service: sql-server
---

# Get-SqlErrorLog

## SYNOPSIS
Gets the SQL Server error logs.

## SYNTAX

### ByPath (Default)
```
Get-SqlErrorLog [-Timespan <TimeSpan>] [-Before <DateTime>] [-After <DateTime>] [-Since <SinceType>]
 [-Ascending] [[-Path] <String[]>] [-InformationAction <ActionPreference>] [-InformationVariable <String>]
 [<CommonParameters>]
```

### ByName
```
Get-SqlErrorLog [-Timespan <TimeSpan>] [-Before <DateTime>] [-After <DateTime>] [-Since <SinceType>]
 [-Ascending] [[-ServerInstance] <String[]>] [-Credential <PSCredential>] [-ConnectionTimeout <Int32>]
 [-InformationAction <ActionPreference>] [-InformationVariable <String>] [<CommonParameters>]
```

### ByObject
```
Get-SqlErrorLog [-Timespan <TimeSpan>] [-Before <DateTime>] [-After <DateTime>] [-Since <SinceType>]
 [-Ascending] [-InputObject] <Server[]> [-InformationAction <ActionPreference>] [-InformationVariable <String>]
 [<CommonParameters>]
```

## DESCRIPTION
The **Get-SqlErrorLog** cmdlet gets the SQL Server errors logs.

This cmdlet supports the following modes of operation to get an error log:

- Pass the instance of the SQL Server. 
- Specify the *Path* parameter of the SQL Server instance. 
- Invoke the cmdlet in a valid context.

## EXAMPLES

### Example 1: Get all logs generated in a specific time frame that have a search word
```
PS C:\> cd SQLSERVER:\SQL\MyServer\MyInstance
PS SQLSERVER:\SQL\MyServer\MyInstance> Get-SqlErrorLog -Since Yesterday  | Where-Object { $_.Text -match 'Error' } | Format-Table
Date                 Source Text                                  ArchiveNo ServerInstance
----                 ------ ----                                  --------- --------------
6/16/2016 6:04:20 PM Logon  Error: 17828, Severity: 20, State: 4.         0 MyServer\MyInstance
```

The first command changes the directory to the SQL Server instance.

The second command gets all the SQL Server logs generated in the last 24 hours and filters out the ones that do not have the word Error in the Text field.

### Example 2: Get all logs generated in a specific time frame
```
PS C:\> cd SQLSERVER:\SQL\MyServer\MyInstance
PS SQLSERVER:\SQL\MyServer\MyInstance> Get-SqlErrorLog -Timespan '05:30:00' | Format-Table
Date                  Source  Text
----                  ------  ----
6/17/2016 12:00:00 AM spid26s This instance of SQL Server has been using a process ID of 21520 since 6/10/2016 3:56:... 
6/16/2016 6:04:20 PM  Logon   The prelogin packet used to open the connection is structurally invalid; the connectio... 
6/16/2016 6:04:20 PM  Logon   Error: 17828, Severity: 20, State: 4.
```

The first command changes the directory to the SQL Server instance.

The second command gets all the logs generated in the past five hours and a half.

### Example 3: Get all logs generated in a specific time frame sorted ascending and grouped
```
PS C:\> cd SQLSERVER:\SQL\MyServer
PS SQLSERVER:\SQL\MyServer> ls | Get-SqlErrorLog -After '2016-05-10' -Before '2016-06-18' -Ascending | ? { $_.Text -match 'Login failed' } | Group-Object -Property ServerInstance
Count Name                      Group
----- ----                      -----
    1 MyServer                  {{ Date = 6/17/2016 2:00:04 AM, Source = Logon, Text = Login failed for user ... 
    2 MyServer\INST1            {{ Date = 6/10/2016 3:58:46 PM, Source = Logon, Text = Login failed for user
```

The first command changes the directory to the SQL Server instance.

The second command gets all the error logs generated after 2016/06/10 and before 2016/06/18 for each SQL instance named MyServer.
The command gets error logs that have text that matches Login failed.
Logs are sorted ascending and eventually grouped by the **ServerInstance** property.

## PARAMETERS

### -Timespan
Specifies a **TimeSpan** object that this cmdlet filters out of the error logs that do are outside of the time span.

The format of this parameter is d.HH:mm:ss.

This parameter is ignored if you use the *Since*, *After*, or *Before* parameters.

```yaml
Type: TimeSpan
Parameter Sets: (All)
Aliases: 

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Before
Specifies that this cmdlet only gets error logs generated before the given time.

If the *After* parameter is specified, the cmdlet defaults to now, meaning that the cmdlet gets all the error logs generated after what you specified for this parameter until the present time.

Do not specify a value for this parameter if you intend to use the *Since* or *Timespan* parameters.
The format is defined according to the rules of **.Net System.Datatime.Parse()**.

```yaml
Type: DateTime
Parameter Sets: (All)
Aliases: 

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -After
Specifies that this cmdlet only gets error logs generated after the given time.

If you specify the *Before* parameter, then this cmdlet gets all the error logs generated before the specified.

Do not specify this parameter if you intend to use the *Since* or *Timespan* parameters.

The format is defined according to the rules of **.Net System.DataTime.Parse()**.

```yaml
Type: DateTime
Parameter Sets: (All)
Aliases: 

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Since
Specifies an abbreviation for the *Timespan* parameter.

Do not specify this parameter if you intend to use the *After* or *Before* parameter.

The acceptable values for this parameter are:

- Midnight (gets all the logs generated after midnight) 
- Yesterday (gets all the logs generated in the last 24 hours). 
- LastWeek (gets all the logs generated in the last week) 
- LastMonth (gets all the logs generated in the last month)

```yaml
Type: SinceType
Parameter Sets: (All)
Aliases: 

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Ascending
Indicates that the cmdlet sorts the collection of error logs by the log date in ascending order.
If you do not specify this parameter, the cmdlet sorts the error logs in descending order.

When this cmdlet gets error logs multiple sources, the sorting is applied to all the error logs from the same source.
The logs this cmdlet get are grouped by source first and then sorted by log date.

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

### -Path
Specifies the path, as an array, to the instance of SQL Server on which this cmdlet runs the operation.
If you do not specify a value for this parameter, the cmdlet uses the current working location.

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

### -ServerInstance
Specifies the name of an instance of SQL Server, as an array.
For default instances, only specify the computer name: MyComputer.
For named instances, use the format ComputerName\InstanceName.

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
Specifies a **PSCredential** object used to specify the credentials for a SQL Server login that has permission to perform this operation.

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
Specifies the server object, as an array, of the target instance that this cmdlet get the logs from.

```yaml
Type: Server[]
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

[Set-SqlErrorLog](xref:sqlserver/vlatest/Set-SqlErrorLog.md)
