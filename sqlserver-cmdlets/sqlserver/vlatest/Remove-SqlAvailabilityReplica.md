---
external help file: Microsoft.SqlServer.Management.PSSnapins.dll-Help.xml
online version: 
schema: 2.0.0
ms.assetid: 490B8962-9DDE-4B0C-8F3E-2262282F8F73
updated_at: 3/13/2017 4:14 PM
ms.date: 3/13/2017
content_git_url: https://github.com/MicrosoftDocs/sql-docs-powershell/blob/master/sqlserver-cmdlets/sqlserver/vlatest/Remove-SqlAvailabilityReplica.md
original_content_git_url: https://github.com/MicrosoftDocs/sql-docs-powershell/blob/master/sqlserver-cmdlets/sqlserver/vlatest/Remove-SqlAvailabilityReplica.md
gitcommit: https://github.com/MicrosoftDocs/sql-docs-powershell/blob/6eefe64a0ce19459190f09768267a4c79f9a6af9/sqlserver-cmdlets/sqlserver/vlatest/Remove-SqlAvailabilityReplica.md
ms.topic: reference
author: stevestein
ms.author: sstein
keywords: powershell, cmdlet
manager: jhubbard
open_to_public_contributors: True
ms.service: sql-server
---

# Remove-SqlAvailabilityReplica

## SYNOPSIS
Removes a secondary availability replica.

## SYNTAX

### ByPath (Default)
```
Remove-SqlAvailabilityReplica [-Path] <String[]> [-Script] [-InformationAction <ActionPreference>]
 [-InformationVariable <String>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### ByObject
```
Remove-SqlAvailabilityReplica [-InputObject] <AvailabilityReplica[]> [-Script]
 [-InformationAction <ActionPreference>] [-InformationVariable <String>] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

## DESCRIPTION
The **Remove-SqlAvailabilityReplica** cmdlet removes the secondary replica that is specified by the *InputObject* or *Path* parameters.
This cmdlet must be executed at the server instance that hosts the primary replica.

## EXAMPLES

### Example 1: Remove an availability replica
```
PS C:\> Remove-SqlAvailabilityReplica -Path "SQLSERVER:\SQL\PrimaryServer\InstanceName\AvailabilityGroups\MainAg\AvailabilityReplicas\MainReplica"
```

This command removes the availability replica named MainReplica from the availability group named MainAg.
This command must be run on the server instance that hosts the primary replica of the availability group.

### Example 2: Generate a Transact-SQL script that removes an availability replica
```
PS C:\> Remove-SqlAvailabilityReplica -Path "SQLSERVER:\SQL\PrimaryServer\InstanceName\AvailabilityGroups\MainAg\AvailabilityReplicas\MainReplica" -Script
```

This command outputs the Transact-SQL script that removes the availability replica named MainReplica from the availability group named MainAg.
This command does not remove the replica.

## PARAMETERS

### -Path
Specifies the path to the availability replica.
This parameter is required.

```yaml
Type: String[]
Parameter Sets: ByPath
Aliases: 

Required: True
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Script
Indicates that this command returns a Transact-SQL script that performs the task.

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
Specifies the **AvailabilityReplica** object for the replica to remove.

```yaml
Type: AvailabilityReplica[]
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

### Microsoft.SqlServer.Management.Smo.AvailabilityReplica
Specifies the availability replica to remove.

## OUTPUTS

## NOTES

## RELATED LINKS

[New-SqlAvailabilityReplica](xref:sqlserver/vlatest/New-SqlAvailabilityReplica.md)

[Set-SqlAvailabilityReplica](xref:sqlserver/vlatest/Set-SqlAvailabilityReplica.md)

[Test-SqlAvailabilityReplica](xref:sqlserver/vlatest/Test-SqlAvailabilityReplica.md)
