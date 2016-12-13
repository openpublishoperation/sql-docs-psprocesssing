---
external help file: Microsoft.SqlServer.Management.PSSnapins.dll-Help.xml
online version: 
schema: 2.0.0
ms.assetid: D51BD77D-A5A2-4C37-92F4-89DE8E004E3F
updated_at: 12/8/2016 7:20 PM
ms.date: 12/8/2016
content_git_url: https://github.com/MicrosoftDocs/sql-docs-powershell/blob/master/sqlserver-cmdlets/sqlps/vlatest/Test-SqlAvailabilityGroup.md
original_content_git_url: https://github.com/MicrosoftDocs/sql-docs-powershell/blob/master/sqlserver-cmdlets/sqlps/vlatest/Test-SqlAvailabilityGroup.md
gitcommit: https://github.com/MicrosoftDocs/sql-docs-powershell/blob/b925b18b49186ab91cfeb5201e061d569d0eeae2/sqlserver-cmdlets/sqlps/vlatest/Test-SqlAvailabilityGroup.md
ms.topic: reference
author: stevestein
ms.author: sstein
keywords: powershell, cmdlet
manager: jhubbard
open_to_public_contributors: true
ms.service: sql-server
---

# Test-SqlAvailabilityGroup

## SYNOPSIS
Evaluates the health of an availability group.

## SYNTAX

### ByPath (Default)
```
Test-SqlAvailabilityGroup [-ShowPolicyDetails] [-AllowUserPolicies] [-NoRefresh] [[-Path] <String[]>] [-WhatIf]
 [-Confirm] [<CommonParameters>]
```

### ByObject
```
Test-SqlAvailabilityGroup [-ShowPolicyDetails] [-AllowUserPolicies] [-NoRefresh]
 [-InputObject] <AvailabilityGroup[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

## DESCRIPTION
The **Test-SqlAvailabilityGroup** cmdlet evaluates the health of an availability group.
This cmdlet evaluates SQL Server policy-based management policies.
To run this cmdlet, you must have CONNECT, VIEW SERVER STATE, and VIEW ANY DEFINITION user rights.

## EXAMPLES

### Example 1: Evaluate the health of an availability group
```
PS C:\>Test-SqlAvailabilityGroup -Path "SQLSERVER:\Sql\Server\InstanceName\AvailabilityGroups\MainAG"
```

This command evaluates the health of the availability group named MainAG.
The command returns a summary.

### Example 2: Evaluate the health of all availability group
```
PS C:\>Get-ChildItem "SQLSERVER:\Sql\Server\InstanceName\AvailabilityGroups" | Test-SqlAvailabilityGroup
```

This command gets all availability groups that have availability replicas in the specified location in the SQLSERVER: provider.
The command passes them to the current cmdlet by using the pipeline operator.
That cmdlet evaluates the health of each availability group.

### Example 3: Display results for each policy of an availability group
```
PS C:\>Test-SqlAvailabilityGroup -Path "SQLSERVER:\Sql\Server\InstanceName\AvailabilityGroups\MainAG" -ShowPolicyDetails
```

This command evaluates the health of the availability group named MainAG.
This command specifies the **ShowPolicyDetails** parameter.
Therefore, it displays the evaluation results for each policy-based management policy that ran.

### Example 4: Display results for user-defined policies of an availability group
```
PS C:\>Test-SqlAvailabilityGroup -Path "SQLSERVER:\Sql\Server\InstanceName\AvailabilityGroups\MainAG" -AllowUserPolicies
```

This command evaluates the health of the availability group named MainAG.
The command includes user-defined policies in this evaluation.

### Example 5: Get groups that have an error state
```
PS C:\>Get-ChildItem "SQLSERVER:\Sql\Server\InstanceName\AvailabilityGroups" | Test-SqlAvailabilityGroup | Where-Object { $_.HealthState -eq "Error" }
```

This command gets all availability groups that have availability replicas in the specified location in the SQLSERVER: provider.
The command passes them to the current cmdlet by using the pipeline operator.
That cmdlet evaluates the health of each availability group.
The command passes those results to the Where-Object cmdlet, which returns results based on the **HealthState** property.

## PARAMETERS

### -AllowUserPolicies
Indicates that this cmdlet tests user policies found in the policy categories of AlwaysOn Availability Groups.

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
Specifies an array of availability group, as **AvailabilityGroup** objects.
This cmdlet evaluates the health of the availability groups that this parameter specifies.

```yaml
Type: AvailabilityGroup[]
Parameter Sets: ByObject
Aliases: 

Required: True
Position: 2
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -NoRefresh
Indicates that will not refresh the objects specified by the **Path** or **InputObject** parameter.

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
Specifies the path of the availability group that this cmdlet evaluates.
If you do not specify this parameter, this cmdlet uses current working location.

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
Indicates that this cmdlet displays the result of each policy evaluation that it performs.
The cmdlet returns one object per policy evaluation.
Each policy object includes the results of evaluation.
This information includes whether the policy passed or not, the policy name, and policy category.

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

### Microsoft.SqlServer.Management.Smo.AvailabilityGroup

## OUTPUTS

## NOTES

## RELATED LINKS

[Join-SqlAvailabilityGroup](xref:sqlps/vlatest/Join-SqlAvailabilityGroup.md)

[New-SqlAvailabilityGroup](xref:sqlps/vlatest/New-SqlAvailabilityGroup.md)

[Remove-SqlAvailabilityGroup](xref:sqlps/vlatest/Remove-SqlAvailabilityGroup.md)

[Set-SqlAvailabilityGroup](xref:sqlps/vlatest/Set-SqlAvailabilityGroup.md)

[Switch-SqlAvailabilityGroup](xref:sqlps/vlatest/Switch-SqlAvailabilityGroup.md)


