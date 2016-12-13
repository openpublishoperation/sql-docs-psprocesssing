---
external help file: Microsoft.SqlServer.Management.PSSnapins.dll-Help.xml
online version: 
schema: 2.0.0
ms.assetid: CD641CBF-C521-4B02-A580-7752D7200464
updated_at: 12/13/2016 8:09 PM
ms.date: 12/13/2016
content_git_url: https://github.com/MicrosoftDocs/sql-docs-powershell/blob/master/sqlserver-cmdlets/sqlserver-module/vlatest/New-SqlColumnMasterKeySettings.md
original_content_git_url: https://github.com/MicrosoftDocs/sql-docs-powershell/blob/master/sqlserver-cmdlets/sqlserver-module/vlatest/New-SqlColumnMasterKeySettings.md
gitcommit: https://github.com/MicrosoftDocs/sql-docs-powershell/blob/f97823fbeb2d71358573a8e4b5c2c322a3a5c138/sqlserver-cmdlets/sqlserver-module/vlatest/New-SqlColumnMasterKeySettings.md
ms.topic: reference
author: stevestein
ms.author: sstein
keywords: powershell, cmdlet
manager: jhubbard
open_to_public_contributors: true
ms.service: sql-server
---

# New-SqlColumnMasterKeySettings

## SYNOPSIS
Creates a SqlColumnMasterKeySettings object.

## SYNTAX

```
New-SqlColumnMasterKeySettings [-KeyStoreProviderName] <String> [-KeyPath] <String>
 [-InformationAction <ActionPreference>] [-InformationVariable <String>] [<CommonParameters>]
```

## DESCRIPTION
The **New-SqlColumnMasterKeySettings** cmdlet creates a **SqlColumnMasterKeySettings** object, which references a key.
The **SqlColumnMasterKeySettings** object has two properties: **KeyStoreProviderName** and **KeyPath**.
Use the *KeyStoreProviderName* and *KeyPath* parameters to specify values for these properties.

## EXAMPLES

### Example 1: Create column master key settings that contain Azure Key Vault as the provider
```
PS C:\>$CmkSettings = New-SqlColumnMasterKeySettings -KeyStoreProviderName "AZURE_KEY_VAULT" -KeyPath "https://myvault.vault.azure.net:443/keys/CMK/4c05f1a41b12488f9cba2ea964b6a700"
```

This command creates a **SqlColumnMasterKeySettings** object that contains Azure Key Vault as the provider.
The command stores the result in the $CmkSettings variable.

### Example 2: Create column master key settings that contain a custom key provider
```
PS C:\>$CmkSettings = New-SqlColumnMasterKeySettings -KeyStoreProviderName "CUSTOM_PROVIDER" -KeyPath "\\SecureNetworkShare\Keys\AlwaysEncrypted.key"
```

This command creates a **SqlColumnMasterKeySettings** object that contains a custom key provider.
The command stores the result in the $CmkSettings variable.

## PARAMETERS

### -KeyStoreProviderName
Specifies the name of the key store provider.

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

### -KeyPath
Specifies the key path.

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

## NOTES

## RELATED LINKS

[Configure Always Encrypted using PowerShell](https://msdn.microsoft.com/library/mt755926.aspx)

[New-SqlCngColumnMasterKeySettings](xref:sqlserver-module/vlatest/New-SqlCngColumnMasterKeySettings.md)

[New-SqlCspColumnMasterKeySettings](xref:sqlserver-module/vlatest/New-SqlCspColumnMasterKeySettings.md)


