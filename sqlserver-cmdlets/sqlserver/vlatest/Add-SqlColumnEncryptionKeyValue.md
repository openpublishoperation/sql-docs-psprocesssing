---
external help file: Microsoft.SqlServer.Management.PSSnapins.dll-Help.xml
online version: 
schema: 2.0.0
ms.assetid: DC291DDD-89BC-414D-8583-6A9EDF01CE51
updated_at: 12/8/2016 7:20 PM
ms.date: 12/8/2016
content_git_url: https://github.com/MicrosoftDocs/sql-docs-powershell/blob/master/sqlserver-cmdlets/sqlserver/vlatest/Add-SqlColumnEncryptionKeyValue.md
original_content_git_url: https://github.com/MicrosoftDocs/sql-docs-powershell/blob/master/sqlserver-cmdlets/sqlserver/vlatest/Add-SqlColumnEncryptionKeyValue.md
gitcommit: https://github.com/MicrosoftDocs/sql-docs-powershell/blob/b925b18b49186ab91cfeb5201e061d569d0eeae2/sqlserver-cmdlets/sqlserver/vlatest/Add-SqlColumnEncryptionKeyValue.md
ms.topic: reference
author: stevestein
ms.author: sstein
keywords: powershell, cmdlet
manager: jhubbard
open_to_public_contributors: true
ms.service: sql-server
---

# Add-SqlColumnEncryptionKeyValue

## SYNOPSIS
Adds an encrypted value for an existing column encryption key object in the database.

## SYNTAX

### ByObject
```
Add-SqlColumnEncryptionKeyValue -ColumnMasterKeyName <String> -EncryptedValue <String> [-Name] <String>
 [-InputObject] <Database> [-Script] [-InformationAction <ActionPreference>] [-InformationVariable <String>]
 [<CommonParameters>]
```

### ByPath
```
Add-SqlColumnEncryptionKeyValue -ColumnMasterKeyName <String> -EncryptedValue <String> [-Name] <String>
 [[-Path] <String>] [-Script] [-InformationAction <ActionPreference>] [-InformationVariable <String>]
 [<CommonParameters>]
```

## DESCRIPTION
The **Add-SqlColumnEncryptionKeyValue** cmdlet adds a column encryption key object in the database, by adding an entry for a new encrypted value.
Initially, a column encryption key object contains one entry containing an encrypted value of a column encryption key for Always Encrypted.
This cmdlet adds the second encrypted value entry, in order to support a rotating column master key.
Both the new and the initial encrypted value should represent the same plaintext key, but they should be produced using different column master keys.

## EXAMPLES

### Example 1: Add an encrypted value for an existing column encryption key
```
PS C:\>Add-SqlColumnEncryptionKeyValue -Name "CEK1" -InputObject $Database -ColumnMasterKeyName "CMK2" -ColumnEncryptionKeyCiphertext "0x016E000001630075007200720065006E00740075007300650072002F006D0079002F006200330039003900340035006200370031003100330037003700350032006400380061003100310033003900660035006200640036006400380066003700330038006600320033006200360032003000307925663D2C3E275DD272E15E606927DA4326F5735C2C8E84F91B9EFE44F503ED01C130984E83AF4513F8A4A8D0878D42364E958291AE25111A868D25B69FC5143EEC04131DA27D05F3442CB665ACB4BB3F6A7A9F07DBD5D212A772414A2CCA03BEBEB7BF0E22C644C715D739B983872AFB2D390229A0B5311BCA07E3C1D857EE8982320BBBE9382C960B9674E3CC3D618AD623D6A362BEAEF68B1B1BB49660DD643A4375A9285CD9EAA5B13BFE2792DA92025351E7B6067BA07B6178D03041F40F00D84326627094C9D6944DD912497B080058A529D2DA11C8D609604449714420B4E44ECD1EB26DEE18BF712146A51DD99A02E3D4EE692A503CF02F874497010772DE743DDFB2A74801AC9A94C876D1F93554B70CE0ECC437E7FC28BC11A08222977CDA807E256ED536C41700C631878226E513AFE1199A1DB4732F975AA09A1E75B8A19802AE018871A7A0AD5B1E29B942F30490EDABD310A4170B991EBCFDA2AFE43285D5406476204B381D8A33EEB0B967073B4C0127B1C7F0281AB310EE4B9A3C2D3EAB44A1F5D15D4739FFAEF6110ED4808446F6A05DBF4121B2B33A0AF5A457CD38F895B8F7ABDF792E3ADBC3AF55B1442625F88F80127D08DE9E4AC1BB2AAA46843A477135053CEEFA4327D8C999C16D8B49C225F34AD7588A5F9E93FB5532B1F1DC5AFB3CE23DDC8DC12327DD6B5985104D14F4A1BC0F61F0AACD"
```

This command adds a new encrypted value for the column encryption key database object named CEK1.
The new value is encrypted with the column master key, named CMK2.

## PARAMETERS

### -ColumnMasterKeyName
Specifies the name of the column master key that is used to produce the encrypted value that this cmdlet adds to the database.

```yaml
Type: String
Parameter Sets: (All)
Aliases: 

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -EncryptedValue
Specifies the encrypted value that this cmdlet adds to the database.
You are responsible that the encrypted value, if specified, has been generated using the specified column master key.

```yaml
Type: String
Parameter Sets: (All)
Aliases: 

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Name
Specifies the name of the column encryption key object that this cmdlet modifies.

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
Specifies the SQL database object for which this cmdlet runs the operation.

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
Indicates that this cmdlet runs a script to add the SQL column encryption key value.

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
Specifies the path of the SQL database for which this cmdlet runs the operation.
If you do not specify the value of this parameter, this cmdlet uses the current working location.

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

## NOTES

## RELATED LINKS

[Configure Always Encrypted using PowerShell](https://msdn.microsoft.com/library/mt755926.aspx)

[New-SqlColumnEncryptionKeyEncryptedValue](xref:sqlserver/vlatest/New-SqlColumnEncryptionKeyEncryptedValue.md)

[Remove-SqlColumnEncryptionKeyValue](xref:sqlserver/vlatest/Remove-SqlColumnEncryptionKeyValue.md)


