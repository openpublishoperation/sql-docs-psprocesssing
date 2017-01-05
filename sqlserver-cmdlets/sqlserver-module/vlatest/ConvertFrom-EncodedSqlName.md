---
external help file: Microsoft.SqlServer.Management.PSProvider.dll-Help.xml
online version: 
schema: 2.0.0
ms.assetid: 7DAADDA3-C07F-40BD-84BE-2B8D25A152E9
updated_at: 1/5/2017 8:57 AM
ms.date: 1/5/2017
content_git_url: https://github.com/MicrosoftDocs/sql-docs-powershell/blob/master/sqlserver-cmdlets/sqlserver-module/vlatest/ConvertFrom-EncodedSqlName.md
original_content_git_url: https://github.com/MicrosoftDocs/sql-docs-powershell/blob/master/sqlserver-cmdlets/sqlserver-module/vlatest/ConvertFrom-EncodedSqlName.md
gitcommit: https://github.com/MicrosoftDocs/sql-docs-powershell/blob/0d97835841eb5cfbe37d096037375a2e0c3eb87c/sqlserver-cmdlets/sqlserver-module/vlatest/ConvertFrom-EncodedSqlName.md
ms.topic: reference
author: stevestein
ms.author: sstein
keywords: powershell, cmdlet
manager: jhubbard
open_to_public_contributors: true
ms.service: sql-server
---

# ConvertFrom-EncodedSqlName

## SYNOPSIS
Returns the original SQL Server identifier when given an identifier that has been encoded into a format usable in Windows PowerShell paths.

## SYNTAX

```
ConvertFrom-EncodedSqlName [-SqlName] <String> [-InformationAction <ActionPreference>]
 [-InformationVariable <String>] [<CommonParameters>]
```

## DESCRIPTION
The **ConvertFrom-EncodedSqlName** cmdlet returns the un-encoded SQL Server identifier when given an identifier that has been encoded into a format usable in Windows PowerShell paths.
SQL Server delimited identifiers can contain special characters not normally supported in Windows PowerShell object names.
These extended characters must be either encoded to their hexadecimal representation or escaped using the \` character.
Certain characters, such as the colon character (:) cannot be escaped.
The hexadecimal encoding is in the format %nn.
Decode-SqlName converts the following encodings to the corresponding characters:    %5C-\    %3A-:    %2E-. 
%2F-/   %25-%    %3C-\<    %3E-\>    %2A-*    %3F-? 
%5B-\[    %5D-\]    %7C-|

## EXAMPLES

### Example 1: Decode a SQL Server identifier
```
PS C:\> ConvertFrom-EncodedSqlName -SqlName "My%3ATable`/" "My:Table/"
```

This command decodes a SQL Server identifier that has an encoded hexadecimal representation for the : character.
Windows PowerShell also removes the escaping back-tick character (\`) from an escaped / character.

## PARAMETERS

### -SqlName
Specifies the SQL Server identifier that this cmdlet reformats.

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

[ConvertTo-EncodedSqlName](xref:sqlserver-module/vlatest/ConvertTo-EncodedSqlName.md)
