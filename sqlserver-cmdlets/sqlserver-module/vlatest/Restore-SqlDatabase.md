---
external help file: Microsoft.SqlServer.Management.PSSnapins.dll-Help.xml
online version: 
schema: 2.0.0
ms.assetid: EE22EDC7-16C7-4E6F-8CA1-19F6F7ED8F78
updated_at: 1/5/2017 8:57 AM
ms.date: 1/5/2017
content_git_url: https://github.com/MicrosoftDocs/sql-docs-powershell/blob/master/sqlserver-cmdlets/sqlserver-module/vlatest/Restore-SqlDatabase.md
original_content_git_url: https://github.com/MicrosoftDocs/sql-docs-powershell/blob/master/sqlserver-cmdlets/sqlserver-module/vlatest/Restore-SqlDatabase.md
gitcommit: https://github.com/MicrosoftDocs/sql-docs-powershell/blob/0d97835841eb5cfbe37d096037375a2e0c3eb87c/sqlserver-cmdlets/sqlserver-module/vlatest/Restore-SqlDatabase.md
ms.topic: reference
author: stevestein
ms.author: sstein
keywords: powershell, cmdlet
manager: jhubbard
open_to_public_contributors: true
ms.service: sql-server
---

# Restore-SqlDatabase

## SYNOPSIS
Restores a database from a backup or transaction log records.

## SYNTAX

### ByPath (Default)
```
Restore-SqlDatabase [-ClearSuspectPageTable] [-KeepReplication] [-Partial] [-ReplaceDatabase] [-RestrictedUser]
 [-Offset <Int64[]>] [-RelocateFile <RelocateFile[]>] [-FileNumber <Int32>]
 [-RestoreAction <RestoreActionType>] [-StandbyFile <String>] [-StopAtMarkAfterDate <String>]
 [-StopAtMarkName <String>] [-StopBeforeMarkAfterDate <String>] [-StopBeforeMarkName <String>]
 [-ToPointInTime <String>] [-Database] <String> [-Path <String[]>] [[-BackupFile] <String[]>]
 [-SqlCredential <PSObject>] [-BackupDevice <BackupDeviceItem[]>] [-PassThru] [-Checksum] [-ContinueAfterError]
 [-NoRewind] [-Restart] [-UnloadTapeAfter] [-NoRecovery] [-DatabaseFile <String[]>]
 [-DatabaseFileGroup <String[]>] [-BlockSize <Int32>] [-BufferCount <Int32>] [-MaxTransferSize <Int32>]
 [-MediaName <String>] [-Script] [-InformationAction <ActionPreference>] [-InformationVariable <String>]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

### ByName
```
Restore-SqlDatabase [-ClearSuspectPageTable] [-KeepReplication] [-Partial] [-ReplaceDatabase] [-RestrictedUser]
 [-Offset <Int64[]>] [-RelocateFile <RelocateFile[]>] [-FileNumber <Int32>]
 [-RestoreAction <RestoreActionType>] [-StandbyFile <String>] [-StopAtMarkAfterDate <String>]
 [-StopAtMarkName <String>] [-StopBeforeMarkAfterDate <String>] [-StopBeforeMarkName <String>]
 [-ToPointInTime <String>] [-Database] <String> -ServerInstance <String[]> [-Credential <PSCredential>]
 [-ConnectionTimeout <Int32>] [[-BackupFile] <String[]>] [-SqlCredential <PSObject>]
 [-BackupDevice <BackupDeviceItem[]>] [-PassThru] [-Checksum] [-ContinueAfterError] [-NoRewind] [-Restart]
 [-UnloadTapeAfter] [-NoRecovery] [-DatabaseFile <String[]>] [-DatabaseFileGroup <String[]>]
 [-BlockSize <Int32>] [-BufferCount <Int32>] [-MaxTransferSize <Int32>] [-MediaName <String>] [-Script]
 [-InformationAction <ActionPreference>] [-InformationVariable <String>] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

