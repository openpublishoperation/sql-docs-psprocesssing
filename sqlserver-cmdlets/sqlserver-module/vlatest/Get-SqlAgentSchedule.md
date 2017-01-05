---
external help file: Microsoft.SqlServer.Management.PSSnapins.dll-Help.xml
online version: 
schema: 2.0.0
ms.assetid: A7B1C97E-5DF8-413E-81DB-BC7DD9C67824
updated_at: 1/5/2017 8:57 AM
ms.date: 1/5/2017
content_git_url: https://github.com/MicrosoftDocs/sql-docs-powershell/blob/live/sqlserver-cmdlets/sqlserver-module/vlatest/Get-SqlAgentSchedule.md
original_content_git_url: https://github.com/MicrosoftDocs/sql-docs-powershell/blob/live/sqlserver-cmdlets/sqlserver-module/vlatest/Get-SqlAgentSchedule.md
gitcommit: https://github.com/MicrosoftDocs/sql-docs-powershell/blob/0d97835841eb5cfbe37d096037375a2e0c3eb87c/sqlserver-cmdlets/sqlserver-module/vlatest/Get-SqlAgentSchedule.md
ms.topic: reference
author: stevestein
ms.author: sstein
keywords: powershell, cmdlet
manager: jhubbard
open_to_public_contributors: true
ms.service: sql-server
---

# Get-SqlAgentSchedule

## SYNOPSIS
Gets a SQL job schedule object for each schedule that is present in the target instance of SQL Agent.

## SYNTAX

### ByPath (Default)
```
Get-SqlAgentSchedule [[-Name] <String>] [[-Path] <String>] [-InformationAction <ActionPreference>]
 [-InformationVariable <String>] [<CommonParameters>]
```

### ByName
```
Get-SqlAgentSchedule [[-ServerInstance] <String[]>] [-Credential <PSCredential>] [-ConnectionTimeout <Int32>]
 [[-Name] <String>] [-InformationAction <ActionPreference>] [-InformationVariable <String>]
 [<CommonParameters>]
```

### ByObject
```
Get-SqlAgentSchedule [[-Name] <String>] [-InputObject] <JobServer> [-InformationAction <ActionPreference>]
 [-InformationVariable <String>] [<CommonParameters>]
```

## DESCRIPTION
The **Get-SqlAgentSchedule** cmdlet gets a SQL **JobSchedule** object for each schedule that is present in the target instance of SQL Agent.
If you provide the name of the schedule, the cmdlet only gets that specific **JobSchedule** object.

The cmdlet queries the **Microsoft.SqlServer.Management.Smo.Agent.SharedSchedules** SQL Server Management Object (SMO) object.
If you are interested in schedules associated to a specific job, use the [Get-SqlAgentJobSchedule](./Get-SqlAgentJobSchedule.md) cmdlet.

This cmdlet supports the following modes of operation to return a collection of **JobSchedule** objects:

- Specify the instance of the SQL Agent. 
- Specify the *Path* parameter of the job instance. 
- Invoke the cmdlet in a valid context.

## EXAMPLES

### Example 1: Get all job schedules on the specified server instance
```
PS C:\> Get-SqlAgentSchedule -ServerInstance MyComputer | ? { $_.JobCount -eq 0 }
Name                           Jobs  Enabled    DateCreated               ActiveStartDate           ActiveEndDate             ID
----                           ----  -------    -----------               ---------------           -------------             --
EveryDay                       0     True       4/13/2016 11:36:30 AM     4/13/2016 12:00:00 AM     12/31/9999 12:00:00 AM    3
OnceAWeek                      0     True       4/13/2016 11:36:30 AM     4/13/2016 12:00:00 AM     12/31/9999 12:00:00 AM    4
```

This command gets all the job schedules on the SQL Agent that are located on the server instance named MyComputer which have no jobs.

## PARAMETERS

### -Name
Specifies the name of the **JobSchedule** object that this cmdlet gets.

```yaml
Type: String
Parameter Sets: (All)
Aliases: 

Required: False
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Path
Specifies the path to the Agent of SQL Server on which this cmdlet runs the operation.
If you do not specify a value for this parameter, the cmdlet uses the current working location.

```yaml
Type: String
Parameter Sets: ByPath
Aliases: 

Required: False
Position: 2
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
Specifies the name of an instance of SQL Server, as an array, where the SQL Agent is running.
For default instances, only specify the computer name: MyComputer.
For named instances, use the format ComputerName\InstanceName.

```yaml
Type: String[]
Parameter Sets: ByName
Aliases: 

Required: False
Position: 2
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
Specifies the number of seconds that this cmdlet waits for a server connection before a time-out failure.
The time-out value must be an integer value between 0 and 65534.
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
Specifies the SQL Server Agent of the target instance.

```yaml
Type: JobServer
Parameter Sets: ByObject
Aliases: 

Required: True
Position: 2
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

[Get-SqlAgent](xref:sqlserver-module/vlatest/Get-SqlAgent.md)

[Get-SqlAgentJob](xref:sqlserver-module/vlatest/Get-SqlAgentJob.md)

[Get-SqlAgentJobHistory](xref:sqlserver-module/vlatest/Get-SqlAgentJobHistory.md)

[Get-SqlAgentJobStep](xref:sqlserver-module/vlatest/Get-SqlAgentJobStep.md)
