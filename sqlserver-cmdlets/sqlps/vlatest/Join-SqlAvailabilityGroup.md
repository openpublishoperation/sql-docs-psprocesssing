---
external help file: Microsoft.SqlServer.Management.PSSnapins.dll-Help.xml
online version: 
schema: 2.0.0
ms.assetid: 907367D4-31EB-4339-9483-672FF9F6770D
updated_at: 1/4/2017 6:38 PM
ms.date: 1/4/2017
content_git_url: https://github.com/MicrosoftDocs/sql-docs-powershell/blob/live/sqlserver-cmdlets/sqlps/vlatest/Join-SqlAvailabilityGroup.md
original_content_git_url: https://github.com/MicrosoftDocs/sql-docs-powershell/blob/live/sqlserver-cmdlets/sqlps/vlatest/Join-SqlAvailabilityGroup.md
gitcommit: https://github.com/MicrosoftDocs/sql-docs-powershell/blob/4c48bd1c26220ff873e612527853aeeef98777da/sqlserver-cmdlets/sqlps/vlatest/Join-SqlAvailabilityGroup.md
ms.topic: reference
author: stevestein
ms.author: sstein
keywords: powershell, cmdlet
manager: jhubbard
open_to_public_contributors: true
ms.service: sql-server
---

# Join-SqlAvailabilityGroup

## SYNOPSIS
Joins the local secondary replica to an availability group.

## SYNTAX

### ByPath (Default)
```
Join-SqlAvailabilityGroup [-Name] <String> [[-Path] <String>] [-Script] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

### ByObject
```
Join-SqlAvailabilityGroup [-Name] <String> [-InputObject] <Server> [-Script] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

## DESCRIPTION
The **Join-SqlAvailabilityGroup** cmdlet joins the local secondary replica to an availability group.
Run this cmdlet on an instance of SQL Server that hosts a secondary replica that is not joined to the availability group.

## EXAMPLES

### Example 1: Join a secondary replica to an availability group
```
PS C:\> Join-SqlAvailabilityGroup -Path "SQLSERVER:\SQL\SecondaryServer\InstanceName" -Name "MainAG"
```

This command joins a secondary replica to the availability group named MainAG.
This server instance must host a secondary replica in this availability group.

### Example 2: Create a script that joins a secondary replica to an availability group
```
PS C:\> Join-SqlAvailabilityGroup -Path "SQLSERVER:\SQL\SecondaryServer\InstanceName" -Name "MainAG" -Script
```

This command creates a Transact-SQL script that joins a secondary replica to the availability group named MainAG.

## PARAMETERS

### -InputObject
Specifies the server that hosts the instance of SQL Server that hosts the secondary replica that this cmdlet joins to the availability group.

```yaml
Type: Server
Parameter Sets: ByObject
Aliases: 

Required: True
Position: 3
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -Name
Specifies the name of the availability group to which this cmdlet joins a secondary replica.

```yaml
Type: String
Parameter Sets: (All)
Aliases: 

Required: True
Position: 2
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Path
Specifies the path of the instance of SQL Server that hosts the secondary replica that this cmdlet joins to the availability group.
If you do not specify this parameter, this cmdlet uses current working location.

```yaml
Type: String
Parameter Sets: ByPath
Aliases: 

Required: False
Position: 3
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

### Microsoft.SqlServer.Management.Smo.Server
You can pass a server instance to this cmdlet.

## OUTPUTS

## NOTES
* The high availability data recovery service must be enabled on the server instance. The availability replica specified by the *Path* parameter must exist.

## RELATED LINKS

[New-SqlAvailabilityGroup](xref:sqlps/vlatest/New-SqlAvailabilityGroup.md)

[Remove-SqlAvailabilityGroup](xref:sqlps/vlatest/Remove-SqlAvailabilityGroup.md)

[Set-SqlAvailabilityGroup](xref:sqlps/vlatest/Set-SqlAvailabilityGroup.md)

[Switch-SqlAvailabilityGroup](xref:sqlps/vlatest/Switch-SqlAvailabilityGroup.md)

[Test-SqlAvailabilityGroup](xref:sqlps/vlatest/Test-SqlAvailabilityGroup.md)
