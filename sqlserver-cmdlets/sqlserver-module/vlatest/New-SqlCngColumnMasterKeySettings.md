---
external help file: Microsoft.SqlServer.Management.PSSnapins.dll-Help.xml
online version: 
schema: 2.0.0
ms.assetid: EB155EFC-6536-4A28-B811-D0682C50C485
updated_at: 12/13/2016 8:09 PM
ms.date: 12/13/2016
content_git_url: https://github.com/MicrosoftDocs/sql-docs-powershell/blob/master/sqlserver-cmdlets/sqlserver-module/vlatest/New-SqlCngColumnMasterKeySettings.md
original_content_git_url: https://github.com/MicrosoftDocs/sql-docs-powershell/blob/master/sqlserver-cmdlets/sqlserver-module/vlatest/New-SqlCngColumnMasterKeySettings.md
gitcommit: https://github.com/MicrosoftDocs/sql-docs-powershell/blob/f97823fbeb2d71358573a8e4b5c2c322a3a5c138/sqlserver-cmdlets/sqlserver-module/vlatest/New-SqlCngColumnMasterKeySettings.md
ms.topic: reference
author: stevestein
ms.author: sstein
keywords: powershell, cmdlet
manager: jhubbard
open_to_public_contributors: true
ms.service: sql-server
---

# New-SqlCngColumnMasterKeySettings

## SYNOPSIS
Creates a SqlColumnMasterKeySettings object describing an asymmetric key stored in a key store supporting the CNG API.

## SYNTAX

```
New-SqlCngColumnMasterKeySettings [-CngProviderName] <String> [-KeyName] <String>
 [-InformationAction <ActionPreference>] [-InformationVariable <String>] [<CommonParameters>]
```

## DESCRIPTION
The **New-SqlCngColumnMasterKeySettings** cmdlet creates a **SqlColumnMasterKeySettings** object.
The **SqlColumnMasterKeySettings** object references a key, stored in a key store supporting the Cryptography Next Generation (CNG) API.
The **SqlColumnMasterKeySettings** object has two properties: **KeyStoreProviderName** and **KeyPath**.
This cmdlet sets the **KeyStoreProviderName** property to contain the name of the column master key store provider for CNG, then generates and sets the value of the **KeyPath** property to reference the specified key.

## EXAMPLES

### Example 1: Create a SqlColumnMasterKeySettings object
```
PS C:\>$CMKSettings = New-SqlCngColumnMasterKeySettings -CngProviderName "Microsoft Software Key Storage Provider" -KeyName "AlwaysEncryptedKey"
```

This command creates a **SqlColumnMasterKeySettings** object referencing a key in a key store encapsulated by a CNG provider named Microsoft Software Key Storage Provider.
The command then stores the result of the operation in the variable named $CMKSettings.

## PARAMETERS

### -CngProviderName
Specifies the name of the CNG provider for the key store.

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

### -KeyName
Specifies the name of the key in the key store.

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

[Configure Always Encrypted using PowerShell](https://msdn.microsoft.com/library/mt755926.aspx)

[SQL Server Cmdlets](xref:sqlserver-module/vlatest/SqlServer.md)


