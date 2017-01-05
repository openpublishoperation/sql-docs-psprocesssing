---
external help file: Microsoft.SqlServer.Management.PSSnapins.dll-Help.xml
online version: 
schema: 2.0.0
ms.assetid: 4E782D81-0B0E-49A2-8E18-C6A76F1B6C5D
updated_at: 1/5/2017 8:57 AM
ms.date: 1/5/2017
content_git_url: https://github.com/MicrosoftDocs/sql-docs-powershell/blob/master/sqlserver-cmdlets/sqlserver-module/vlatest/New-SqlAzureKeyVaultColumnMasterKeySettings.md
original_content_git_url: https://github.com/MicrosoftDocs/sql-docs-powershell/blob/master/sqlserver-cmdlets/sqlserver-module/vlatest/New-SqlAzureKeyVaultColumnMasterKeySettings.md
gitcommit: https://github.com/MicrosoftDocs/sql-docs-powershell/blob/0d97835841eb5cfbe37d096037375a2e0c3eb87c/sqlserver-cmdlets/sqlserver-module/vlatest/New-SqlAzureKeyVaultColumnMasterKeySettings.md
ms.topic: reference
author: stevestein
ms.author: sstein
keywords: powershell, cmdlet
manager: jhubbard
open_to_public_contributors: true
ms.service: sql-server
---

# New-SqlAzureKeyVaultColumnMasterKeySettings

## SYNOPSIS
Creates a SqlColumnMasterKeySettings object describing an asymmetric key stored in Azure Key Vault.

## SYNTAX

```
New-SqlAzureKeyVaultColumnMasterKeySettings [-KeyUrl] <String> [-InformationAction <ActionPreference>]
 [-InformationVariable <String>] [<CommonParameters>]
```

## DESCRIPTION
The **New-SqlAzureKeyVaultColumnMasterKeySettings** cmdlet creates a **SqlColumnMasterKeySettings** object.
The **SqlColumnMasterKeySettings** object references a key, stored in Azure Key Vault, which is intended to be used as a column master key for the Always Encrypted feature.
The **SqlColumnMasterKeySettings** object has two properties: **KeyStoreProviderName** and **KeyPath**.
This cmdlet sets the **KeyStoreProviderName** property to contain the name of column master key store provider for AzureKey Vault, and it sets the value of the **KeyPath** property to the specified key URL.

## EXAMPLES

### Example 1: Create a SqlColumnMasterKey object
```
PS C:\> $CMKSettings = New-SqlAzureKeyVaultColumnMasterKeySettings -KeyUrl "https://myvault.vault.contoso.net:443/keys/CMK/4c05f1a41b12488f9cba2ea964b6a700"
```

This command creates a **SqlColumnMasterKeySettings** object that references a key in Azure Key Vault and stores the result in the variable named CMKSettings.

## PARAMETERS

### -KeyUrl
Specifies the link, as a URL, of the key in Azure Key Vault.

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
