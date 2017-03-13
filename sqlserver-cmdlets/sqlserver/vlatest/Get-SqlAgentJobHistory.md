---
external help file: Microsoft.SqlServer.Management.PSSnapins.dll-Help.xml
online version: 
schema: 2.0.0
ms.assetid: 54FC22A5-8B32-4D4E-A9AB-59AD04323C96
updated_at: 3/13/2017 4:14 PM
ms.date: 3/13/2017
content_git_url: https://github.com/MicrosoftDocs/sql-docs-powershell/blob/live/sqlserver-cmdlets/sqlserver/vlatest/Get-SqlAgentJobHistory.md
original_content_git_url: https://github.com/MicrosoftDocs/sql-docs-powershell/blob/live/sqlserver-cmdlets/sqlserver/vlatest/Get-SqlAgentJobHistory.md
gitcommit: https://github.com/MicrosoftDocs/sql-docs-powershell/blob/6eefe64a0ce19459190f09768267a4c79f9a6af9/sqlserver-cmdlets/sqlserver/vlatest/Get-SqlAgentJobHistory.md
ms.topic: reference
author: stevestein
ms.author: sstein
keywords: powershell, cmdlet
manager: jhubbard
open_to_public_contributors: True
ms.service: sql-server
---

# Get-SqlAgentJobHistory

## SYNOPSIS
Gets the job history present in the target instance of SQL Agent.

## SYNTAX

### ByPath (Default)
```
Get-SqlAgentJobHistory [-StartRunDate <DateTime>] [-EndRunDate <DateTime>] [-JobID <Guid>] [-JobName <String>]
 [-MinimumRetries <Int32>] [-MinimumRunDurationInSeconds <Int32>] [-OldestFirst]
 [-OutcomesType <CompletionResult>] [-SqlMessageID <Int32>] [-SqlSeverity <Int32>] [-Since <SinceType>]
 [[-Path] <String[]>] [-InformationAction <ActionPreference>] [-InformationVariable <String>]
 [<CommonParameters>]
```

### ByName
```
Get-SqlAgentJobHistory [-StartRunDate <DateTime>] [-EndRunDate <DateTime>] [-JobID <Guid>] [-JobName <String>]
 [-MinimumRetries <Int32>] [-MinimumRunDurationInSeconds <Int32>] [-OldestFirst]
 [-OutcomesType <CompletionResult>] [-SqlMessageID <Int32>] [-SqlSeverity <Int32>] [-Since <SinceType>]
 [[-ServerInstance] <String[]>] [-Credential <PSCredential>] [-ConnectionTimeout <Int32>]
 [-InformationAction <ActionPreference>] [-InformationVariable <String>] [<CommonParameters>]
```

### ByObject
```
Get-SqlAgentJobHistory [-StartRunDate <DateTime>] [-EndRunDate <DateTime>] [-JobID <Guid>] [-JobName <String>]
 [-MinimumRetries <Int32>] [-MinimumRunDurationInSeconds <Int32>] [-OldestFirst]
 [-OutcomesType <CompletionResult>] [-SqlMessageID <Int32>] [-SqlSeverity <Int32>] [-Since <SinceType>]
 [-InputObject] <JobServer[]> [-InformationAction <ActionPreference>] [-InformationVariable <String>]
 [<CommonParameters>]
```

## DESCRIPTION
The **Get-SqlAgentJobHistory** cmdlet gets the **JobHistory** object present in the target instance of SQL Agent.

This cmdlet supports the following modes of operation to get the **JobHistory** object:

- Specify the path of the SQL Agent instance. 
- Pass the instance of the SQL Agent in the input. 
- Invoke the cmdlet in a valid context.

## EXAMPLES

### Example 1: Get the entire job history from the specified server instance
```
PS C:\> Get-SqlAgentJobHistory -ServerInstance "MyServerInstance" | Format-Table
InstanceID SqlMessageID Message
---------- ------------ -------
        34            0 The job succeeded.  The Job was invoked by Schedule 8 (syspolicy_purge_history_schedule).  T... 
        33            0 Executed as user: DOMAIN\Machine1$. The step did not generate any output.  Process Exit
```

