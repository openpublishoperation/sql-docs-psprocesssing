---
external help file: Microsoft.SqlServer.Management.PSSnapins.dll-Help.xml
online version: 
schema: 2.0.0
ms.assetid: 4FBAA360-3B2C-41EF-A556-C13D40B36D45
updated_at: 12/8/2016 7:20 PM
ms.date: 12/8/2016
content_git_url: https://github.com/MicrosoftDocs/sql-docs-powershell/blob/master/sqlserver-cmdlets/sqlserver/vlatest/New-SqlColumnEncryptionKeyEncryptedValue.md
original_content_git_url: https://github.com/MicrosoftDocs/sql-docs-powershell/blob/master/sqlserver-cmdlets/sqlserver/vlatest/New-SqlColumnEncryptionKeyEncryptedValue.md
gitcommit: https://github.com/MicrosoftDocs/sql-docs-powershell/blob/b925b18b49186ab91cfeb5201e061d569d0eeae2/sqlserver-cmdlets/sqlserver/vlatest/New-SqlColumnEncryptionKeyEncryptedValue.md
ms.topic: reference
author: stevestein
ms.author: sstein
keywords: powershell, cmdlet
manager: jhubbard
open_to_public_contributors: true
ms.service: sql-server
---

# New-SqlColumnEncryptionKeyEncryptedValue

## SYNOPSIS
Creates the encrypted value of a column encryption key.

## SYNTAX

```
New-SqlColumnEncryptionKeyEncryptedValue [-TargetColumnMasterKeySettings] <SqlColumnMasterKeySettings>
 [[-ColumnMasterKeySettings] <SqlColumnMasterKeySettings>] [[-EncryptedValue] <String>]
 [-InformationAction <ActionPreference>] [-InformationVariable <String>] [<CommonParameters>]
```

## DESCRIPTION
The **New-SqlColumnEncryptionKeyEncryptedValue** cmdlet creates the encrypted value of a column encryption key.
The returned encrypted value is a hexadecimal string.
The cmdlet supports two modes of operation.
If a no encrypted value is specified, the cmdlet generates a new plaintext symmetric key and encrypts the key with the specified column master key.
If an encrypted value is specified, the cmdlet first decrypts the specified encrypted value and then re-encrypts the obtained plaintext key with the specified column master key.

## EXAMPLES

### Example 1: Generate a key and encrypt it using a certificate
```
PS C:\>$TargetCmkSettings = New-SqlCertificateStoreColumnMasterKeySettings -CertificateStoreLocation "CurrentUser" -CertificateThumbprint "f2260f28d909d21c642a3d8e0b45a830e79a1420"
C:\PS> New-SqlColumnEncryptionKeyEncryptedValue -TargetColumnMasterKeySettings $TargetCmkSettings
```

The first command generates a key and encrypts the key with a certificate in Windows Certificate Store and stores it in the variable named $TargetCmkSettings.
The result is a hexadecimal string that is an encrypted key value.

The second command creates the encrypted value of a column encryption key using the information stored in the variable named $TargetCmkSettings.

