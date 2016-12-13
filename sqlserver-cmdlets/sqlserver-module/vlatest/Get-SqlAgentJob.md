---
external help file: Microsoft.SqlServer.Management.PSSnapins.dll-Help.xml
online version: 
schema: 2.0.0
ms.assetid: 7A23F6EA-3CD1-4B74-9AFD-7579374BC460
updated_at: 12/13/2016 8:09 PM
ms.date: 12/13/2016
content_git_url: https://github.com/MicrosoftDocs/sql-docs-powershell/blob/master/sqlserver-cmdlets/sqlserver-module/vlatest/Get-SqlAgentJob.md
original_content_git_url: https://github.com/MicrosoftDocs/sql-docs-powershell/blob/master/sqlserver-cmdlets/sqlserver-module/vlatest/Get-SqlAgentJob.md
gitcommit: https://github.com/MicrosoftDocs/sql-docs-powershell/blob/f97823fbeb2d71358573a8e4b5c2c322a3a5c138/sqlserver-cmdlets/sqlserver-module/vlatest/Get-SqlAgentJob.md
ms.topic: reference
author: stevestein
ms.author: sstein
keywords: powershell, cmdlet
manager: jhubbard
open_to_public_contributors: true
ms.service: sql-server
---

# Get-SqlAgentJob

## SYNOPSIS
Gets a SQL Agent Job object for each job that is present in the target instance of SQL Agent.

## SYNTAX

### ByPath (Default)
```
Get-SqlAgentJob [[-Name] <String>] [[-Path] <String>] [-InformationAction <ActionPreference>]
 [-InformationVariable <String>] [<CommonParameters>]
```

### ByName
```
Get-SqlAgentJob [[-ServerInstance] <String[]>] [-Credential <PSCredential>] [-ConnectionTimeout <Int32>]
 [[-Name] <String>] [-InformationAction <ActionPreference>] [-InformationVariable <String>]
 [<CommonParameters>]
```

### ByObject
```
Get-SqlAgentJob [[-Name] <String>] [-InputObject] <JobServer> [-InformationAction <ActionPreference>]
 [-InformationVariable <String>] [<CommonParameters>]
```

## DESCRIPTION
The **Get-SqlAgentJob** cmdlet gets a SQL Agent Job object for each job that is present in the target instance of SQL Agent.
If the name of the job is provided, the cmdlet gets only this specific job object.

This cmdlet supports the following modes of operation to get a collection of Job objects:

- Specify the path of the SQL Agent instance. 
- Pass the instance of the SQL Agent in the input. 
- Invoke the cmdlet in a valid context.

## EXAMPLES

### Example 1: Get all Job instances from the specified server instance
```
PS C:\>Get-SqlAgent -ServerInstance MyServerInstance | Get-SqlAgentJob
Name                      Owner                Category                  Enabled    CurrentRunStatus     DateCreated               LastModified              JobID
----                      -----                --------                  -------    ----------------     -----------               ------------              -----
MyJob1                    Owner                [Uncategorized (Local)]   True       Idle                 6/2/2016 10:21:44 AM      6/2/2016 10:21:44 AM      841255df-06e8-43ef-b798-3... 
MyJob2                    Owner                [Uncategorized (Local)]   True       Idle                 5/31/2016 2:40:58 PM      6/1/2016 5:09:40 PM       995b296a-cd35-4505-868a-3... 
MyJob3                    Owner                [Uncategorized (Local)]   True       Idle                 5/25/2016 12:13:56 PM     5/25/2016 12:13:56 PM     01d2e61a-9a90-4f77-98f4-e...
```

This command gets all Job instances in the server instance named MyServerInstance.

### Example 2: Get a job instance by name from the specified server instance
```
PS C:\>Get-SqlAgent -ServerInstance MyServerInstance | Get-SqlAgentJob -Name MyJob1
Name                      Owner                Category                  Enabled    CurrentRunStatus     DateCreated               LastModified              JobID
----                      -----                --------                  -------    ----------------     -----------               ------------              -----
MyJob1                    Owner                [Uncategorized (Local)]   True       Idle                 6/2/2016 10:21:44 AM      6/2/2016 10:21:44 AM      841255df-06e8-43ef-b798-3...
```

This command gets the Job instance named MyJob1 in the Server Instance named MyServerInstance.

## PARAMETERS

### -Name
Specifies the name of the **Job** object that this cmdlet gets.
The name may or may not be case-sensitive, depending on the collation of the SQL Server where the SQL Agent is running.

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
Specifies, as a string array, the name of an instance of SQL Serverwhere the SQL Agent is running.
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
Specifies the number of seconds to wait for a server connection before a time-out failure.
The time-out value must be an integer Value between 0 and 65534.
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
Specifies a SQL Management Objects (SMO) object representing the SQL Server Agent being targeted.

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

[Get-SqlAgentJobHistory](xref:sqlserver-module/vlatest/Get-SqlAgentJobHistory.md)

[Get-SqlAgentJobSchedule](xref:sqlserver-module/vlatest/Get-SqlAgentJobSchedule.md)

[Get-SqlAgentJobStep](xref:sqlserver-module/vlatest/Get-SqlAgentJobStep.md)


