---
external help file: Microsoft.SqlServer.Management.PSSnapins.dll-Help.xml
online version: 
schema: 2.0.0
ms.assetid: D21A8FF1-E95D-43F0-9DC6-AF6526804A50
updated_at: 12/8/2016 7:20 PM
ms.date: 12/8/2016
content_git_url: https://github.com/MicrosoftDocs/sql-docs-powershell/blob/live/sqlserver-cmdlets/sqlps/vlatest/Test-SqlAvailabilityReplica.md
original_content_git_url: https://github.com/MicrosoftDocs/sql-docs-powershell/blob/live/sqlserver-cmdlets/sqlps/vlatest/Test-SqlAvailabilityReplica.md
gitcommit: https://github.com/MicrosoftDocs/sql-docs-powershell/blob/b925b18b49186ab91cfeb5201e061d569d0eeae2/sqlserver-cmdlets/sqlps/vlatest/Test-SqlAvailabilityReplica.md
ms.topic: reference
author: stevestein
ms.author: sstein
keywords: powershell, cmdlet
manager: jhubbard
open_to_public_contributors: true
ms.service: sql-server
---

# Test-SqlAvailabilityReplica

## SYNOPSIS
Evaluates the health of availability replicas.

## SYNTAX

### ByPath (Default)
```
Test-SqlAvailabilityReplica [-ShowPolicyDetails] [-AllowUserPolicies] [-NoRefresh] [[-Path] <String[]>]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

### ByObject
```
Test-SqlAvailabilityReplica [-ShowPolicyDetails] [-AllowUserPolicies] [-NoRefresh]
 [-InputObject] <AvailabilityReplica[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

## DESCRIPTION
The **Test-SqlAvailabilityReplica** cmdlet assesses the health of availability replicas by evaluating SQL Server policy based management (PBM) policies.
You must have CONNECT, VIEW SERVER STATE, and VIEW ANY DEFINITION permissions to execute this cmdlet.

## EXAMPLES

### Example 1: Evaluate the health of an availability replica
```
PS C:\>Test-SqlAvailabilityReplica -Path "SQLSERVER:\Sql\Computer\Instance\AvailabilityGroups\MainAg\AvailabilityReplicas\MainReplica"
```

This command evaluates the health of the availability replica named MainReplica in the MainAg availability group and outputs a brief summary.

### Example 2: Evaluate the health of all availability replicas in an availability group
```
PS C:\>Get-ChildItem "SQLSERVER:\Sql\Computer\Instance\AvailabilityGroups\MainAg\AvailabilityReplicas" | Test-SqlAvailabilityReplica
```

This command evaluates the health of all availability replicas in the availability group named MainAg and outputs a brief summary for each replica.

### Example 3: Evaluate the health of an availability replica for each PBM policy
```
PS C:\>Test-SqlAvailabilityReplica -Path "SQLSERVER:\Sql\Computer\Instance\AvailabilityGroups\MainAg\AvailabilityReplicas\MainReplica" -ShowPolicyDetails
```

This command evaluates the health of the availability replica named MainReplica in the MainAg availability group and outputs the evaluation results for each PBM policy that was executed.

### Example 4: Evaluate the health of an availability replica and include user-defined policies
```
PS C:\>Test-SqlAvailabilityReplica -Path "SQLSERVER:\Sql\Computer\Instance\AvailabilityGroups\MainAg\AvailabilityReplicas\MainReplica" -AllowUserPolicies
```

This command evaluates the health of the availability replica named MainReplica in the MainAg availability group.
User-defined policies are included in this evaluation.

### Example 5: Show all availability replicas that are in an error state
```
PS C:\>Get-ChildItem "SQLSERVER:\Sql\Computer\Instance\AvailabilityGroups\MainAg\AvailabilityReplicas" | Test-SqlAvailabilityReplica | Where-Object { $_.HealthState -eq "Error" }
```

This command shows all availability replicas with a health state of "Error" in the MainAg availability group.

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
Specifies an array of availability replicas to evaluate.

```yaml
Type: AvailabilityReplica[]
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
Specifies the path to one or more availability replicas.
This parameter is optional.
If not specified, the current working location is used.

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
Indicates that the result of each policy evaluation performed by this cmdlet is shown.
The cmdlet outputs one object per policy evaluation.
This object contains fields that describe the results of the evaluation.

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

### Microsoft.SqlServer.Management.Smo.AvailabilityReplica

## OUTPUTS

## NOTES

## RELATED LINKS

[New-SqlAvailabilityReplica](xref:sqlps/vlatest/New-SqlAvailabilityReplica.md)

[Set-SqlAvailabilityReplica](xref:sqlps/vlatest/Set-SqlAvailabilityReplica.md)


