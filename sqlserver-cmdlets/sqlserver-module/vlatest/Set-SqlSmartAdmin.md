---
external help file: Microsoft.SqlServer.Management.PSSnapins.dll-Help.xml
online version: 
schema: 2.0.0
ms.assetid: 137482FC-6D5B-4E66-BEC1-EFA9AABC15D7
updated_at: 12/13/2016 8:09 PM
ms.date: 12/13/2016
content_git_url: https://github.com/MicrosoftDocs/sql-docs-powershell/blob/master/sqlserver-cmdlets/sqlserver-module/vlatest/Set-SqlSmartAdmin.md
original_content_git_url: https://github.com/MicrosoftDocs/sql-docs-powershell/blob/master/sqlserver-cmdlets/sqlserver-module/vlatest/Set-SqlSmartAdmin.md
gitcommit: https://github.com/MicrosoftDocs/sql-docs-powershell/blob/f97823fbeb2d71358573a8e4b5c2c322a3a5c138/sqlserver-cmdlets/sqlserver-module/vlatest/Set-SqlSmartAdmin.md
ms.topic: reference
author: stevestein
ms.author: sstein
keywords: powershell, cmdlet
manager: jhubbard
open_to_public_contributors: true
ms.service: sql-server
---

# Set-SqlSmartAdmin

## SYNOPSIS
Configures or modifies backup retention and storage settings.

## SYNTAX

### ByPath (Default)
```
Set-SqlSmartAdmin [-SqlCredential <PSObject>] [-MasterSwitch <Boolean>] [-BackupEnabled <Boolean>]
 [-BackupRetentionPeriodInDays <Int32>] [-EncryptionOption <BackupEncryptionOptions>] [-DatabaseName <String>]
 [[-Path] <String>] [-Script] [-InformationAction <ActionPreference>] [-InformationVariable <String>] [-WhatIf]
 [-Confirm] [<CommonParameters>]
```

### ByObject
```
Set-SqlSmartAdmin [-SqlCredential <PSObject>] [-MasterSwitch <Boolean>] [-BackupEnabled <Boolean>]
 [-BackupRetentionPeriodInDays <Int32>] [-EncryptionOption <BackupEncryptionOptions>] [-DatabaseName <String>]
 [-InputObject] <SmartAdmin> [-Script] [-InformationAction <ActionPreference>] [-InformationVariable <String>]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

## DESCRIPTION
The **Set-SqlSmartAdmin** cmdlet configures or modifies the *BackupEnabled*, *BackupRetentionPeriodinDays*, *MasterSwitch*, and *SqlCredential* parameter settings.
This cmdlet can be run for only instance level configurations and not for a specific database.

This cmdlet supports the following modes of operation to return the object:

- Pass a **Smo.Server** object to the *InputObject* parameter, either directly or through the pipeline. 
- Pass the path of the instance of SQL Server to the *Path* parameter

## EXAMPLES

### Example 1: Configure backup retention and storage settings
```
PS C:\>$EncryptionOption = New-SqlBackupEncryptionOption -EncryptionAlgorithm Aes128 -EncryptorType ServerCertificate -EncryptorName "MyBackupCert"
```

This command configures backup retention for storage settings that uses the encryptor named MyBackupCert and stores the result in the variable named $EncryptionOption.

## PARAMETERS

### -SqlCredential
Specifies the **SqlCredential** object that is used to authenticate to the Windows Azure storage account.

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

### -MasterSwitch
Indicates that this cmdlet pauses or restarts all services under Smart Admin including SQL Server Managed Backup to Windows Azure.

```yaml
Type: Boolean
Parameter Sets: (All)
Aliases: 

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -BackupEnabled
Indicates that this cmdlet enables SQL Server Managed Backup to Windows Azure.

```yaml
Type: Boolean
Parameter Sets: (All)
Aliases: 

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -BackupRetentionPeriodInDays
Specifies the number of days the backup files should be retained.
This determines the timeframe of the recoverability for the databases.
For instance, if you set the value for 30 days, you can recover a database to a point in time in the last 30 days.

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

### -EncryptionOption
Specifies the encryption options.

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

### -DatabaseName
Specifies the name of the database that this cmdlet modifies.

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

### -Path
Specifies the path to the instance of SQL Server.
If you do not specify a value for this parameter, the cmdlet uses the current working directory.
This is useful when you create scripts to manage multiple instances.

```yaml
Type: String
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
Specifies the Smo Smart Admin object.
You can use the Get-SqlSmartAdmin cmdlet to get this object.

```yaml
Type: SmartAdmin
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

## OUTPUTS

## NOTES

## RELATED LINKS

[Get-SqlSmartAdmin](xref:sqlserver-module/vlatest/Get-SqlSmartAdmin.md)


