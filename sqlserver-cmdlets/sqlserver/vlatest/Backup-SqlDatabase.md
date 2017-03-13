---
external help file: Microsoft.SqlServer.Management.PSSnapins.dll-Help.xml
online version: 
schema: 2.0.0
ms.assetid: B67946FE-25EF-4D3F-99B3-A0A64349E478
updated_at: 3/13/2017 4:14 PM
ms.date: 3/13/2017
content_git_url: https://github.com/MicrosoftDocs/sql-docs-powershell/blob/live/sqlserver-cmdlets/sqlserver/vlatest/Backup-SqlDatabase.md
original_content_git_url: https://github.com/MicrosoftDocs/sql-docs-powershell/blob/live/sqlserver-cmdlets/sqlserver/vlatest/Backup-SqlDatabase.md
gitcommit: https://github.com/MicrosoftDocs/sql-docs-powershell/blob/6eefe64a0ce19459190f09768267a4c79f9a6af9/sqlserver-cmdlets/sqlserver/vlatest/Backup-SqlDatabase.md
ms.topic: reference
author: stevestein
ms.author: sstein
keywords: powershell, cmdlet
manager: jhubbard
open_to_public_contributors: True
ms.service: sql-server
---

# Backup-SqlDatabase

## SYNOPSIS
Backs up SQL Server database objects.

## SYNTAX

### ByPath (Default)
```
Backup-SqlDatabase [-BackupContainer <String>] [-MirrorDevices <BackupDeviceList[]>]
 [-BackupAction <BackupActionType>] [-BackupSetName <String>] [-BackupSetDescription <String>]
 [-CompressionOption <BackupCompressionOptions>] [-CopyOnly] [-ExpirationDate <DateTime>] [-FormatMedia]
 [-Incremental] [-Initialize] [-LogTruncationType <BackupTruncateLogType>] [-MediaDescription <String>]
 [-RetainDays <Int32>] [-SkipTapeHeader] [-UndoFileName <String>] [-EncryptionOption <BackupEncryptionOptions>]
 [-Database] <String> [-Path <String[]>] [[-BackupFile] <String[]>] [-SqlCredential <PSObject>]
 [-BackupDevice <BackupDeviceItem[]>] [-PassThru] [-Checksum] [-ContinueAfterError] [-NoRewind] [-Restart]
 [-UnloadTapeAfter] [-NoRecovery] [-DatabaseFile <String[]>] [-DatabaseFileGroup <String[]>]
 [-BlockSize <Int32>] [-BufferCount <Int32>] [-MaxTransferSize <Int32>] [-MediaName <String>] [-Script]
 [-InformationAction <ActionPreference>] [-InformationVariable <String>] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

### ByObject
```
Backup-SqlDatabase [-BackupContainer <String>] [-MirrorDevices <BackupDeviceList[]>]
 [-BackupAction <BackupActionType>] [-BackupSetName <String>] [-BackupSetDescription <String>]
 [-CompressionOption <BackupCompressionOptions>] [-CopyOnly] [-ExpirationDate <DateTime>] [-FormatMedia]
 [-Incremental] [-Initialize] [-LogTruncationType <BackupTruncateLogType>] [-MediaDescription <String>]
 [-RetainDays <Int32>] [-SkipTapeHeader] [-UndoFileName <String>] [-EncryptionOption <BackupEncryptionOptions>]
 [-Database] <String> -InputObject <Server[]> [[-BackupFile] <String[]>] [-SqlCredential <PSObject>]
 [-BackupDevice <BackupDeviceItem[]>] [-PassThru] [-Checksum] [-ContinueAfterError] [-NoRewind] [-Restart]
 [-UnloadTapeAfter] [-NoRecovery] [-DatabaseFile <String[]>] [-DatabaseFileGroup <String[]>]
 [-BlockSize <Int32>] [-BufferCount <Int32>] [-MaxTransferSize <Int32>] [-MediaName <String>] [-Script]
 [-InformationAction <ActionPreference>] [-InformationVariable <String>] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

