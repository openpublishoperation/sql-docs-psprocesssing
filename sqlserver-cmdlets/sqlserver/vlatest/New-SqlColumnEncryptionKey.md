---
external help file: Microsoft.SqlServer.Management.PSSnapins.dll-Help.xml
online version: 
schema: 2.0.0
ms.assetid: 931FFA81-4195-4092-AA67-D8D31D81DA25
updated_at: 3/13/2017 4:14 PM
ms.date: 3/13/2017
content_git_url: https://github.com/MicrosoftDocs/sql-docs-powershell/blob/live/sqlserver-cmdlets/sqlserver/vlatest/New-SqlColumnEncryptionKey.md
original_content_git_url: https://github.com/MicrosoftDocs/sql-docs-powershell/blob/live/sqlserver-cmdlets/sqlserver/vlatest/New-SqlColumnEncryptionKey.md
gitcommit: https://github.com/MicrosoftDocs/sql-docs-powershell/blob/6eefe64a0ce19459190f09768267a4c79f9a6af9/sqlserver-cmdlets/sqlserver/vlatest/New-SqlColumnEncryptionKey.md
ms.topic: reference
author: stevestein
ms.author: sstein
keywords: powershell, cmdlet
manager: jhubbard
open_to_public_contributors: True
ms.service: sql-server
---

# New-SqlColumnEncryptionKey

## SYNOPSIS
Crates a column encryption key object in the database.

## SYNTAX

### ByObject
```
New-SqlColumnEncryptionKey -ColumnMasterKeyName <String> [-EncryptedValue <String>] [-Name] <String>
 [-InputObject] <Database> [-Script] [-InformationAction <ActionPreference>] [-InformationVariable <String>]
 [<CommonParameters>]
```

### ByPath
```
New-SqlColumnEncryptionKey -ColumnMasterKeyName <String> [-EncryptedValue <String>] [-Name] <String>
 [[-Path] <String>] [-Script] [-InformationAction <ActionPreference>] [-InformationVariable <String>]
 [<CommonParameters>]
```

## DESCRIPTION
The **New-SqlColumnEncryptionKey** cmdlet creates a column encryption key object in the database.
A column encryption key object encapsulates an encrypted value of a symmetric cryptographic key that can be subsequently used to encrypt database columns using the Always Encrypted feature.
This cmdlet supports two modes of operation.
If the encrypted value of a column encryption key is specified, the cmdlet simply creates a new column encryption key object encapsulating the specified encrypted value.
If the encrypted value of a column encryption key is not specified, the cmdlet first generates a plaintext key value, encrypts it with the specified column master key, and then creates a new column encryption key object encapsulating the generated encrypted value.

## EXAMPLES

### Example 1: Generate a column encryption key
```
PS C:\> New-SqlColumnEncryptionKey -Name "CEK1" -ColumnMasterKeyName "CMK1"
```

This command generates a plaintext value of a column encryption key, encrypts the plaintext value with the specified master key, and then creates a column encryption key object, encapsulating the generated encrypted value in the database.

### Example 2: Generate a column encryption key using a specific encryption string
```
PS C:\> New-SqlColumnEncryptionKey "CEK1" "CMK1" -EncryptedValue "0x01700000016C006F00630061006C006D0061006300680069006E0065002F006D0079002F003200660061006600640038003100320031003400340034006500620031006100320065003000360039003300340038006100350064003400300032003300380065006600620063006300610031006300284FC4316518CF3328A6D9304F65DD2CE387B79D95D077B4156E9ED8683FC0E09FA848275C685373228762B02DF2522AFF6D661782607B4A2275F2F922A5324B392C9D498E4ECFC61B79F0553EE8FB2E5A8635C4DBC0224D5A7F1B136C182DCDE32A00451F1A7AC6B4492067FD0FAC7D3D6F4AB7FC0E86614455DBB2AB37013E0A5B8B5089B180CA36D8B06CDB15E95A7D06E25AACB645D42C85B0B7EA2962BD3080B9A7CDB805C6279FE7DD6941E7EA4C2139E0D4101D8D7891076E70D433A214E82D9030CF1F40C503103075DEEB3D64537D15D244F503C2750CF940B71967F51095BFA51A85D2F764C78704CAB6F015EA87753355367C5C9F66E465C0C66BADEDFDF76FB7E5C21A0D89A2FCCA8595471F8918B1387E055FA0B816E74201CD5C50129D29C015895CD073925B6EA87CAF4A4FAF018C06A3856F5DFB724F42807543F777D82B809232B465D983E6F19DFB572BEA7B61C50154605452A891190FB5A0C4E464862CF5EFAD5E7D91F7D65AA1A78F688E69A1EB098AB42E95C674E234173CD7E0925541AD5AE7CED9A3D12FDFE6EB8EA4F8AAD2629D4F5A18BA3DDCC9CF7F352A892D4BEBDC4A1303F9C683DACD51A237E34B045EBE579A381E26B40DCFBF49EFFA6F65D17F37C6DBA54AA99A65D5573D4EB5BA038E024910A4D36B79A1D4E3C70349DADFF08FD8B4DEE77FDB57F01CB276ED5E676F1EC973154F86"
```

This command creates a column encryption key object, encapsulating the specified encrypted value, in the database.

## PARAMETERS

### -ColumnMasterKeyName
Specifies the name of the column master key that was used to produce the specified encrypted value of the column encryption key, or the name the column master key that is used to produce the new encrypted value.

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
Specifies a string that this cmdlet uses to encrypt the column master key.

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

### -Name
Specifies the name of the column encryption key object to be created.

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
Indicates that this cmdlet runs a Transact-SQL script that performs the operation.

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

### SqlColumnEncryptionKey

## NOTES

## RELATED LINKS

[Configure Always Encrypted using PowerShell](https://msdn.microsoft.com/library/mt755926.aspx)

[Get-SqlColumnEncryptionKey](xref:sqlserver/vlatest/Get-SqlColumnEncryptionKey.md)

[Remove-SqlColumnEncryptionKey](xref:sqlserver/vlatest/Remove-SqlColumnEncryptionKey.md)
