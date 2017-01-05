---
external help file: Microsoft.SqlServer.Management.PSSnapins.dll-Help.xml
online version: 
schema: 2.0.0
ms.assetid: DF2EB014-5603-437A-A475-850802937862
updated_at: 1/5/2017 8:57 AM
ms.date: 1/5/2017
content_git_url: https://github.com/MicrosoftDocs/sql-docs-powershell/blob/master/sqlserver-cmdlets/sqlserver-module/vlatest/New-SqlCertificateStoreColumnMasterKeySettings.md
original_content_git_url: https://github.com/MicrosoftDocs/sql-docs-powershell/blob/master/sqlserver-cmdlets/sqlserver-module/vlatest/New-SqlCertificateStoreColumnMasterKeySettings.md
gitcommit: https://github.com/MicrosoftDocs/sql-docs-powershell/blob/0d97835841eb5cfbe37d096037375a2e0c3eb87c/sqlserver-cmdlets/sqlserver-module/vlatest/New-SqlCertificateStoreColumnMasterKeySettings.md
ms.topic: reference
author: stevestein
ms.author: sstein
keywords: powershell, cmdlet
manager: jhubbard
open_to_public_contributors: true
ms.service: sql-server
---

# New-SqlCertificateStoreColumnMasterKeySettings

## SYNOPSIS
Creates a SqlColumnMasterKeySettings object referencing the specified certificate.

## SYNTAX

```
New-SqlCertificateStoreColumnMasterKeySettings [-CertificateStoreLocation] <String> [-Thumbprint] <String>
 [-InformationAction <ActionPreference>] [-InformationVariable <String>] [<CommonParameters>]
```

## DESCRIPTION
The **New-SqlCertificateStoreColumnMasterKeySettings** cmdlet creates a **SqlColumnMasterKeySettings** object.
The **SqlColumnMasterKeySettings** object references the specified certificate, stored in the Windows Certificate Store, which is intended to be used a column master key for the Always Encrypted feature.
The **SqlColumnMasterKeySettings** object has two properties: **KeyStoreProviderName** and **KeyPath**.
This cmdlet sets the **KeyStoreProviderName** property to contain the name of column master key store provider for the Windows Certificate Store, and then generates and sets the value of the **KeyPath** property, to reference the specified certificate.

## EXAMPLES

### Example 1: Create a SqlColumnMasterKeySettings object
```
PS C:\> $CMKSettings = New-SqlCertificateStoreColumnMasterKeySettings -CertificateStoreLocation "CurrentUser" -CertificateThumbprint "f2260f28d909d21c642a3d8e0b45a830e79a1420"
```

This command creates a **SqlColumnMasterKeySettings** object referencing a certificate in Windows Certificate Store.

## PARAMETERS

### -CertificateStoreLocation
Specifies the certificate store location, containing the certificate.
The acceptable values for this parameter are:

- CurrentUser
- LocalMachine

```yaml
Type: String
Parameter Sets: (All)
Aliases: 

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Thumbprint
Specifies the thumbprint of the certificate.

```yaml
Type: String
Parameter Sets: (All)
Aliases: 

Required: True
Position: 1
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

### SqlColumnMasterKeySettings

## NOTES

## RELATED LINKS

[SQL Server Cmdlets](xref:sqlserver-module/vlatest/SqlServer.md)