This command gets the entire job history in the server instance named MyServerInstance and then formats the output.

### Example 2: Get the job history from the specified server instance
```
PS C:\> Get-SqlAgentJobHistory -ServerInstance "MyServerInstance" -JobID 187112d7-84e1-4b66-b093-e97201c441ed
JobID            : 187112d7-84e1-4b66-b093-e97201c441ed
JobName          : Job_73cc6990-6386-49f9-9826-96c318ad8afa
RunStatus        : 3
```

This command gets the job history of the job object with ID 187112d7-84e1-4b66-b093-e97201c441ed in the server instance named MyServerInstance.

### Example 3: Get the job history from a time duration from the specified server instance
```
PS C:\> Get-SqlAgentJobHistory -ServerInstance "MyServerInstance" -Since Yesterday
InstanceID       : 4
SqlMessageID     : 0
Message          : The job was stopped prior to completion by User admin.  The Job was invoked by User
                  admin.  The last step to run was step 1 (JobStep_3e4cd4ba-3433-4311-a6a2-816884101504).
```

This command returns the job history since the day before in the server instance named MyServerInstance.

## PARAMETERS

### -StartRunDate
Specifies a job filter constraint that restricts the values returned to the date the job started.

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

### -EndRunDate
Specifies a job filter constraint that restricts the values returned to the date the job completed.

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

### -JobID
Specifies a job filter constraint that restricts the values returned to the job specified by the job ID value.

```yaml
Type: Guid
Parameter Sets: (All)
Aliases: 

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -JobName
Specifies a job filter constraint that restricts the values returned to the job specified by the name of the job.

```yaml
Type: String
Parameter Sets: (All)
Aliases: 

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -MinimumRetries
Specifies the job filter constraint that restricts the values returned to jobs that have failed and been retried for minimum number of times.

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

### -MinimumRunDurationInSeconds
Specifies a job filter constraint that restricts the values returned to jobs that have completed in the minimum length of time specified, in seconds.

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

### -OldestFirst
Indicates that this cmdlet lists jobs in oldest-first order.
If you do not specify this parameter, the cmdlet uses newest-first order.

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

### -OutcomesType
Specifies a job filter constraint that restricts the values returned to jobs that have the specified outcome at completion.

The acceptable values for this parameter are:

- Failed
- Succeeded
- Retry
- Cancelled
- InProgress
- Unknown

```yaml
Type: CompletionResult
Parameter Sets: (All)
Aliases: 

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -SqlMessageID
Specifies a job filter constraint that restricts the values returned to jobs that have generated the specified message during runtime.

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

### -SqlSeverity
Specifies a job filter constraint that restricts the values returned to jobs that have generated an error of the specified severity during runtime.

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

### -Since
Specifies an abbreviation that you can instead of the *StartRunDate* parameter.

It can be specified with the *EndRunDate* parameter.

You cannot use the *StartRunDate* parameter, if you use this parameter.

The acceptable values for this parameter are:

- Midnight (gets all the job history information generated after midnight) 
- Yesterday (gets all the job history information generated in the last 24 hours) 
- LastWeek (gets all the job history information generated in the last week) 
- LastMonth (gets all the job history information generated in the last month)

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

### -Path
Specifies the path to the Agent of SQL Server, as an array, on which this cmdlet runs the operation.
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
Specifies the name of an instance of SQL Server, as an array, where the SQL Agent runs.
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
Specifies a **PSCredential** object that is used to specify the credentials for a SQL Server login that has permission to perform this operation.

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
Specifies an array of SQL Server Management Object (SMO) objects that represent the SQL Server Agent being targeted.

```yaml
Type: JobServer[]
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

[Get-SqlAgent](xref:sqlserver/vlatest/Get-SqlAgent.md)

[Get-SqlAgentJob](xref:sqlserver/vlatest/Get-SqlAgentJob.md)

[Get-SqlAgentJobSchedule](xref:sqlserver/vlatest/Get-SqlAgentJobSchedule.md)

[Get-SqlAgentJobStep](xref:sqlserver/vlatest/Get-SqlAgentJobStep.md)
