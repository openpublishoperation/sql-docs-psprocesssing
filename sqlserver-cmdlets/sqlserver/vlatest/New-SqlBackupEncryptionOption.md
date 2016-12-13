---
external help file: Microsoft.SqlServer.Management.PSSnapins.dll-Help.xml
online version: 
schema: 2.0.0
ms.assetid: 59D942A5-9998-42D6-ABF0-9CE8C55FEFEA
updated_at: 12/8/2016 7:20 PM
ms.date: 12/8/2016
content_git_url: https://github.com/MicrosoftDocs/sql-docs-powershell/blob/master/sqlserver-cmdlets/sqlserver/vlatest/New-SqlBackupEncryptionOption.md
original_content_git_url: https://github.com/MicrosoftDocs/sql-docs-powershell/blob/master/sqlserver-cmdlets/sqlserver/vlatest/New-SqlBackupEncryptionOption.md
gitcommit: https://github.com/MicrosoftDocs/sql-docs-powershell/blob/b925b18b49186ab91cfeb5201e061d569d0eeae2/sqlserver-cmdlets/sqlserver/vlatest/New-SqlBackupEncryptionOption.md
ms.topic: reference
author: stevestein
ms.author: sstein
keywords: powershell, cmdlet
manager: jhubbard
open_to_public_contributors: true
ms.service: sql-server
---

# New-SqlBackupEncryptionOption

## SYNOPSIS
Creates the encryption options for the Backup-SqlDatabase cmdlet or the Set-SqlSmartAdmin cmdlet.

## SYNTAX

```
New-SqlBackupEncryptionOption [-NoEncryption] [-Algorithm <BackupEncryptionAlgorithm>]
 [-EncryptorType <BackupEncryptorType>] [-EncryptorName <String>] [-InformationAction <ActionPreference>]
 [-InformationVariable <String>] [<CommonParameters>]
```

## DESCRIPTION
The **New-SqlBackupEncryptionOption** cmdlet creates the encryption options for the Backup-SqlDatabase cmdlet or the Set-SqlSmartAdmin cmdlet.

## EXAMPLES

### Example 1: Create encryption options
```
PS C:\>$EncryptionOption = New-SqlBackupEncryptionOption -Algorithm Aes256 -EncryptorType ServerCertificate -EncryptorName "BackupCert"
```

This command creates the encryption options and stores the result in the variable named $EncrytionOption.

## PARAMETERS

### -NoEncryption
Indicates that this cmdlet disables encryption.
This parameter cannot be used with any other parameters.

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

### -Algorithm
Specifies the encryption algorithm.
The acceptable values for this parameter are:

- AES128
- AES192
- AES256
- TripleDes

```yaml
Type: BackupEncryptionAlgorithm
Parameter Sets: (All)
Aliases: 

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -EncryptorType
Specifies the encryptor type.
The acceptable values for this parameter are:

- ServerCertificate
- ServerAsymmetricKey

```yaml
Type: BackupEncryptorType
Parameter Sets: (All)
Aliases: 

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -EncryptorName
Specifies the name of the server certificate or server asymmetric key.

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

### CommonParameters
This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable. For more information, see about_CommonParameters (http://go.microsoft.com/fwlink/?LinkID=113216).

## INPUTS

## OUTPUTS

### Microsoft.SqlServer.Management.Smo.BackupEncryptionOptions
This cmdlet is used as input to the *EncryptionOption* parameter for the **Backup-SqlDatabase** and **Set-SqlSmartAdmin** cmdlets.

## NOTES

## RELATED LINKS

[Backup-SqlDatabase](xref:sqlserver/vlatest/Backup-SqlDatabase.md)

[Set-SqlSmartAdmin](xref:sqlserver/vlatest/Set-SqlSmartAdmin.md)


