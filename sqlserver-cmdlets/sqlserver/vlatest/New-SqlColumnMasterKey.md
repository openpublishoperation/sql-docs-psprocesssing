---
external help file: Microsoft.SqlServer.Management.PSSnapins.dll-Help.xml
online version: 
schema: 2.0.0
ms.assetid: C74866E4-C488-487D-8D92-8C7CD33513FE
updated_at: 12/8/2016 7:20 PM
ms.date: 12/8/2016
content_git_url: https://github.com/MicrosoftDocs/sql-docs-powershell/blob/master/sqlserver-cmdlets/sqlserver/vlatest/New-SqlColumnMasterKey.md
original_content_git_url: https://github.com/MicrosoftDocs/sql-docs-powershell/blob/master/sqlserver-cmdlets/sqlserver/vlatest/New-SqlColumnMasterKey.md
gitcommit: https://github.com/MicrosoftDocs/sql-docs-powershell/blob/b925b18b49186ab91cfeb5201e061d569d0eeae2/sqlserver-cmdlets/sqlserver/vlatest/New-SqlColumnMasterKey.md
ms.topic: reference
author: stevestein
ms.author: sstein
keywords: powershell, cmdlet
manager: jhubbard
open_to_public_contributors: true
ms.service: sql-server
---

# New-SqlColumnMasterKey

## SYNOPSIS
Creates a column master key object in the database.

## SYNTAX

### ByObject
```
New-SqlColumnMasterKey -ColumnMasterKeySettings <SqlColumnMasterKeySettings> [-Name] <String>
 [-InputObject] <Database> [-Script] [-InformationAction <ActionPreference>] [-InformationVariable <String>]
 [<CommonParameters>]
```

### ByPath
```
New-SqlColumnMasterKey -ColumnMasterKeySettings <SqlColumnMasterKeySettings> [-Name] <String>
 [[-Path] <String>] [-Script] [-InformationAction <ActionPreference>] [-InformationVariable <String>]
 [<CommonParameters>]
```

## DESCRIPTION
The **New-SqlColumnMasterKey** cmdlet creates a column master key object in the database.
A column master key object captures the location of a physical cryptographic key that is intended to be used as a column master key for the Always Encrypted feature.

## EXAMPLES

### Example 1: Create a column master key object that references a certificate
```
PS C:\>$CmkSettings = New-SqlCertificateStoreColumnMasterKeySettings -CertificateStoreLocation "CurrentUser" -CertificateThumbprint "f2260f28d909d21c642a3d8e0b45a830e79a1420"
PS C:\> New-SqlColumnMasterKey -Name "CMK1" -ColumnMasterKeySettings $CmkSettings
```

The first command uses the **New-SqlCertificateStoreColumnMasterKeySettings** cmdlet to create column master settings referencing a certificate in Windows Certificate Store and stores the result in the variable named $CmkSettings.

The second command create a column master key object named CMK1 that uses the settings stored in the $CmkSettings variable.

### Example 2: Create a column master key object that references a key in Azure Key Vault
```
PS C:\>$CmkSettings = New-SqlAzureKeyVaultColumnMasterKeySettings -KeyUrl "https://myvault.vault.contoso.net:443/keys/CMK/4c05f1a41b12488f9cba2ea964b6a700"
PS C:\> New-SqlColumnMasterKey "CMK1" -ColumnMasterKeySettings $CmkSettings
```

The first command uses the **New-SqlCertificateStoreColumnMasterKeySettings** cmdlet to create column master key object referencing a key in Azure Key Vault and stores the result in the variable named $CmkSettings.

The second command create a column master key object named CMK1 that uses the settings stored in the $CmkSettings variable.

### Example 3: Create a column master key object that references a key supporting CNG
```
PS C:\>$CmkSettings = New-SqlCngColumnMasterKeySettings -CngProviderName "Microsoft Software Key Storage Provider" -KeyName "AlwaysEncryptedKey"
PS C:\> New-SqlColumnMasterKey "CMK1" -ColumnMasterKeySettings $CmkSettings
```

The first command uses the **New-SqlCertificateStoreColumnMasterKeySettings** cmdlet to create column master key object referencing a key in a key store supporting the Cryptography Next Generation (CNG) API and stores the result in the variable named $CmkSettings.

The second command create a column master key object named CMK1 that uses the settings stored in the $CmkSettings variable.

### Example 4: Create a column master key object that references a key supporting CSP
```
PS C:\>$CmkSettings = New-SqlCspColumnMasterKeySettings "MyCspProvider" "AlwaysEncryptedKey"
C:\PS> New-SqlColumnMasterKey "CMK1" -ColumnMasterKeySettings $CmkSettings
```

The first command uses the **New-SqlCertificateStoreColumnMasterKeySettings** cmdlet to create column master key object referencing a key in a key store key store with a Cryptography Service Provider (CSP) supporting Cryptography API (CAPI).

The second command create a column master key object named CMK1 that uses the settings stored in the $CmkSettings variable.

## PARAMETERS

### -ColumnMasterKeySettings
Specifies the **SqlColumnMasterKeySettings** object that specifies the location of the actual column master key.
The **SqlColumnMasterKeySettings** object has two properties: **KeyStoreProviderName** and **KeyPath**.
**KeyStoreProviderName** specifies the name of a column master key store provider, which an Always Encrypted-enabled client driver must use to access the key store containing the column master key.
**KeyPath** specifies the location of the column master key within the key store.
The **KeyPath** format is specific to the key store.

```yaml
Type: SqlColumnMasterKeySettings
Parameter Sets: (All)
Aliases: 

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Name
Specifies the name of the column master key object that this cmdlet creates.

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

### -InputObject
Specifies the SQL database object, for which this cmdlet runs the operation.

```yaml
Type: Database
Parameter Sets: ByObject
Aliases: 

Required: True
Position: 2
Default value: None
Accept pipeline input: True (ByValue)
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

### -Path
Specifies the path of the SQL database, for which this cmdlet runs the operation.
If you do not specify a value for this parameter, the cmdlet uses the current working location.

```yaml
Type: String
Parameter Sets: ByPath
Aliases: 

Required: False
Position: 2
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters
This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable. For more information, see about_CommonParameters (http://go.microsoft.com/fwlink/?LinkID=113216).

## INPUTS

## OUTPUTS

### Microsoft.SqlServer.Management.Smo.SqlColumnMasterKey

## NOTES

## RELATED LINKS

[Configure Always Encrypted using PowerShell](https://msdn.microsoft.com/library/mt755926.aspx)

[Get-SqlColumnMasterKey](xref:sqlserver/vlatest/Get-SqlColumnMasterKey.md)

[Remove-SqlColumnMasterKey](xref:sqlserver/vlatest/Remove-SqlColumnMasterKey.md)


