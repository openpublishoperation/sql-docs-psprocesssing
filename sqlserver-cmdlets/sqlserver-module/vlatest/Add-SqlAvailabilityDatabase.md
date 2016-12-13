---
external help file: Microsoft.SqlServer.Management.PSSnapins.dll-Help.xml
online version: 
schema: 2.0.0
ms.assetid: 78FBC553-E510-4F00-A09A-A987D1B9E5A1
updated_at: 12/13/2016 8:09 PM
ms.date: 12/13/2016
content_git_url: https://github.com/MicrosoftDocs/sql-docs-powershell/blob/master/sqlserver-cmdlets/sqlserver-module/vlatest/Add-SqlAvailabilityDatabase.md
original_content_git_url: https://github.com/MicrosoftDocs/sql-docs-powershell/blob/master/sqlserver-cmdlets/sqlserver-module/vlatest/Add-SqlAvailabilityDatabase.md
gitcommit: https://github.com/MicrosoftDocs/sql-docs-powershell/blob/f97823fbeb2d71358573a8e4b5c2c322a3a5c138/sqlserver-cmdlets/sqlserver-module/vlatest/Add-SqlAvailabilityDatabase.md
ms.topic: reference
author: stevestein
ms.author: sstein
keywords: powershell, cmdlet
manager: jhubbard
open_to_public_contributors: true
ms.service: sql-server
---

# Add-SqlAvailabilityDatabase

## SYNOPSIS
Adds primary databases to an availability group or joins secondary databases to an availability group.

## SYNTAX

### ByPath (Default)
```
Add-SqlAvailabilityDatabase -Database <String[]> [[-Path] <String[]>] [-Script]
 [-InformationAction <ActionPreference>] [-InformationVariable <String>] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

### ByObject
```
Add-SqlAvailabilityDatabase -Database <String[]> [-InputObject] <AvailabilityGroup[]> [-Script]
 [-InformationAction <ActionPreference>] [-InformationVariable <String>] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

## DESCRIPTION
The **Add-SqlAvailabilityDatabase** cmdlet adds primary databases to an availability group or joins secondary databases to an availability group.
The **InputObject** or **Path** parameter specifies the availability group.
A database can belong to only one availability group.

To add databases to an availability group, run this cmdlet on the server instance that hosts the primary replica.
Specify one or more local user databases.

To join a secondary database to the availability group, manually prepare the secondary database on the server instance that hosts the secondary replica.
Then run this cmdlet on the server instance that hosts the secondary replica.

## EXAMPLES

### Example 1: Add a database to an availability group
```
PS C:\>Add-SqlAvailabilityDatabase -Path "SQLSERVER:\SQL\PrimaryServer\InstanceName\AvailabilityGroups\MainAG" -Database "Database16"
```

This command adds the database Database16 to the availability group MainAG.
Run this command  on the primary server instance of the availability group.
This command does not prepare secondary databases for data  synchronization.

### Example 2: Join a database to an availability group
```
PS C:\>Add-SqlAvailabilityDatabase -Path "SQLSERVER:\SQL\SecondaryServer\InstanceName\AvailabilityGroups\MainAG" -Database "Database16"
```

This command joins a secondary database named Database16 to the availability group MainAG on one of the server instances that hosts a secondary replica.

### Example 3: Add a database and join a secondary database to an availability group
```
PS C:\>$DatabaseBackupFile = "\\share\backups\Database16.bak"
PS C:\>$LogBackupFile = "\\share\backups\Database16.trn"
PS C:\>$AGPrimaryPath = "SQLSERVER:\SQL\PrimaryServer\InstanceName\AvailabilityGroups\MainAG"
PS C:\>$MyAGSecondaryPath = "SQLSERVER:\SQL\SecondaryServer\InstanceName\AvailabilityGroups\MainAG"
PS C:\>Backup-SqlDatabase -Database "Database16" -BackupFile $DatabaseBackupFile -ServerInstance "PrimaryServer\InstanceName"
PS C:\>Backup-SqlDatabase -Database "Database16" -BackupFile $LogBackupFile -ServerInstance "PrimaryServer\InstanceName" -BackupAction Log
PS C:\>Restore-SqlDatabase -Database "Database16" -BackupFile $DatabaseBackupFile -ServerInstance "SecondaryServer\InstanceName" -NoRecovery
PS C:\>Restore-SqlDatabase -Database "Database16" -BackupFile $LogBackupFile -ServerInstance "SecondaryServer\InstanceName" -RestoreAction Log -NoRecovery
PS C:\>Add-SqlAvailabilityDatabase -Path $AGPrimaryPath -Database 'Database16'
PS C:\>Add-SqlAvailabilityDatabase -Path $AGSecondaryPath -Database "Database16"
```

This example prepares a secondary database from a database on the server instance that hosts the primary replica of an availability group.
It adds the database to an availability group as a primary database.
Finally, it joins the secondary database to the availability group.

The first four commands store paths in variables for use later in the example.
The commands assign values to the **$DatabaseBackupFile**, **$LogBackupFile**, **$AGPrimaryPath**, and **$AGSecondaryPath** variables.

The fifth command backs up the database named Database16 that is on the primary server to the location in **$DatabaseBackupFile**.

The sixth command backs up the log file for Database16 on the primary server to the location in **$LogBackupFile**.

The seventh command restores the database backup for Database16 on a secondary server.

The eighth command restores the log file for Database16 on a secondary server.

The ninth command adds the database to the availability group on the primary server.

The final command joins the secondary database for that replica to the availability group.
If you have more than one secondary replica, restore and join the secondary database for each of them.

### Example 4: Create a script to add a database to an availability group
```
PS C:\>Add-SqlAvailabilityDatabase -Path "SQLSERVER:\SQL\PrimaryServer\InstanceName\AvailabilityGroups\MainAG" -Database "Database16" -Script
```

This command creates a Transact-SQL script that adds the database Database16 to the availability group MainAG.

## PARAMETERS

### -Database
Specifies an array of user databases.
This cmdlet adds or joins  the databases that this parameter specifies to the availability group.
The databases that you specify must reside on the local instance of SQL Server.

```yaml
Type: String[]
Parameter Sets: (All)
Aliases: 

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### -Path
Specifies the path of an availability group to which this cmdlet adds or joins databases.
If you do not specify this parameter, this cmdlet uses current working location.

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

### -InputObject
Specifies availability group, as an **AvailabilityGroup** object, to which this cmdlet adds or joins databases.

```yaml
Type: AvailabilityGroup[]
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

### Microsoft.SqlServer.Management.Smo.AvailabilityGroup

## OUTPUTS

## NOTES

## RELATED LINKS

[Backup-SqlDatabase](xref:sqlserver-module/vlatest/Backup-SqlDatabase.md)

[Remove-SqlAvailabilityDatabase](xref:sqlserver-module/vlatest/Remove-SqlAvailabilityDatabase.md)

[Restore-SqlDatabase](xref:sqlserver-module/vlatest/Restore-SqlDatabase.md)

[Resume-SqlAvailabilityDatabase](xref:sqlserver-module/vlatest/Resume-SqlAvailabilityDatabase.md)

[Suspend-SqlAvailabilityDatabase](xref:sqlserver-module/vlatest/Suspend-SqlAvailabilityDatabase.md)