### ByObject
```
Restore-SqlDatabase [-ClearSuspectPageTable] [-KeepReplication] [-Partial] [-ReplaceDatabase] [-RestrictedUser]
 [-Offset <Int64[]>] [-RelocateFile <RelocateFile[]>] [-FileNumber <Int32>]
 [-RestoreAction <RestoreActionType>] [-StandbyFile <String>] [-StopAtMarkAfterDate <String>]
 [-StopAtMarkName <String>] [-StopBeforeMarkAfterDate <String>] [-StopBeforeMarkName <String>]
 [-ToPointInTime <String>] [-Database] <String> -InputObject <Server[]> [[-BackupFile] <String[]>]
 [-SqlCredential <PSObject>] [-BackupDevice <BackupDeviceItem[]>] [-PassThru] [-Checksum] [-ContinueAfterError]
 [-NoRewind] [-Restart] [-UnloadTapeAfter] [-NoRecovery] [-DatabaseFile <String[]>]
 [-DatabaseFileGroup <String[]>] [-BlockSize <Int32>] [-BufferCount <Int32>] [-MaxTransferSize <Int32>]
 [-MediaName <String>] [-Script] [-InformationAction <ActionPreference>] [-InformationVariable <String>]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

### ByDBObject
```
Restore-SqlDatabase [-ClearSuspectPageTable] [-KeepReplication] [-Partial] [-ReplaceDatabase] [-RestrictedUser]
 [-Offset <Int64[]>] [-RelocateFile <RelocateFile[]>] [-FileNumber <Int32>]
 [-RestoreAction <RestoreActionType>] [-StandbyFile <String>] [-StopAtMarkAfterDate <String>]
 [-StopAtMarkName <String>] [-StopBeforeMarkAfterDate <String>] [-StopBeforeMarkName <String>]
 [-ToPointInTime <String>] [-DatabaseObject] <Database> [[-BackupFile] <String[]>] [-SqlCredential <PSObject>]
 [-BackupDevice <BackupDeviceItem[]>] [-PassThru] [-Checksum] [-ContinueAfterError] [-NoRewind] [-Restart]
 [-UnloadTapeAfter] [-NoRecovery] [-DatabaseFile <String[]>] [-DatabaseFileGroup <String[]>]
 [-BlockSize <Int32>] [-BufferCount <Int32>] [-MaxTransferSize <Int32>] [-MediaName <String>] [-Script]
 [-InformationAction <ActionPreference>] [-InformationVariable <String>] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

## DESCRIPTION
The **Restore-SqlDatabase** cmdlet performs restore operations on a SQL Server database.
This includes full database restores, transaction log restores, and database file restores.

This cmdlet is modeled after the **Microsoft.SqlServer.Management.Smo.Restore** class.
The parameters on this cmdlet generally correspond to properties on the **Smo.Restore** object.

## EXAMPLES

### Example 1: Restore a database from a backup file on a network share
```
PS C:\> Restore-SqlDatabase -ServerInstance "Computer\Instance" -Database "MainDB" -BackupFile "\\mainserver\databasebackup\MainDB.bak"
```

This command restores the full database MainDB from the file \\\\mainserver\databasebackup\MainDB.bak to the server instance Computer\Instance.

### Example 2: Restore a database transaction log
```
PS C:\> Restore-SqlDatabase -ServerInstance "Computer\Instance" -Database "MainDB" -BackupFile "\\mainserver\databasebackup\MainDB.trn" -RestoreAction Log
```

This command restores the transaction log for the database MainDB from the file \\\\mainserver\databasebackup\MainDB.trn to the server instance Computer\Instance.

### Example 3: Restore a database and prompt for a password
```
PS C:\> Restore-SqlDatabase -ServerInstance "Computer\Instance" -Database "MainDB" -BackupFile "\\mainserver\databasebackup\MainDB.bak" -Credential (Get-Credential "sa")
```

This command restores the full database MainDB from the file \\\\mainserver\databasebackup\MainDB.trn to the server instance Computer\Instance, using the sa SQL login.
This command will prompt you for a password to complete the authentication.

### Example 4: Restore a transaction log with the NORECOVERY option
```
PS C:\> Restore-SqlDatabase -ServerInstance "Computer\Instance" -Database "MainDB" -BackupFile "\\mainserver\databasebackup\MainDB.trn" -RestoreAction Log -NoRecovery
```

This command restores the transaction log of the database MainDB with the NORECOVERY option from the file \\\\mainserver\databasebackup\MainDB.trn to the server instance 'Computer\Instance'.

