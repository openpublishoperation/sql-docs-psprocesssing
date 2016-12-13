---
external help file: Microsoft.SqlServer.Management.PSSnapins.dll-Help.xml
online version: 
schema: 2.0.0
ms.assetid: 11191A9E-2CE9-4C98-B08A-EE92A0CFB899
updated_at: 12/13/2016 8:09 PM
ms.date: 12/13/2016
content_git_url: https://github.com/MicrosoftDocs/sql-docs-powershell/blob/master/sqlserver-cmdlets/sqlserver-module/vlatest/Get-SqlAgentJobStep.md
original_content_git_url: https://github.com/MicrosoftDocs/sql-docs-powershell/blob/master/sqlserver-cmdlets/sqlserver-module/vlatest/Get-SqlAgentJobStep.md
gitcommit: https://github.com/MicrosoftDocs/sql-docs-powershell/blob/f97823fbeb2d71358573a8e4b5c2c322a3a5c138/sqlserver-cmdlets/sqlserver-module/vlatest/Get-SqlAgentJobStep.md
ms.topic: reference
author: stevestein
ms.author: sstein
keywords: powershell, cmdlet
manager: jhubbard
open_to_public_contributors: true
ms.service: sql-server
---

# Get-SqlAgentJobStep

## SYNOPSIS
Gets a SQL JobStep object for each step that is present in the target instance of SQL Agent Job.

## SYNTAX

### ByPath (Default)
```
Get-SqlAgentJobStep [[-Name] <String>] [[-Path] <String>] [-InformationAction <ActionPreference>]
 [-InformationVariable <String>] [<CommonParameters>]
```

### ByObject
```
Get-SqlAgentJobStep [[-Name] <String>] [-InputObject] <Job> [-InformationAction <ActionPreference>]
 [-InformationVariable <String>] [<CommonParameters>]
```

## DESCRIPTION
The **Get-SqlAgentJobStep** cmdlet gets a SQL **JobStep** object for each step that is present in the target instance of SQL Agent Job.
If you provide the name of the job step, the cmdlet gets only this specific **JobStep** object.

This cmdlet supports the following modes of operation to return a collection of **JobStep** objects: 

- Pass the instance of the SQL Agent Job in the input. 
- Specify the *Path* parameter of the Job instance. 
- Invoke the cmdlet in a valid context.

## EXAMPLES

### Example 1: Get all JobStep instances in the job instances
```
PS C:\>Get-SqlAgent -ServerInstance "MyServerInstance" | Get-SqlAgentJob | Get-SqlAgentJobStep
    Name      ID         OnSuccessAction           OnFailAction              LastRunDate               LastRunDuration 
    ----      --         ---------------           ------------              -----------               --------------- 
    step1     1          QuitWithSuccess           QuitWithFailure           1/1/0001 12:00:00 AM      4.03:23:45      
    step2     2          QuitWithSuccess           QuitWithFailure           1/1/0001 12:00:00 AM      00:33:59        
    step3     3          GoToNextStep              QuitWithSuccess           1/1/0001 12:00:00 AM      00:00:11
```

This command uses the **Get-SqlAgent** cmdlet to get the server instance named MyServerInstance then passes the result using the pipeline to the **Get-SqlAgentJob** cmdlet.
The command then passes the result using the pipeline to the **Get-SqlAgentJobStep** cmdlet to get all **JobStep** instances.

### Example 2: Get a JobStep instance by name
```
PS C:\>Get-SqlAgent -ServerInstance "MyServerInstance" | Get-SqlAgentJob | Get-SqlAgentJobStep -Name "Step1"
    Name      ID         OnSuccessAction           OnFailAction              LastRunDate               LastRunDuration               
    ----      --         ---------------           ------------              -----------               ---------------               
    step1     1          QuitWithSuccess           QuitWithFailure           1/1/0001 12:00:00 AM      4.03:23:45
```

This command uses the **Get-SqlAgent** cmdlet to get the server instance named MyServerInstance then passes the result using the pipeline to the **Get-SqlAgentJob** cmdlet.
The command then passes the result using the pipeline to the **Get-SqlAgentJobStep** cmdlet to get the **JobStep** instance named Step1.

## PARAMETERS

### -Name
Specifies the name of the **JobStep** object that this cmdlet gets.

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
Specifies the path to the job object on which this cmdlet runs the operation.
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
Specifies the job object of the target instance.

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

[Get-SqlAgentJobSchedule](xref:sqlserver-module/vlatest/Get-SqlAgentJobSchedule.md)

[Get-SqlAgentSchedule](xref:sqlserver-module/vlatest/Get-SqlAgentSchedule.md)


