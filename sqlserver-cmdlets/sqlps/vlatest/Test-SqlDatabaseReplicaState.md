---
external help file: Microsoft.SqlServer.Management.PSSnapins.dll-Help.xml
online version: 
schema: 2.0.0
ms.assetid: CCE374F5-0640-4740-8B41-3FA2FA7678E7
updated_at: 12/8/2016 7:20 PM
ms.date: 12/8/2016
content_git_url: https://github.com/MicrosoftDocs/sql-docs-powershell/blob/master/sqlserver-cmdlets/sqlps/vlatest/Test-SqlDatabaseReplicaState.md
original_content_git_url: https://github.com/MicrosoftDocs/sql-docs-powershell/blob/master/sqlserver-cmdlets/sqlps/vlatest/Test-SqlDatabaseReplicaState.md
gitcommit: https://github.com/MicrosoftDocs/sql-docs-powershell/blob/b925b18b49186ab91cfeb5201e061d569d0eeae2/sqlserver-cmdlets/sqlps/vlatest/Test-SqlDatabaseReplicaState.md
ms.topic: reference
author: stevestein
ms.author: sstein
keywords: powershell, cmdlet
manager: jhubbard
open_to_public_contributors: true
ms.service: sql-server
---

# Test-SqlDatabaseReplicaState

## SYNOPSIS
Evaluates the health of an availability database.

## SYNTAX

### ByPath (Default)
```
Test-SqlDatabaseReplicaState [-ShowPolicyDetails] [-AllowUserPolicies] [-NoRefresh] [[-Path] <String[]>]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

### ByObject
```
Test-SqlDatabaseReplicaState [-ShowPolicyDetails] [-AllowUserPolicies] [-NoRefresh]
 [-InputObject] <DatabaseReplicaState[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

## DESCRIPTION
The **Test-SqlDatabaseReplicaState** cmdlet assesses the health of an availability database on all joined availability replicas by evaluating SQL Server policy based management (PBM) policies.
You must have CONNECT, VIEW SERVER STATE, and VIEW ANY DEFINITION permissions to execute this cmdlet.

## EXAMPLES

### Example 1: Evaluate the health of an availability database
```
PS C:\>$Path = "SQLSERVER:\Sql\Computer\Instance\AvailabilityGroups\MainAg\DatabaseReplicaStates\MainReplica.MainDatabase"
PS C:>Test-SqlDatabaseReplicaState -Path $Path
```

This command evaluates the health of the availability database named MainDatabase on the availability replica MainReplica in the availability group MainAg and outputs a brief summary.

### Example 2: Evaluate the health of all availability databases in an availability group
```
PS C:\>Get-ChildItem "SQLSERVER:\Sql\Computer\Instance\AvailabilityGroups\MainAg\DatabaseReplicaStates" | Test-SqlDatabaseReplicaState
```

This command evaluates the health of all availability databases in the MainAg availability group and outputs a brief summary for each database.

### Example 3: Evaluate the health of all availability databases in an availability group showing PBM evaluation results
```
PS C:\>Get-ChildItem "SQLSERVER:\Sql\Computer\Instance\AvailabilityGroups\MainAg\DatabaseReplicaStates" | Test-SqlDatabaseReplicaState -ShowPolicyDetails
```

This command evaluates the health of all availability databases in the MainAg availability group and outputs the evaluation results for each PBM policy that was executed.

### Example 4: Evaluate the health of all availability databases in an availability group and include user-defined policies
```
PS C:\>Get-ChildItem "SQLSERVER:\Sql\Computer\Instance\AvailabilityGroups\MainAg\DatabaseReplicaStates" | Test-SqlDatabaseReplicaState -AllowUserPolicies
```

This command evaluates the health of all availability databases in the MainAg availability group.
User-defined policies are included in this evaluation.

### Example 5: Show all availability databases in an error health state
```
PS C:\>Get-ChildItem "SQLSERVER:\Sql\Computer\Instance\AvailabilityGroups\MainAg\DatabaseReplicaStates" | Test-SqlDatabaseReplicaState | Where-Object { $_.HealthState -eq "Error" }
```

This command shows all availability databases with a health state of "Error" in the MainAg availability group.

## PARAMETERS

### -AllowUserPolicies
Indicates that this cmdlet runs user policies found in the AlwaysOn policy categories.

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

### -InputObject
Specifies an array of availability database state objects.
This cmdlet computes the health of these availability databases.

```yaml
Type: DatabaseReplicaState[]
Parameter Sets: ByObject
Aliases: 

Required: True
Position: 2
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -NoRefresh
Indicates that this cmdlet will not manually refresh the objects specified by the **Path** or **InputObject** parameters.

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
Specifies the path to one or more database replica cluster states of the availability database.
This is an optional parameter.
If not specified, the value of the current working location is used.

```yaml
Type: String[]
Parameter Sets: ByPath
Aliases: 

Required: False
Position: 2
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ShowPolicyDetails
Indicates that this cmdlet shows the result of each policy evaluation performed.
The cmdlet outputs one object per policy evaluation and the results of evaluation are available in the fields of the object.

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

### -Confirm
Prompts you for confirmation before running the cmdlet.Prompts you for confirmation before running the cmdlet.

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

### -WhatIf
Shows what would happen if the cmdlet runs.
The cmdlet is not run.Shows what would happen if the cmdlet runs.
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

### CommonParameters
This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable. For more information, see about_CommonParameters (http://go.microsoft.com/fwlink/?LinkID=113216).

## INPUTS

### Microsoft.SqlServer.Management.Smo.DatabaseReplicaState

## OUTPUTS

## NOTES

## RELATED LINKS

[Add-SqlAvailabilityDatabase](xref:sqlps/vlatest/Add-SqlAvailabilityDatabase.md)

[Remove-SqlAvailabilityDatabase](xref:sqlps/vlatest/Remove-SqlAvailabilityDatabase.md)

[Resume-SqlAvailabilityDatabase](xref:sqlps/vlatest/Resume-SqlAvailabilityDatabase.md)

[Suspend-SqlAvailabilityDatabase](xref:sqlps/vlatest/Suspend-SqlAvailabilityDatabase.md)


