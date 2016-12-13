---
external help file: Microsoft.SqlServer.Management.PSSnapins.dll-Help.xml
online version: 
schema: 2.0.0
ms.assetid: 8C17C904-0782-4701-B3E6-560899F9B690
updated_at: 12/13/2016 8:09 PM
ms.date: 12/13/2016
content_git_url: https://github.com/MicrosoftDocs/sql-docs-powershell/blob/master/sqlserver-cmdlets/sqlserver-module/vlatest/Get-SqlAgentJobSchedule.md
original_content_git_url: https://github.com/MicrosoftDocs/sql-docs-powershell/blob/master/sqlserver-cmdlets/sqlserver-module/vlatest/Get-SqlAgentJobSchedule.md
gitcommit: https://github.com/MicrosoftDocs/sql-docs-powershell/blob/f97823fbeb2d71358573a8e4b5c2c322a3a5c138/sqlserver-cmdlets/sqlserver-module/vlatest/Get-SqlAgentJobSchedule.md
ms.topic: reference
author: stevestein
ms.author: sstein
keywords: powershell, cmdlet
manager: jhubbard
open_to_public_contributors: true
ms.service: sql-server
---

# Get-SqlAgentJobSchedule

## SYNOPSIS
Gets a job schedule object for each schedule that is present in the target instance of SQL Agent Job.

## SYNTAX

### ByPath (Default)
```
Get-SqlAgentJobSchedule [[-Name] <String>] [[-Path] <String>] [-InformationAction <ActionPreference>]
 [-InformationVariable <String>] [<CommonParameters>]
```

### ByObject
```
Get-SqlAgentJobSchedule [[-Name] <String>] [-InputObject] <Job> [-InformationAction <ActionPreference>]
 [-InformationVariable <String>] [<CommonParameters>]
```

## DESCRIPTION
The **Get-SqlAgentJobSchedule** cmdlet gets a SQL **JobStepSchedule** object for each step that is present in the target instance of SQL Agent Job.
If the name of the job schedule is provided, the cmdlet gets only this specific **JobSchedule** object.

This cmdlet supports the following modes of operation to get a collection of **JobSchedule** objects:

- Pass the instance of the SQL Agent Job in the input. 
- Specify the *Path* parameter of the Job instance. 
- Invoke the cmdlet in a valid context.

## EXAMPLES

### Example 1: Get all JobSchedule object instances in the specified server instance
```
PS C:\>Get-SqlAgent -ServerInstance "MyServerInstance" | Get-SqlAgentJob | Get-SqlAgentJobSchedule
Name                           Jobs  Enabled    DateCreated               ActiveStartDate           ActiveEndDate             ID
----                           ----  -------    -----------               ---------------           -------------             --
Schedule1                      1     False      6/2/2016 10:21:44 AM      6/14/2016 12:00:00 AM     12/31/9999 12:00:00 AM    10
Schedule2                      1     True       6/9/2016 4:35:25 PM       6/9/2016 12:00:00 AM      12/31/9999 12:00:00 AM    58
Schedule3                      1     True       6/9/2016 4:35:25 PM       6/9/2016 12:00:00 AM      12/31/9999 12:00:00 AM    59
```

This command gets all **JobSchedule** object instances in the Job Instances passed by pipeline.

### Example 2: Get a JobSchedule object instance in the specified server instance
```
PS C:\>Get-SqlAgentJob -ServerInstance "MyServer" | Get-SqlAgentJobSchedule -Name "Schedule1"
```

This command gets the **JobSchedule** object instance named Schedule1 from the Job instances passed by pipeline.

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
Specifies the path to the **Job** object on which this cmdlet runs the operation.
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

### -InputObject
Specifies the **Job** object of the target instance.

```yaml
Type: Job
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


