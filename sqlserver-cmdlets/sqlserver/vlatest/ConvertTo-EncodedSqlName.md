---
external help file: Microsoft.SqlServer.Management.PSProvider.dll-Help.xml
online version: 
schema: 2.0.0
ms.assetid: 7942B878-8FE8-4928-9F54-BCF46E622805
updated_at: 12/8/2016 7:20 PM
ms.date: 12/8/2016
content_git_url: https://github.com/MicrosoftDocs/sql-docs-powershell/blob/master/sqlserver-cmdlets/sqlserver/vlatest/ConvertTo-EncodedSqlName.md
original_content_git_url: https://github.com/MicrosoftDocs/sql-docs-powershell/blob/master/sqlserver-cmdlets/sqlserver/vlatest/ConvertTo-EncodedSqlName.md
gitcommit: https://github.com/MicrosoftDocs/sql-docs-powershell/blob/b925b18b49186ab91cfeb5201e061d569d0eeae2/sqlserver-cmdlets/sqlserver/vlatest/ConvertTo-EncodedSqlName.md
ms.topic: reference
author: stevestein
ms.author: sstein
keywords: powershell, cmdlet
manager: jhubbard
open_to_public_contributors: true
ms.service: sql-server
---

# ConvertTo-EncodedSqlName

## SYNOPSIS
Encodes extended characters in SQL Server names to formats usable in Windows PowerShell paths.

## SYNTAX

```
ConvertTo-EncodedSqlName [-SqlName] <String> [-InformationAction <ActionPreference>]
 [-InformationVariable <String>] [<CommonParameters>]
```

## DESCRIPTION
The **ConvertTo-EncodedSqlName** cmdlet encodes special characters in SQL Server names to formats usable in Windows PowerShell paths.
SQL Server delimited identifiers can contain characters not normally supported in Windows PowerShell object names.
When using delimited identifiers in SQL Server provider paths, these extended characters must be either encoded to their hexadecimal representation or escaped using the \` character.
Certain characters, such as the colon character (:) cannot be escaped.
The hexadecimal encoding for the characters is in the format %nn.
The characters encoded by **ConvertTo-EncodedSqlName** are: \:./%\<\>*?\[\]|

## EXAMPLES

### Example 1: Encode a SQL Server table name
```
PS C:\>ConvertTo-EncodedSqlName -SqlName "My:Table/" "My%3ATable%2F"
```

This command encodes a SQL Server table name that contains : and / characters.

## PARAMETERS

### -SqlName
Specifies the SQL Server identifier to be encoded.

```yaml
Type: String
Parameter Sets: (All)
Aliases: 

Required: True
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
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

### String

## OUTPUTS

### String

## NOTES

## RELATED LINKS

[Using SQL Server Identifiers in PowerShell](https://technet.microsoft.com/en-us/library/cc281841(v=sql.110).aspx)

[ConvertFrom-EncodedSqlName](xref:sqlserver/vlatest/ConvertFrom-EncodedSqlName.md)


