---
external help file: Microsoft.SqlServer.Management.PSSnapins.dll-Help.xml
online version: 
schema: 2.0.0
ms.assetid: 78B8E67A-EA21-485D-A3C5-D03548A9961F
updated_at: 1/4/2017 6:38 PM
ms.date: 1/4/2017
content_git_url: https://github.com/MicrosoftDocs/sql-docs-powershell/blob/master/sqlserver-cmdlets/sqlps/vlatest/Remove-SqlAvailabilityDatabase.md
original_content_git_url: https://github.com/MicrosoftDocs/sql-docs-powershell/blob/master/sqlserver-cmdlets/sqlps/vlatest/Remove-SqlAvailabilityDatabase.md
gitcommit: https://github.com/MicrosoftDocs/sql-docs-powershell/blob/4c48bd1c26220ff873e612527853aeeef98777da/sqlserver-cmdlets/sqlps/vlatest/Remove-SqlAvailabilityDatabase.md
ms.topic: reference
author: stevestein
ms.author: sstein
keywords: powershell, cmdlet
manager: jhubbard
open_to_public_contributors: true
ms.service: sql-server
---

# Remove-SqlAvailabilityDatabase

## SYNOPSIS
Removes an availability database from its availability group.

## SYNTAX

### ByPath (Default)
```
Remove-SqlAvailabilityDatabase [-Path] <String[]> [-Script] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### ByObject
```
Remove-SqlAvailabilityDatabase [-InputObject] <AvailabilityDatabase[]> [-Script] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

## DESCRIPTION
The **Remove-SqlAvailabilityDatabase** cmdlet removes availability database from its availability group.
The *InputObject* or *Path* parameter specifies the availability database.

If you run this cmdlet at the server instance that hosts the primary replica, the cmdlet removes the primary database and all corresponding secondary databases from the availability group.

If you run this cmdlet at a server instance that hosts a secondary replica, the cmdlet removes only the local secondary database from the availability group.
The secondary database is no longer joined to the availability group, but other copies of the database continue to be joined.

## EXAMPLES

### Example 1: Remove a database from an availability group
```
PS C:\> Remove-SqlAvailabilityDatabase -Path "SQLSERVER:\Sql\PrimaryServer\InstanceName\AvailabilityGroups\MainAG\AvailabilityDatabases\Database16"
```

This command removes the availability database named Database16 from the availability group named MainAG.
This command runs on the server instance that hosts the primary replica.
Therefore, it removes the primary database and all its corresponding secondary databases from the availability group.
Data synchronization no longer occurs for this database on any secondary replica.

### Example 2: Remove all databases from an availability group
```
PS C:\> Get-ChildItem "SQLSERVER:\Sql\PrimaryServer\InstanceName\AvailabilityGroups\MainAG\AvailabilityDatabases" | Remove-SqlAvailabilityDatabase
```

This command gets all the availability databases that belong to MainAG, and then passes them to the current cmdlet by using the pipeline operator.
The current cmdlet removes each availability database.

### Example 3: Remove a secondary database from an availability group
```
PS C:\> Remove-SqlAvailabilityDatabase -Path "SQLSERVER:\Sql\SecondaryServer\InstanceName\AvailabilityGroups\MainAG\AvailabilityDatabases\Database16"
```

This command removes the secondary database named Database16 from the secondary replica hosted by the server instance named SecondaryServer\Instance.
Data synchronization to the removed secondary databases stops.
This command does not affect the primary database or any other secondary databases.

To restart data synchronization on this secondary database, rejoin it to the availability group by running the [Add-SqlAvailabilityDatabase](./Add-SqlAvailabilityDatabase.md) cmdlet on the same server instance.

### Example 4: Create a script to remove a database from an availability group
```
PS C:\> Remove-SqlAvailabilityDatabase -Path "SQLSERVER:\Sql\PrimaryServer\InstanceName\AvailabilityGroups\MainAG\AvailabilityDatabases\Database16" -Script
```

This command creates a Transact-SQL script that removes the availability database named Database16 from the availability group named MainAG.
The command does not perform this action.

## PARAMETERS

### -InputObject
Specifies availability database, as an **AvailabilityDatabase** object, that this cmdlet removes.

```yaml
Type: AvailabilityDatabase[]
Parameter Sets: ByObject
Aliases: 

Required: True
Position: 2
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -Path
Specifies the path of an availability database that cmdlet removes.

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

### CommonParameters
This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable. For more information, see about_CommonParameters (http://go.microsoft.com/fwlink/?LinkID=113216).

## INPUTS

### Microsoft.SqlServer.Management.Smo.AvailabilityDatabase
You can pass an availability database to this cmdlet.

## OUTPUTS

## NOTES

## RELATED LINKS

[Add-SqlAvailabilityDatabase](xref:sqlps/vlatest/Add-SqlAvailabilityDatabase.md)

[Resume-SqlAvailabilityDatabase](xref:sqlps/vlatest/Resume-SqlAvailabilityDatabase.md)

[Suspend-SqlAvailabilityDatabase](xref:sqlps/vlatest/Suspend-SqlAvailabilityDatabase.md)
