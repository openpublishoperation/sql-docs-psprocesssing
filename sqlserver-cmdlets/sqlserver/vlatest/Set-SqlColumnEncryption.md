---
external help file: Microsoft.SqlServer.Management.PSSnapins.dll-Help.xml
online version: 
schema: 2.0.0
ms.assetid: 228F6102-2D91-4772-885D-29D118EA7E99
updated_at: 12/8/2016 7:20 PM
ms.date: 12/8/2016
content_git_url: https://github.com/MicrosoftDocs/sql-docs-powershell/blob/master/sqlserver-cmdlets/sqlserver/vlatest/Set-SqlColumnEncryption.md
original_content_git_url: https://github.com/MicrosoftDocs/sql-docs-powershell/blob/master/sqlserver-cmdlets/sqlserver/vlatest/Set-SqlColumnEncryption.md
gitcommit: https://github.com/MicrosoftDocs/sql-docs-powershell/blob/b925b18b49186ab91cfeb5201e061d569d0eeae2/sqlserver-cmdlets/sqlserver/vlatest/Set-SqlColumnEncryption.md
ms.topic: reference
author: stevestein
ms.author: sstein
keywords: powershell, cmdlet
manager: jhubbard
open_to_public_contributors: true
ms.service: sql-server
---

# Set-SqlColumnEncryption

## SYNOPSIS
Encrypts, decrypts, or re-encrypts specified columns in the database.

## SYNTAX

### ByObject
```
Set-SqlColumnEncryption -ColumnEncryptionSettings <SqlColumnEncryptionSettings[]> [-InputObject] <Database>
 [-Script] [-InformationAction <ActionPreference>] [-InformationVariable <String>] [<CommonParameters>]
```

### ByPath
```
Set-SqlColumnEncryption -ColumnEncryptionSettings <SqlColumnEncryptionSettings[]> [[-Path] <String>] [-Script]
 [-InformationAction <ActionPreference>] [-InformationVariable <String>] [<CommonParameters>]
```

## DESCRIPTION
The **Set-SqlColumnEncryption** cmdlet encrypts, decrypts, or re-encrypts specified database columns using the Always Encrypted feature.
The cmdlet accepts an array of **SqlColumnEncryptionSettings** objects, each of which specifies the target encryption configuration for one column in the database.
The cmdlet will encrypt, decrypt, or re-encrypt each specified column, depending on what the current encryption configuration of the column is and the specified target encryption settings.

## EXAMPLES

### Example 1: Apply target encryption settings to multiple columns
```
PS C:\>$Ces = @()
PS C:\> $Ces += New-SqlColumnEncryptionSettings -ColumnName dbo.Student.Id -EncryptionType Deterministic -EncryptionKey MyCek
PS C:\> $Ces += New-SqlColumnEncryptionSettings -ColumnName dbo.Student.LastName -EncryptionType Randomized -EncryptionKey MyCek
PS C:\> $Ces += New-SqlColumnEncryptionSettings -ColumnName dbo.Student.FirstName -EncryptionType Plaintext
PS C:\> Set-SqlColumnEncryption $Ces ?Data Source=myServerName;Initial Catalog=myDatabaseName;Integrated Security=True -Verbose
```

This example applies the target encryption settings to three database columns.
As a result, the dbo.Student.Id column is encrypted using deterministic encryption and the column encryption key, named MyCEK.
The dbo.Student.LastName column is encrypted that uses randomized encryption and the column encryption key, named MyCEK.
The dbo.StudentFirstName column is not encrypted, if the column is initially encrypted, it is decrypted.

## PARAMETERS

### -ColumnEncryptionSettings
Specifies an array of **SqlColumnEncryptionSettings** objects, each of which specifies the target encryption configuration for one column in the database.

```yaml
Type: SqlColumnEncryptionSettings[]
Parameter Sets: (All)
Aliases: 

Required: True
Position: Named
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
Position: 1
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
Position: 1
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

[SQL Server Cmdlets](xref:sqlserver/vlatest/SqlServer.md)


