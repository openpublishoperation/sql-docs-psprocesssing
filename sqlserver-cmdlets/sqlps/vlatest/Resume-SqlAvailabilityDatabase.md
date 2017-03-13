---
external help file: Microsoft.SqlServer.Management.PSSnapins.dll-Help.xml
online version: 
schema: 2.0.0
ms.assetid: 6E725DAB-116A-4E67-B3C6-C0EA32DA878A
updated_at: 1/4/2017 6:38 PM
ms.date: 1/4/2017
content_git_url: https://github.com/MicrosoftDocs/sql-docs-powershell/blob/live/sqlserver-cmdlets/sqlps/vlatest/Resume-SqlAvailabilityDatabase.md
original_content_git_url: https://github.com/MicrosoftDocs/sql-docs-powershell/blob/live/sqlserver-cmdlets/sqlps/vlatest/Resume-SqlAvailabilityDatabase.md
gitcommit: https://github.com/MicrosoftDocs/sql-docs-powershell/blob/4c48bd1c26220ff873e612527853aeeef98777da/sqlserver-cmdlets/sqlps/vlatest/Resume-SqlAvailabilityDatabase.md
ms.topic: reference
author: stevestein
ms.author: sstein
keywords: powershell, cmdlet
manager: jhubbard
open_to_public_contributors: True
ms.service: sql-server
---

# Resume-SqlAvailabilityDatabase

## SYNOPSIS
Resumes data movement on an availability database.

## SYNTAX

### ByPath (Default)
```
Resume-SqlAvailabilityDatabase [[-Path] <String[]>] [-Script] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### ByObject
```
Resume-SqlAvailabilityDatabase [-InputObject] <AvailabilityDatabase[]> [-Script] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

## DESCRIPTION
The **Resume-SqlAvailabilityDatabase** cmdlet resumes data movement on an availability database.
If you resume synchronization for a primary database, data movement resumes on the corresponding secondary databases.
If you resume a particular secondary database, only that database is affected.

## EXAMPLES

### Example 1: Resume synchronization for a database
```
PS C:\> Resume-SqlAvailabilityDatabase -Path "SQLSERVER:\Sql\Server\Instance\AvailabilityGroups\MainAG\AvailabilityDatabases\Database16"
```

This command resumes data synchronization for the availability database named Database16 in the availability group named MainAG.

### Example 2: Resume synchronization for all databases
```
PS C:\> Get-ChildItem "SQLSERVER:\Sql\Server\Instance\AvailabilityGroups\MainAG\AvailabilityDatabases" | Resume-SqlAvailabilityDatabase
```

This command gets all the availability databases that belong to MainAG, and then passes them to the current cmdlet by using the pipeline operator.
The current cmdlet resumes synchronization for each availability database.

### Example 3: Create a script to resume a database
```
PS C:\> Resume-SqlAvailabilityDatabase -Path "SQLSERVER:\Sql\Server\Instance\AvailabilityGroups\MainAG\AvailabilityDatabases\Database16" -Script
```

This command creates a Transact-SQL script that resumes database synchronization for the availability database named Database16 in the availability group named MainAG.
The command does not perform this action.

## PARAMETERS

### -InputObject
Specifies availability database, as an **AvailabilityDatabase** object, that this cmdlet resumes.

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
Specifies the path of an availability database that cmdlet resumes.
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

[Remove-SqlAvailabilityDatabase](xref:sqlps/vlatest/Remove-SqlAvailabilityDatabase.md)

[Suspend-SqlAvailabilityDatabase](xref:sqlps/vlatest/Suspend-SqlAvailabilityDatabase.md)