### ByName
```
Backup-SqlDatabase [-BackupContainer <String>] [-MirrorDevices <BackupDeviceList[]>]
 [-BackupAction <BackupActionType>] [-BackupSetName <String>] [-BackupSetDescription <String>]
 [-CompressionOption <BackupCompressionOptions>] [-CopyOnly] [-ExpirationDate <DateTime>] [-FormatMedia]
 [-Incremental] [-Initialize] [-LogTruncationType <BackupTruncateLogType>] [-MediaDescription <String>]
 [-RetainDays <Int32>] [-SkipTapeHeader] [-UndoFileName <String>] [-EncryptionOption <BackupEncryptionOptions>]
 [-Database] <String> -ServerInstance <String[]> [-Credential <PSCredential>] [-ConnectionTimeout <Int32>]
 [[-BackupFile] <String[]>] [-SqlCredential <PSObject>] [-BackupDevice <BackupDeviceItem[]>] [-PassThru]
 [-Checksum] [-ContinueAfterError] [-NoRewind] [-Restart] [-UnloadTapeAfter] [-NoRecovery]
 [-DatabaseFile <String[]>] [-DatabaseFileGroup <String[]>] [-BlockSize <Int32>] [-BufferCount <Int32>]
 [-MaxTransferSize <Int32>] [-MediaName <String>] [-Script] [-InformationAction <ActionPreference>]
 [-InformationVariable <String>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### ByBackupContainer
```
Backup-SqlDatabase [-BackupContainer <String>] [-MirrorDevices <BackupDeviceList[]>]
 [-BackupAction <BackupActionType>] [-BackupSetName <String>] [-BackupSetDescription <String>]
 [-CompressionOption <BackupCompressionOptions>] [-CopyOnly] [-ExpirationDate <DateTime>] [-FormatMedia]
 [-Incremental] [-Initialize] [-LogTruncationType <BackupTruncateLogType>] [-MediaDescription <String>]
 [-RetainDays <Int32>] [-SkipTapeHeader] [-UndoFileName <String>] [-EncryptionOption <BackupEncryptionOptions>]
 [[-BackupFile] <String[]>] [-SqlCredential <PSObject>] [-BackupDevice <BackupDeviceItem[]>] [-PassThru]
 [-Checksum] [-ContinueAfterError] [-NoRewind] [-Restart] [-UnloadTapeAfter] [-NoRecovery]
 [-DatabaseFile <String[]>] [-DatabaseFileGroup <String[]>] [-BlockSize <Int32>] [-BufferCount <Int32>]
 [-MaxTransferSize <Int32>] [-MediaName <String>] [-Script] [-InformationAction <ActionPreference>]
 [-InformationVariable <String>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### ByDBObject
```
Backup-SqlDatabase [-BackupContainer <String>] [-MirrorDevices <BackupDeviceList[]>]
 [-BackupAction <BackupActionType>] [-BackupSetName <String>] [-BackupSetDescription <String>]
 [-CompressionOption <BackupCompressionOptions>] [-CopyOnly] [-ExpirationDate <DateTime>] [-FormatMedia]
 [-Incremental] [-Initialize] [-LogTruncationType <BackupTruncateLogType>] [-MediaDescription <String>]
 [-RetainDays <Int32>] [-SkipTapeHeader] [-UndoFileName <String>] [-EncryptionOption <BackupEncryptionOptions>]
 [-DatabaseObject] <Database> [[-BackupFile] <String[]>] [-SqlCredential <PSObject>]
 [-BackupDevice <BackupDeviceItem[]>] [-PassThru] [-Checksum] [-ContinueAfterError] [-NoRewind] [-Restart]
 [-UnloadTapeAfter] [-NoRecovery] [-DatabaseFile <String[]>] [-DatabaseFileGroup <String[]>]
 [-BlockSize <Int32>] [-BufferCount <Int32>] [-MaxTransferSize <Int32>] [-MediaName <String>] [-Script]
 [-InformationAction <ActionPreference>] [-InformationVariable <String>] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

## DESCRIPTION
The **Backup-SqlDatabase** cmdlet performs backup operations on a SQL Server database.
This includes full database backups, transaction log backups, and database file backups.
This cmdlet is modeled after the **Microsoft.SqlServer.Management.Smo.Backup** class.
The parameters on this class generally correspond to properties on that **Smo** object.

To back up a database by server instance path and database name, specify the server instance path in the *Path* parameter and the database name in the *Database* parameter.

To back up a database using an **Smo.Server** object and database name, specify the **Smo.Server** object in the *InputObject* parameter, either directly or by using the pipeline operator, and the database name in the *Database* parameter.

To back up a database by server instance and database name, specify the server instance in the *ServerInstance* parameter and the database name in the *Database* parameter.

To back up a database using an **Smo.Database** object, specify the **Smo.Database** object in the *DatabaseObject* parameter, either directly or by using the pipeline operator.

By default this cmdlet performs a full database backup.
Set the type of the backup by using the *BackupAction* parameter.

By default the backup file is stored in the default server backup location under the name databasename.bak for full and/or file backups and under the name databasename.trn for log backups.
To specify a different file name, use the *BackupFile* parameter.

To specify a backup file location and use an auto-generated file name, specify the location by using the *BackupContainer* parameter.

## EXAMPLES

### Example 1: Backup a complete database
```
PS C:\> Backup-SqlDatabase -ServerInstance "Computer\Instance" -Database "MainDB"
```

This command creates a complete database backup of the database named MainDB to the default backup location of the server instance Computer\Instance.
The backup file is named MainDB.bak.

### Example 2: Backup a database based on location
```
PS C:\> Set-Location "SQLSERVER:\SQL\Computer\Instance" 
PS SQLSERVER:\SQL\Computer\Instance> Backup-SqlDatabase -Database "MainDB"
```

This command creates a complete database backup of the database MainDB to the default backup location of the server instance Computer\Instance.
The current working directory is used to determine the server instance where the backup occurs.

### Example 3: Backup the transaction log
```
PS C:\> Backup-SqlDatabase -ServerInstance "Computer\Instance" -Database "MainDB" -BackupAction Log
```

This command creates a backup of the transaction log of the database MainDB to the default backup location of the server instance Computer\Instance.
The backup file is named MainDB.trn.

### Example 4: Backup a database and prompt for credentials
```
PS C:\> Backup-SqlDatabase -ServerInstance "Computer\Instance" -Database "MainDB" -Credential (Get-Credential "sa")
```

This command creates a complete database backup of the database MainDB using the sa SQL Server login.
This command prompts you for a password to complete the authentication.

### Example 5: Backup a database to a network file share
```
PS C:\> Backup-SqlDatabase -ServerInstance "Computer\Instance" -Database "MainDB" -BackupFile "\\mainserver\databasebackup\MainDB.bak"
```

This command creates a complete database backup of the database MainDB to the file \\\\mainserver\databasebackup\MainDB.bak.

### Example 6: Backup all databases in a server instance
```
PS C:\> Get-ChildItem "SQLSERVER:\SQL\Computer\Instance\Databases" | Backup-SqlDatabase
```

This command backs up all databases on the server instance Computer\Instance to the default backup location.
The backup files are named \<database name\>.bak.

### Example 7: Backup all databases in a server instance to a network file share
```
PS C:\> Set-Location "SQLSERVER:\SQL\Computer\Instance\Databases"
PS SQLSERVER:\SQL\Computer\Instance\Databases> ForEach($database in (Get-ChildItem)) {
>>> $dbName = $database.Name
>>> Backup-SqlDatabase -Database $dbName -BackupFile "\\mainserver\databasebackup\$dbName.bak"
>>> }
```

This command creates a full backup for each database on the server instance Computer\Instance to the share \\\\mainserver\databasebackup.
The backup files are named \<database name\>.bak.

### Example 8: Backup all files in secondary file groups
```
PS C:\> Backup-SqlDatabase -ServerInstance "Computer\Instance" -Database "MainDB" -BackupAction Files -DatabaseFileGroup "FileGroupJan","FileGroupFeb"
```

This command creates a full file backup of every file in the secondary filegroups FileGroupJan and FileGroupFeb.

### Example 9: Create a differential backup
```
PS C:\> Backup-SqlDatabase -ServerInstance "Computer\Instance" -Database "MainDB" -Incremental
```

This command creates a differential backup of the database MainDB to the default backup location of the server instance Computer\Instance.
The backup file is named MainDB.bak.

### Example 10: Create a backup to a tape drive
```
PS C:\> $TapeDevice = New-Object Microsoft.Sqlserver.Management.Smo.BackupDeviceItem("\\.\tape0", "Tape")
PS C:\> Backup-SqlDatabase -ServerInstance "Computer\Instance" -Database "MainDB" -BackupDevice $TapeDevice
```

This command creates a full backup of the database MainDB to the tape device \\\\.\tape0.
To represent this device, the command constructs an instance of the **Microsoft.Sqlserver.Management.Smo.BackupDeviceItem** object.
The constructor takes two arguments, the name of the backup device and the type of the backup device.
This **BackupDeviceItem** object is passed to the *BackupDevice* parameter of the **Backup-SqlDatabase** cmdlet.

### Example 11: Backup a database to the Azure Blob Storage service
```
PS C:\> Backup-SqlDatabase -ServerInstance "Computer\Instance" -Database "MainDB" -BackupContainer "https://storageaccountname.blob.core.windows.net/containername" -SqlCredential "SQLCredentialName"
```

This command creates a full backup of the database MainDB to the Windows Azure Blob Storage service.
It uses *BackupContainer* to specify the location (URL) of the Windows Azure Blob container.
The name of the backup file is auto-generated.
The *SqlCredential* parameter is used to specify the name of the SQL Server credential that stores the authentication information.

### Example 12: Backup a database to the Azure Blob Storage service and specify the file name
```
PS C:\> Backup-SqlDatabase -ServerInstance "Computer\Instance" -Database "MainyDB" -BackupFile "https://storageaccountname.blob.core.windows.net/containername/MainDB.bak" -SqlCredential "SQLCredentialName"
```

This command creates a full backup of the database MainDB to the Windows Azure Blob Storage service.
It uses the *BackupFile* parameter to specify the location (URL) and the backup file name.
The *SqlCredential* parameter is used to specify the name of the SQL Server credential.

### Example 13: Backup all databases to the Azure Blob Storage service
```
PS C:\> Get-ChildItem "SQLSERVER:\SQL\Computer\Instance\Databases" | Backup-SqlDatabase -BackupContainer "https://storageaccountname.blob.core.windows.net/containername" -SqlCredential "SQLCredentialName"
```

This command backs up all databases on the server instance Computer\Instance to the Windows Azure Blob Storage service location by using the **BackupContainer** parameter.
The backup file names are auto generated.

### Example 14: Create an encrypted backup
```
PS C:\> $EncryptionOption = New-SqlBackupEncryptionOption -Algorithm Aes256 -EncryptorType ServerCertificate -EncryptorName "BackupCert"
PS C:\> Backup-SqlDatabase -ServerInstance "." -Database "MainDB" -BackupFile "MainDB.bak" -CompressionOption On -EncryptionOption $EncryptionOption
```

This example creates the encryption options and uses it as a parameter value in **Backup-SqlDatabase** to create an encrypted backup.

## PARAMETERS

### -BackupContainer
Specifies the folder or location where the cmdlet stores backups.
This can be a folder on a disk or URL for an Azure Blob container.
This parameter can be useful when backing up multiple databases in a given instance.
This parameter cannot be used with a *BackupDevice* parameter.
The *BackupContainer* parameter cannot be used with the *BackupFile* parameter.

The path used to specify the location should end with a forward slash (/).

```yaml
Type: String
Parameter Sets: (All)
Aliases: 

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -MirrorDevices
Specifies an array of **BackupDeviceList** objects used by the mirrored backup.

```yaml
Type: BackupDeviceList[]
Parameter Sets: (All)
Aliases: 

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -BackupAction
Specifies the type of backup operation to perform.
Valid values are: 

- Database.
Backs up all the data files in the database.
- Files.
Backs up data files specified in the *DatabaseFile* or *DatabaseFileGroup* parameters. 
- Log.
Backs up the transaction log.

```yaml
Type: BackupActionType
Parameter Sets: (All)
Aliases: 

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -BackupSetName
Specifies the name of the backup set.

```yaml
Type: String
Parameter Sets: (All)
Aliases: 

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -BackupSetDescription
Specifies the description of the backup set.
This parameter is optional.

```yaml
Type: String
Parameter Sets: (All)
Aliases: 

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -CompressionOption
Specifies the compression options for the backup operation.
Valid values are: 

- Default
- On
- Off

```yaml
Type: BackupCompressionOptions
Parameter Sets: (All)
Aliases: 

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -CopyOnly
Indicates that the backup is a copy-only backup.
A copy-only backup does not affect the normal sequence of your regularly scheduled conventional backups.

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

### -ExpirationDate
Specifies the date and time when the backup set expires and the backup data is no longer considered valid.
This can only be used for backup data stored on disk or tape devices.
Backup sets older than the expiration date are available to be overwritten by a later backup.

```yaml
Type: DateTime
Parameter Sets: (All)
Aliases: 

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -FormatMedia
Indicates that the tape is formatted as the first step of the backup operation.
This doesnot apply to a disk backup.

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

### -Incremental
Indicates that a differential backup is performed.

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

### -Initialize
Indicates that devices associated with the backup operation are initialized.
This overwrites any existing backup sets on the media and makes this backup the first backup set on the media.

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

### -LogTruncationType
Specifies the truncation behavior for log backups.
Valid values are: 

- TruncateOnly
- NoTruncate
- Truncate

The default value is Truncate.

```yaml
Type: BackupTruncateLogType
Parameter Sets: (All)
Aliases: 

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -MediaDescription
Specifies the description for the medium that contains the backup set.
This parameter is optional.

```yaml
Type: String
Parameter Sets: (All)
Aliases: 

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -RetainDays
Specifies the number of days that must elapse before a backup set can be overwritten.
This can only be used for backup data stored on disk or tape devices.

```yaml
Type: Int32
Parameter Sets: (All)
Aliases: 

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -SkipTapeHeader
Indicates that the tape header is not read.

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

### -UndoFileName
Specifies the name of the undo file used to store uncommitted transactions that are rolled back during recovery.

```yaml
Type: String
Parameter Sets: (All)
Aliases: 

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -EncryptionOption
Specifies the encryption options for the backup operation.

```yaml
Type: BackupEncryptionOptions
Parameter Sets: (All)
Aliases: 

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Database
Specifies the name of the database to back up.
This parameter cannot be used with the *DatabaseObject* parameter.
When this parameter is specified, the *Path*, *InputObject*, or *ServerInstance* parameters must also be specified.

```yaml
Type: String
Parameter Sets: ByPath, ByObject, ByName
Aliases: 

Required: True
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Path
Specifies the path to the instance of SQL Server to execute the backup operation.
This is an optional parameter.
If not specified, the value of this parameter defaults to the current working location.

```yaml
Type: String[]
Parameter Sets: ByPath
Aliases: 

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -BackupFile
Specifies the location and file name of the backup.
This is an optional parameter.
If not specified, the backups are stored in the default backup location of the server under the name databasename.bak for full and file backups, or databasename.trn for log backups.
This parameter cannot be used with the *BackupDevice* or *BackupContainer* parameters.

```yaml
Type: String[]
Parameter Sets: (All)
Aliases: 

Required: False
Position: 2
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -SqlCredential
Specifies an SQL Server credential object that stores authentication information.
If you are backing up to Blob storage service, you must specify this parameter.
The authentication information stored includes the Storage account name and the associated access key values.
Do not specify this parameter for disk or tape.

```yaml
Type: PSObject
Parameter Sets: (All)
Aliases: 

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -BackupDevice
Specifies the devices where the backups are stored.
This parameter cannot be used with the *BackupFile* parameter.
Use this parameter if you are backing up to tape.

```yaml
Type: BackupDeviceItem[]
Parameter Sets: (All)
Aliases: 

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -PassThru
Indicates that the cmdlet outputs the **Smo.Backup** object that performed the backup.

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

### -Checksum
Indicates that a checksum value is calculated during the backup operation.

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

### -ContinueAfterError
Indicates that the operation continues when a checksum error occurs.
If not set, the operation will fail after a checksum error.

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

### -NoRewind
Indicates that a tape drive is left open at the ending position when the backup completes.
When not set, the tape is rewound after the operation completes.
This does not apply to disk or URL backups.

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

### -Restart
Indicates that the cmdlet continues processing a partially completed backup operation.
If not set, the cmdlet restarts an interrupted backup operation at the beginning of the backup set.

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

### -UnloadTapeAfter
Indicates that the tape device is rewound and unloaded when the operation finishes.
If not set, no attempt is made to rewind and unload the tape medium.
This does not apply to disk or URL backups.

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

### -NoRecovery
Indicates that the tail end of the log is not backed up.
When restored, the database is in the restoring state.
When not set, the tail end of the log is backed up.
This only applies when the *BackupAction* parameter is set to Log.

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

### -DatabaseFile
Specifies one or more database files to back up.
This parameter is only used when the *BackupAction* parameter is set to Files.
When *BackupAction* is set to Files, either the *DatabaseFileGroups* or *DatabaseFiles* parameter must be specified.

```yaml
Type: String[]
Parameter Sets: (All)
Aliases: 

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -DatabaseFileGroup
Specifies the database file groups targeted by the backup operation.
This parameter is only used when **BackupAction** property is set to Files.
When the *BackupAction* parameter is set to Files, either the *DatabaseFileGroups* or *DatabaseFiles* parameter must be specified.

```yaml
Type: String[]
Parameter Sets: (All)
Aliases: 

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -BlockSize
Specifies the physical block size for the backup, in bytes.
The supported sizes are 512, 1024, 2048, 4096, 8192, 16384, 32768, and 65536 (64 KB) bytes.
The default is 65536 for tape devices and 512 for all other devices.

```yaml
Type: Int32
Parameter Sets: (All)
Aliases: 

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -BufferCount
Specifies the number of I/O buffers to use for the backup operation.
You can specify any positive integer.
If there is insufficient virtual address space in the Sqlservr.exe process for the buffers, you will receive an out of memory error.

```yaml
Type: Int32
Parameter Sets: (All)
Aliases: 

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -MaxTransferSize
Specifies the maximum number of bytes to be transferred between the backup media and the instance of SQL Server.
The possible values are multiples of 65536 bytes (64 KB), up to 4194304 bytes (4 MB).

```yaml
Type: Int32
Parameter Sets: (All)
Aliases: 

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -MediaName
Specifies the name used to identify the media set.

```yaml
Type: String
Parameter Sets: (All)
Aliases: 

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Script
Indicates that this cmdlet outputs a Transact-SQL script that performs the backup operation.

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
Specifies the server object for the backup location.

```yaml
Type: Server[]
Parameter Sets: ByObject
Aliases: 

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -ServerInstance
Specifies the name of a SQL Server instance.
This server instance becomes the target of the backup operation.

```yaml
Type: String[]
Parameter Sets: ByName
Aliases: 

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### -Credential
Specifies a **PSCredential** object that contains the credentials for a SQL Server login that has permission to perform this operation.
This is not the SQL credential object that is used to store authentication information internally by SQL Server when accessing resources outside SQL Server.

```yaml
Type: PSCredential
Parameter Sets: ByName
Aliases: 

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ConnectionTimeout
Specifies the number of seconds to wait for a server connection before a timeout failure.
The timeout value must be an integer between 0 and 65534.
If 0 is specified, connection attempts do not timeout.

```yaml
Type: Int32
Parameter Sets: ByName
Aliases: 

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -DatabaseObject
Specifies the database object for the backup operation.

```yaml
Type: Database
Parameter Sets: ByDBObject
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

### SMO.Server
Specifies an **SMO.Server** object referring to the instance of SQL Server on which the backup operation occurs.

## OUTPUTS

## NOTES

## RELATED LINKS

[Restore-SqlDatabase](xref:sqlserver/vlatest/Restore-SqlDatabase.md)