### Example 5: Restore transaction log records up to a point in time
```
PS C:\> Restore-SqlDatabase -ServerInstance "Computer\Instance" -Database "MainDB" -BackupFile "\\mainserver\databasebackup\MainDB.trn" -RestoreAction Log -ToPointInTime "Nov 11, 2011 11:11 AM"
```

This command restores the transaction log of the database MainDB up to the date passed to the **ToPointInTime** parameter, Nov 11, 2011 11:11 AM.

### Example 6: Restore a database and relocate the data and log files
```
PS C:\> $RelocateData = New-Object Microsoft.SqlServer.Management.Smo.RelocateFile("MainDB_Data", "c:\MySQLServer\MainDB.mdf")
PS C:\> $RelocateLog = New-Object Microsoft.SqlServer.Management.Smo.RelocateFile("MainDB_Log", "c:\MySQLServer\MainDB.ldf")
PS C:\> Restore-SqlDatabase -ServerInstance "Computer\Instance" -Database "MainDB" -BackupFile "\\mainserver\databasebackup\MainDB.trn" -RelocateFile @($RelocateData,$RelocateLog)
```

This example restores the full database MainDB to the server instance Computer\Instance, and relocates the data and log files.
For each file that is moved, the example constructs an instance of the **Microsoft.SqlServer.Management.Smo.RelocateFile** class.
Each constructor takes two arguments, the logical name of the file and the physical location where the file will be placed on the target server.
The **RelocateFile** objects are passed to the **RelocateFile** parameter of the **Restore-SqlDatabase** cmdlet.

### Example 7: Restore a database from tape
```
PS C:\> $TapeDevice = New-Object Microsoft.Sqlserver.Management.Smo.BackupDeviceItem("\\.\tape0", "Tape")
PS C:\> Restore-SqlDatabase -ServerInstance "Computer\Instance" -Database "MainDB" -BackupDevice $TapeDevice
```

This example restores the database MainDB from the tape device named \\\\.\tape0 to the server instance Computer\Instance.
To represent this device, the example constructs an instance of the **Microsoft.Sqlserver.Management.Smo.BackupDeviceItem** class.
The constructor takes two arguments, the name of the backup device and the type of the backup device.
This **BackupDeviceItem** object is then passed to the -**BackupDevice** parameter of the **Restore-SqlDatabase** cmdlet.

### Example 8: Restore a database from the Azure Blob Storage service
```
PS C:\> Restore-SqlDatabase -ServerInstance "Computer\Instance" -Database "MainDB" -BackupFile "https://mystorageaccountname.blob.core.windows.net/container/MyDB.bak" -SqlCredential "mySqlCredential"
```

This command restores the full database MainDB from the file on the Windows Azure Blob Storage service to the server instance Computer\Instance.

## PARAMETERS

### -ClearSuspectPageTable
Indicates that the suspect page table is deleted after the restore operation.

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

### -KeepReplication
Indicates that the replication configuration is preserved.
If not set, the replication configuration is ignored by the restore operation.

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

### -Partial
Indicates that the restore operation is a partial restore.

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

### -ReplaceDatabase
Indicates that a new image of the database is created.
This overwrites any existing database with the same name.
If not set, the restore operation will fail when a database with that name already exists on the server.

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

### -RestrictedUser
Indicates that access to the restored database is restricted to the db_owner fixed database role, and the dbcreator and sysadmin fixed server roles.

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

### -Offset
Specifies the page addresses to be restored.
This is only used when the *RestoreAction* parameter is set to OnlinePage.

```yaml
Type: Int64[]
Parameter Sets: (All)
Aliases: 

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -RelocateFile
Specifies a list of **Smo.Relocate** file objects.
Each object consists of a logical backup file name and a physical file system location.
The restore moves the restored database into the specified physical location on the target server.

```yaml
Type: RelocateFile[]
Parameter Sets: (All)
Aliases: 

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -FileNumber
Specifies the index number that is used to identify the targeted backup set on the backup medium.

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

### -RestoreAction
Specifies the type of restore operation that is performed.
Valid values are: 

- Database.
The database is restored. 
- Files.
One or more data files are restored.
The *DatabaseFile* or *DatabaseFileGroup* parameter must be specified. 
- Log.
The translaction log is restored. 
- OnlinePage.
A data page is restored online so that the database remains available to users. 
- OnlineFiles.
Data files are restored online so that the database remains available to users.
The *DatabaseFile* or *DatabaseFileGroup* parameter must be specified.

