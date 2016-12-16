---
external help file: Microsoft.SqlServer.Management.PSSnapins.dll-Help.xml
online version: 
schema: 2.0.0
ms.assetid: FE8B0088-227D-49B8-8294-ABA60113CCA0
updated_at: 12/13/2016 8:09 PM
ms.date: 12/13/2016
content_git_url: https://github.com/MicrosoftDocs/sql-docs-powershell/blob/live/sqlserver-cmdlets/sqlserver-module/vlatest/New-SqlColumnEncryptionSettings.md
original_content_git_url: https://github.com/MicrosoftDocs/sql-docs-powershell/blob/live/sqlserver-cmdlets/sqlserver-module/vlatest/New-SqlColumnEncryptionSettings.md
gitcommit: https://github.com/MicrosoftDocs/sql-docs-powershell/blob/f97823fbeb2d71358573a8e4b5c2c322a3a5c138/sqlserver-cmdlets/sqlserver-module/vlatest/New-SqlColumnEncryptionSettings.md
ms.topic: reference
author: stevestein
ms.author: sstein
keywords: powershell, cmdlet
manager: jhubbard
open_to_public_contributors: true
ms.service: sql-server
---

# New-SqlColumnEncryptionSettings

## SYNOPSIS
Creates a SqlColumnEncryptionSettings object that encapsulates information about a single column's encryption, including CEK and encryption type.

## SYNTAX

```
New-SqlColumnEncryptionSettings [-ColumnName] <String> [-EncryptionType] <String> [[-EncryptionKey] <String>]
 [-InformationAction <ActionPreference>] [-InformationVariable <String>] [<CommonParameters>]
```

## DESCRIPTION
The **New-SqlColumnEncryptionSettings** cmdlet creates a **SqlColumnEncryptionSettings** object.
The **SqlColumnEncryptionSettings** object encapsulates information about the Always Encrypted settings for a single database columns, including the encryption type and the column encryption key.

## EXAMPLES

### Example 1: Create an encrypted SqlColumnEncryptionSettings object for a column
```
PS C:\>$EncryptionSettings = New-SqlColumnEncryptionSettings dbo.Person.LastName "Deterministic" MyCEK
```

This command creates a **SqlColumnEncryptionSettings** object for the column named dbo.Person.LastName, specifying the deterministic encryption and column encryption key named MyCEK for the column.
The command stores the result in the variable named $EncryptionSettings.

### Example 2: Create an unencrypted SqlColumnEncryptionSettings object for a column
```
PS C:\>$EncryptionSettings = New-SqlColumnEncryptionSettings dbo.Person.FirstName "Plaintext"
```

This command creates a **SqlColumnEncryptionSettings** object for the dbo.Person.FirstName column, specifying the column is not encrypted.
The command stores the result in the variable named $EncryptionSettings.

## PARAMETERS

### -ColumnName
Specifies the name of the database column that uses the following format: \[\<schemaName\>.\]\<tableName\>.\<columnName\>.

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

### -EncryptionType
Specifies the type of encryption.
The acceptable values for this parameter are:

- Deterministic, for deterministic encryption
- Randomized, for randomized encryption
-  Plaintext, indicating that the column is not encrypted.

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

### -EncryptionKey
Specifies the name of the column encryption key object.
This argument is not allowed if the *EncryptionType* parameter value is set to Plaintext.

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

### SqlColumnEncryptionSettings

## NOTES

## RELATED LINKS

[Configure Always Encrypted using PowerShell](https://msdn.microsoft.com/library/mt755926.aspx)

[SQL Server Cmdlets](xref:sqlserver-module/vlatest/SqlServer.md)


