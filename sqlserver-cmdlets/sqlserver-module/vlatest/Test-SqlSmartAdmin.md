---
external help file: Microsoft.SqlServer.Management.PSSnapins.dll-Help.xml
online version: 
schema: 2.0.0
ms.assetid: 7BFFA8FD-620D-4539-AA23-9CB8468B3B14
updated_at: 1/5/2017 8:57 AM
ms.date: 1/5/2017
content_git_url: https://github.com/MicrosoftDocs/sql-docs-powershell/blob/live/sqlserver-cmdlets/sqlserver-module/vlatest/Test-SqlSmartAdmin.md
original_content_git_url: https://github.com/MicrosoftDocs/sql-docs-powershell/blob/live/sqlserver-cmdlets/sqlserver-module/vlatest/Test-SqlSmartAdmin.md
gitcommit: https://github.com/MicrosoftDocs/sql-docs-powershell/blob/0d97835841eb5cfbe37d096037375a2e0c3eb87c/sqlserver-cmdlets/sqlserver-module/vlatest/Test-SqlSmartAdmin.md
ms.topic: reference
author: stevestein
ms.author: sstein
keywords: powershell, cmdlet
manager: jhubbard
open_to_public_contributors: true
ms.service: sql-server
---

# Test-SqlSmartAdmin

## SYNOPSIS
Tests the health of Smart Admin by evaluating SQL Server policy based management (PBM) policies.

## SYNTAX

### ByPath (Default)
```
Test-SqlSmartAdmin [-ShowPolicyDetails] [-AllowUserPolicies] [-NoRefresh] [[-Path] <String[]>]
 [-InformationAction <ActionPreference>] [-InformationVariable <String>] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

### ByObject
```
Test-SqlSmartAdmin [-ShowPolicyDetails] [-AllowUserPolicies] [-NoRefresh] [-InputObject] <SmartAdmin[]>
 [-InformationAction <ActionPreference>] [-InformationVariable <String>] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

## DESCRIPTION
The **Test-SqlSmartAdmin** cmdlet tests the health of Smart Admin for the SQL Server instance by evaluating SQL Server policy based management (PBM) policies.

This cmdlet supports the following modes of operation to return the object:

- Pass the path of the instance of SQL Server to the *Path* parameter.
- Pass a **Smo.Server** object to the *InputObject* parameter, either directly or through the pipeline.

## EXAMPLES

### Example 1: Test the status of the SQL Server Smart Admin
```
PS C:\> cd SQLSERVER:\SQL\Computer\MyInstance 
PS SQLSERVER:\SQL\Computer\MyInstance> Get-SqlSmartAdmin | Test-SqlSmartAdmin
```

The first command changes directory to the SQL instance Computer\MyInstance.

The second command tests the the health of Smart Admin by evaluating SQL Server PBM policies.

### Example 2: Evaluate the test results of the SQL Server Smart Admin
```
PS C:\> cd SQLSERVER:\SQL\Computer\MyInstance
PS SQLSERVER:\SQL\Computer\MyInstance> $PolicyResults = Get-SqlSmartAdmin | Test-SqlSmartAdmin 
PS SQLSERVER:\SQL\Computer\MyInstance> $PolicyResults.PolicyEvaluationDetails | select Name, Category, Result, Expression|f1
```

The first command changes directory to the SQL instance Computer\MyInstance.

The second command tests the status of the SQL Server Smart Admin and stores the results in the variable named $PolicyResults.

The third command evaluates the results of the SQL Server Smart Admin stored in the variable named $PolicyResults.

### Example 3: Output the status of the SQL Server Smart Admin
```
PS C:\> PS SQLSERVER:\SQL\COMPUTER\DEFAULT> (Get-SqlSmartAdmin ).EnumHealthStatus()
number_of_storage_connectivity_errors: 0 
number_of_sql_errors: 2 
number_of_invalid_credential_errors: 0 
number_of_other_errors : 0 
number_of_corrupted_or_deleted_backups: 0 
number_of_backup_loops: 2 
number_of_retention_loops: 2
```

This command outputs the status of the local SQL Server Smart Admin.

## PARAMETERS

### -ShowPolicyDetails
Indicates that this cmdlet shows the result of the policy.
The cmdlet outputs one object per policy assessment.
The output includes the results of the assessment: such as, the name of the policy, category, and health.

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

### -AllowUserPolicies
Indicates that this cmdlet runs user policies found in the Smart Admin warning and error policy categories.

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

### -NoRefresh
Indicates that this cmdlet will not manually refresh the object specified by the *Path* or *InputObject* parameters.

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
Specifies the path of the SQL Server instance,  as a string array.
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

### -WhatIf
Shows what would happen if the cmdlet runs.
The cmdlet is not run.

```yaml
Type: SwitchParameter
Parameter Sets: (All)
Aliases: wi

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -Confirm
Prompts you for confirmation before running the cmdlet.

```yaml
Type: SwitchParameter
Parameter Sets: (All)
Aliases: cf

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -InputObject
Specifies an array of **SmartAdmin** objects.
To get this object, use the **Get-SqlSmartAdmin** cmdlet.

```yaml
Type: SmartAdmin[]
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

### Microsoft.SqlServer.Management.Smo.SmartAdmin

## OUTPUTS

###  
This cmdlet outputs the results from the evaluation of the policies.

## NOTES

## RELATED LINKS

[Get-SqlSmartAdmin](xref:sqlserver-module/vlatest/Get-SqlSmartAdmin.md)

[Set-SqlSmartAdmin](xref:sqlserver-module/vlatest/Set-SqlSmartAdmin.md)
