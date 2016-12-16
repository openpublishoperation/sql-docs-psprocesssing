---
external help file: Microsoft.SqlServer.Management.PSSnapins.dll-Help.xml
online version: 
schema: 2.0.0
ms.assetid: 0AEDBDE0-95F5-4345-8AC2-7C3BD422ECC0
updated_at: 12/13/2016 8:09 PM
ms.date: 12/13/2016
content_git_url: https://github.com/MicrosoftDocs/sql-docs-powershell/blob/live/sqlserver-cmdlets/sqlserver-module/vlatest/Remove-SqlColumnEncryptionKeyValue.md
original_content_git_url: https://github.com/MicrosoftDocs/sql-docs-powershell/blob/live/sqlserver-cmdlets/sqlserver-module/vlatest/Remove-SqlColumnEncryptionKeyValue.md
gitcommit: https://github.com/MicrosoftDocs/sql-docs-powershell/blob/f97823fbeb2d71358573a8e4b5c2c322a3a5c138/sqlserver-cmdlets/sqlserver-module/vlatest/Remove-SqlColumnEncryptionKeyValue.md
ms.topic: reference
author: stevestein
ms.author: sstein
keywords: powershell, cmdlet
manager: jhubbard
open_to_public_contributors: true
ms.service: sql-server
---

# Remove-SqlColumnEncryptionKeyValue

## SYNOPSIS
Removes an encrypted value from an existing column encryption key object in the database.

## SYNTAX

### ByObject
```
Remove-SqlColumnEncryptionKeyValue -ColumnMasterKeyName <String> [-Name] <String> [-InputObject] <Database>
 [-Script] [-InformationAction <ActionPreference>] [-InformationVariable <String>] [<CommonParameters>]
```

### ByPath
```
Remove-SqlColumnEncryptionKeyValue -ColumnMasterKeyName <String> [-Name] <String> [[-Path] <String>] [-Script]
 [-InformationAction <ActionPreference>] [-InformationVariable <String>] [<CommonParameters>]
```

## DESCRIPTION
The **Remove-SqlColumnEncryptionKeyValue** cmdlet modifies a column encryption key object in the database, by removing an entry for an encrypted value produced using the specified column master key.

## EXAMPLES

### Example 1: Remove a column encryption key value
```
PS C:\>Remove-SqlColumnEncryptionKeyValue -Name "CEK1" -ColumnMasterKey "CMK1"
```

This command removes the column encryption key value encrypted with a column master key named CMK1 from the column encryption key database object named CEK1.

## PARAMETERS

### -ColumnMasterKeyName
Specifies the name of the column master key that was used to produce the encrypted value that this cmdlet removes.

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
Specifies the name of the column encryption key object that this cmdlet removes.

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
Specifies the path of the SQL database for which this cmdlet runs the operation.
If you do not specify a value for this parameter, this cmdlet uses the current working location.

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

[Add-SqlColumnEncryptionKeyValue](xref:sqlserver-module/vlatest/Add-SqlColumnEncryptionKeyValue.md)