### Example 2: Generate a key and encrypt it with a certificate and an encryption key
```
PS C:\>$CmkSettings = New-SqlCertificateStoreColumnMasterKeySettings -CertificateStoreLocation "CurrentUser" -CertificateThumbprint "f2260f28d909d21c642a3d8e0b45a830e79a1420"
C:\PS> $TargetCmkSettings = New-SqlAzureKeyVaultColumnMasterKeySettings -KeyUrl "https://myvault.vault.contoso.net:443/keys/CMK/4c05f1a41b12488f9cba2ea964b6a700"
C:\PS> New-SqlColumnEncryptionKeyEncryptedValue -TargetColumnMasterKeySettings $TargetCmkSettings -ColumnMasterKeySettings $CmkSettings -EncryptedValue "0x016E000001630075007200720065006E00740075007300650072002F006D0079002F006200330039003900340035006200370031003100330037003700350032006400380061003100310033003900660035006200640036006400380066003700330038006600320033006200360032003000307925663D2C3E275DD272E15E606927DA4326F5735C2C8E84F91B9EFE44F503ED01C130984E83AF4513F8A4A8D0878D42364E958291AE25111A868D25B69FC5143EEC04131DA27D05F3442CB665ACB4BB3F6A7A9F07DBD5D212A772414A2CCA03BEBEB7BF0E22C644C715D739B983872AFB2D390229A0B5311BCA07E3C1D857EE8982320BBBE9382C960B9674E3CC3D618AD623D6A362BEAEF68B1B1BB49660DD643A4375A9285CD9EAA5B13BFE2792DA92025351E7B6067BA07B6178D03041F40F00D84326627094C9D6944DD912497B080058A529D2DA11C8D609604449714420B4E44ECD1EB26DEE18BF712146A51DD99A02E3D4EE692A503CF02F874497010772DE743DDFB2A74801AC9A94C876D1F93554B70CE0ECC437E7FC28BC11A08222977CDA807E256ED536C41700C631878226E513AFE1199A1DB4732F975AA09A1E75B8A19802AE018871A7A0AD5B1E29B942F30490EDABD310A4170B991EBCFDA2AFE43285D5406476204B381D8A33EEB0B967073B4C0127B1C7F0281AB310EE4B9A3C2D3EAB44A1F5D15D4739FFAEF6110ED4808446F6A05DBF4121B2B33A0AF5A457CD38F895B8F7ABDF792E3ADBC3AF55B1442625F88F80127D08DE9E4AC1BB2AAA46843A477135053CEEFA4327D8C999C16D8B49C225F34AD7588A5F9E93FB5532B1F1DC5AFB3CE23DDC8DC12327DD6B5985104D14F4A1BC0F61F0AACD"
```

The first command gets the certificate store column master key settings that uses the current user settings for the location and stores the result in the variable named $CmkSettings.

The second command uses the **New-SqlCertificateStoreColumnMasterKeySettings** cmdlet to get the column master key settings from the specified URL and stores the result in the variable named $TargetCmkSettings.

The third command decrypts the existing encrypted key value, which was encrypted using a certificate stored in Windows Certificate Store, and then encrypts the resulting plaintext key with another key stored in Azure Key Vault.
The result is a hexadecimal string that is the new encrypted key value.

## PARAMETERS

### -TargetColumnMasterKeySettings
Specifies the **SqlColumnMasterKeySettings** object that this cmdlet uses to determine where the column master key, to be used to encrypt the new encrypted value, is stored.
The **SqlColumnMasterKeySettings** object has two properties: **KeyStoreProviderName** and **KeyPath**.
**KeyStoreProviderName** specifies the name of a column master key store provider.
An Always Encrypted-enabled client driver needs to access the key store containing the column master key.
**KeyPath** specifies the location of the column master key within the key store.
The format for **KeyPath** is specific to the key store.

```yaml
Type: SqlColumnMasterKeySettings
Parameter Sets: (All)
Aliases: 

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ColumnMasterKeySettings
Specifies the **SqlColumnMasterKeySettings** object that this cmdlet uses to find where the column master key is stored.

```yaml
Type: SqlColumnMasterKeySettings
Parameter Sets: (All)
Aliases: 

Required: False
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -EncryptedValue
Specifies the existing encrypted value.
If you specify a value for this parameter, the cmdlet will first decrypt this value using the column master key referenced by the *ColumnMasterKeySettings* parameter and then re-encrypt it using the column master key referenced by the *TargetColumnMasterKeySettings* parameter.

```yaml
Type: String
Parameter Sets: (All)
Aliases: 

Required: False
Position: 2
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

### String

## NOTES

## RELATED LINKS

[Configure Always Encrypted using PowerShell](https://msdn.microsoft.com/library/mt755926.aspx)

[Add-SqlColumnEncryptionKeyValue](xref:sqlserver/vlatest/Add-SqlColumnEncryptionKeyValue.md)

[Remove-SqlColumnEncryptionKeyValue](xref:sqlserver/vlatest/Remove-SqlColumnEncryptionKeyValue.md)

[New-SqlCertificateStoreColumnMasterKeySettings](xref:sqlserver/vlatest/New-SqlCertificateStoreColumnMasterKeySettings.md)

[New-SqlAzureKeyVaultColumnMasterKeySettings](xref:sqlserver/vlatest/New-SqlAzureKeyVaultColumnMasterKeySettings.md)


