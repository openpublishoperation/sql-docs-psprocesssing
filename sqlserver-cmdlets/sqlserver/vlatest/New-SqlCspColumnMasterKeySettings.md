---
external help file: Microsoft.SqlServer.Management.PSSnapins.dll-Help.xml
online version: 
schema: 2.0.0
ms.assetid: 02869CE7-785C-43FF-8C10-0F74561AA002
updated_at: 12/8/2016 7:20 PM
ms.date: 12/8/2016
content_git_url: https://github.com/MicrosoftDocs/sql-docs-powershell/blob/master/sqlserver-cmdlets/sqlserver/vlatest/New-SqlCspColumnMasterKeySettings.md
original_content_git_url: https://github.com/MicrosoftDocs/sql-docs-powershell/blob/master/sqlserver-cmdlets/sqlserver/vlatest/New-SqlCspColumnMasterKeySettings.md
gitcommit: https://github.com/MicrosoftDocs/sql-docs-powershell/blob/b925b18b49186ab91cfeb5201e061d569d0eeae2/sqlserver-cmdlets/sqlserver/vlatest/New-SqlCspColumnMasterKeySettings.md
ms.topic: reference
author: stevestein
ms.author: sstein
keywords: powershell, cmdlet
manager: jhubbard
open_to_public_contributors: true
ms.service: sql-server
---

# New-SqlCspColumnMasterKeySettings

## SYNOPSIS
Creates a SqlColumnMasterKeySettings object describing an asymmetric key stored in a key store with a CSP supporting CAPI.

## SYNTAX

```
New-SqlCspColumnMasterKeySettings [-CspProviderName] <String> [-KeyName] <String>
 [-InformationAction <ActionPreference>] [-InformationVariable <String>] [<CommonParameters>]
```

## DESCRIPTION
The **New-SqlCspColumnMasterKeySettings** cmdlet creates a **SqlColumnMasterKeySettings** object.
The **SqlColumnMasterKeySettings** object references a key, stored in a key store using a Cryptographic Service Provider (CSP) supporting the Microsoft Crypto API (CAPI).
The **SqlColumnMasterKeySettings** object has two properties: **KeyStoreProviderName** and **KeyPath**.
This cmdlet sets the **KeyStoreProviderName** property to contain the name of the column master key store provider using CSP/CAPI, then generates and sets the value of the **KeyPath** property to referenced the specified key.

## EXAMPLES

### Example 1: Create a SqlColumnMasterKeySettings object
```
PS C:\>$CmkSettings = New-SqlCspColumnMasterKeySettings -CspProviderName "Microsoft Software Key Storage Provider" -KeyName "AlwaysEncryptedKey"
```

This command creates a **SqlColumnMasterKeySettings** object referencing a key in a key store encapsulated by a CSP provider called Microsoft Software Key Storage Provider.

## PARAMETERS

### -CspProviderName
Specifies the name of the CSP provider for the key store.

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

[SQL Server Cmdlets](xref:sqlserver/vlatest/SqlServer.md)