```yaml
Type: RestoreActionType
Parameter Sets: (All)
Aliases: 

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -StandbyFile
Specifies the name of an undo file that is used as part of the imaging strategy for a SQL Server instance.

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

### -StopAtMarkAfterDate
Specifies the date to be used with the mark name specified by the *StopAtMarkName* parameter to determine the stopping point of the recovery operation.

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

### -StopAtMarkName
Specifies the marked transaction at which to stop the recovery operation.
This is used with the *StopAtMarkAfterDate* parameter to determine the stopping point of the recovery operation.
The recovered data includes the transaction that contains the mark.
If the *StopAtMarkAfterDate* parameter value is not set, recovery stops at the first mark with the specified name.

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

### -StopBeforeMarkAfterDate
Specifies the date to be used with the *StopBeforeMarkName* parameter to determine the stopping point of the recovery operation.

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

### -StopBeforeMarkName
Specifies the marked transaction before which to stop the recovery operation.
This is used with the *StopBeforeMarkAfterDate* parameter to determine the stopping point of the recovery operation.

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

### -ToPointInTime
Specifies the endpoint for database log restoration.
This only applies when the *RestoreAction* parameter is set to Log.

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

### -Database
Specifies the name of the database to restore.
This cannot be used with the *DatabaseObject* parameter.
When this parameter is used, the *Path*, *InputObject*, or *ServerInstance* parameters must also be specified.

```yaml
Type: String
Parameter Sets: ByPath, ByName, ByObject
Aliases: 

Required: True
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Path
Specifies the path of the SQL Server instance on which to execute the restore operation.
This parameter is optional.
If not specified, the current working location is used.

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
Specifies the location or locations where the backup files are stored.
This parameter is optional.
If not specified, the default backup location of the server is searched for the name \<database name\>.trn for log restores, or \<database name\>.bak for all other types of restores.
This parameter cannot be used with the *BackupDevice* parameter.
If you are backing to the Windows Azure Blob Storage service (URL), this parameter or the **BackupDevice** parameter must be specified.

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
Specifies the devices where the backups are be stored.
This parameter cannot be used with the **BackupFile** parameter.
Use this parameter if you are backing up to a tape device.

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
Indicates that this cmdlet outputs the **Smo.Backup** object used to perform the restore operation.

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
Indicates that a checksum value is calculated during the restore operation.

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
Indicates that a tape drive is left open at the ending position when the restore is completed.
If not set, the tape is rewound after the operation is completed.
This does not apply to disk restores.

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
Indicates that this cmdlet resumes a partially completed restore operation.
If not set, the cmdlet restarts an interrupted restore operation at the beginning of the backup set.

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
Indicates that the tape device is rewound and unloaded when the operation is completed.
If not set, no attempt is made to rewind and unload the tape medium.
This does not apply to disk backups.

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
Indicates that the database is restored into the restoring state.
A roll back operation does not occur and additional backups can be restored.

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
Specifies the database files targeted by the restore operation.
This is only used when the **RestoreAction** parameter is set to Files.
When the **RestoreAction** parameter is set to Files, either the **DatabaseFileGroups** or **DatabaseFiles** paameter must also be specified.

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
Specifies the database file groups targeted by the restore operation.
This is only used when the **RestoreAction** parameter is set to File.
When the **RestoreAction** parameter is set to Files, either the **DatabaseFileGroups** or **DatabaseFiles** parameter must also be specified.

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
Specifies the physical block size, in bytes, for the backup.
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
Specifies the total number of I/O buffers to be used for the backup operation.
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
Specifies the maximum number of bytes to be transferred between the backup media and the SQL Server instance.
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
Specifies the name that identifies a media set.

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
Indicates that this cmdlet outputs a Transact-SQL script that performs the restore operation.

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

### -ServerInstance
Specifies the name of a SQL Server instance.
This server instance becomes the target of the restore operation.

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

### -InputObject
Specifies the server object of the SQL Server instance where the restore occurs.

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

### -DatabaseObject
Specifies a database object for the restore operation.

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

### Smo.Server
Specifies an **SMO.Server** object that describes the SQL Server instance on which the restore operation occurs.

## OUTPUTS

## NOTES

## RELATED LINKS

[Backup-SqlDatabase](xref:sqlserver-module/vlatest/Backup-SqlDatabase.md)
