---
external help file: Microsoft.SqlServer.Management.PSSnapins.dll-Help.xml
online version: 
schema: 2.0.0
ms.assetid: EBC4CDAF-03BD-477F-BD5C-DA965727620E
updated_at: 12/8/2016 7:20 PM
ms.date: 12/8/2016
content_git_url: https://github.com/MicrosoftDocs/sql-docs-powershell/blob/master/sqlserver-cmdlets/sqlps/vlatest/Remove-SqlAvailabilityGroup.md
original_content_git_url: https://github.com/MicrosoftDocs/sql-docs-powershell/blob/master/sqlserver-cmdlets/sqlps/vlatest/Remove-SqlAvailabilityGroup.md
gitcommit: https://github.com/MicrosoftDocs/sql-docs-powershell/blob/b925b18b49186ab91cfeb5201e061d569d0eeae2/sqlserver-cmdlets/sqlps/vlatest/Remove-SqlAvailabilityGroup.md
ms.topic: reference
author: stevestein
ms.author: sstein
keywords: powershell, cmdlet
manager: jhubbard
open_to_public_contributors: true
ms.service: sql-server
---

# Remove-SqlAvailabilityGroup

## SYNOPSIS
Removes an availability group.

## SYNTAX

### ByPath (Default)
```
Remove-SqlAvailabilityGroup [-Path] <String[]> [-Script] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### ByObject
```
Remove-SqlAvailabilityGroup [-InputObject] <AvailabilityGroup[]> [-Script] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

## DESCRIPTION
The **Remove-SqlAvailabilityGroup** cmdlet removes an availability group in AlwaysOn Availability Groups.
You can run this cmdlet on any instance of SQL Server that has AlwaysOn Availability Groups enabled on a Windows Server Failover Clustering (WSFC) node that has security credentials for the availability group.

## EXAMPLES

### Example 1: Remove an availabity group
```
PS C:\>Remove-SqlAvailabilityGroup -Path "SQLSERVER:\Sql\Server\InstanceName\AvailabilityGroups\MainAG"
```

This command removes the availability group named MainAG.
You can run this command on any server instance that hosts an availability replica for the availability group.

### Example 2: Remove all availability groups
```
PS C:\>Get-ChildItem "SQLSERVER:\Sql\Server\InstanceName\AvailabilityGroups" | Remove-SqlAvailabilityGroup
```

This command gets all availability groups that have availability replicas in the specified location in the SQLSERVER: provider.
The command passes them to the current cmdlet by using the pipeline operator.
That cmdlet deletes each availability group.

### Example 3: Create a script to remove an availability group
```
PS C:\>Remove-SqlAvailabilityGroup -Path "SQLSERVER:\Sql\Server\InstanceName\AvailabilityGroups\MainAG" -Script
```

This command creates a Transact-SQL script that removes the availability group named MainAG.
The command does not perform this action.

## PARAMETERS

### -InputObject
Specifies availability group that this cmdlet removes.

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

### -Path
Specifies the path of the availability group that this cmdlet removes.

```yaml
Type: String[]
Parameter Sets: ByPath
Aliases: 

Required: True
Position: 2
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Script
Indicates that this cmdlet returns a Transact-SQL script that performs the task that this cmdlet performs.

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

[Set-SqlAvailabilityGroup](xref:sqlps/vlatest/Set-SqlAvailabilityGroup.md)

[Switch-SqlAvailabilityGroup](xref:sqlps/vlatest/Switch-SqlAvailabilityGroup.md)

[Test-SqlAvailabilityGroup](xref:sqlps/vlatest/Test-SqlAvailabilityGroup.md)


