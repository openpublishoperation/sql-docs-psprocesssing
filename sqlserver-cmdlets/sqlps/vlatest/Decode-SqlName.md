---
external help file: Microsoft.SqlServer.Management.PSProvider.dll-Help.xml
online version: 
schema: 2.0.0
ms.assetid: D090069E-D04C-4D5E-B7B2-A3F1EC035928
updated_at: 12/8/2016 7:20 PM
ms.date: 12/8/2016
content_git_url: https://github.com/MicrosoftDocs/sql-docs-powershell/blob/master/sqlserver-cmdlets/sqlps/vlatest/Decode-SqlName.md
original_content_git_url: https://github.com/MicrosoftDocs/sql-docs-powershell/blob/master/sqlserver-cmdlets/sqlps/vlatest/Decode-SqlName.md
gitcommit: https://github.com/MicrosoftDocs/sql-docs-powershell/blob/b925b18b49186ab91cfeb5201e061d569d0eeae2/sqlserver-cmdlets/sqlps/vlatest/Decode-SqlName.md
ms.topic: reference
author: stevestein
ms.author: sstein
keywords: powershell, cmdlet
manager: jhubbard
open_to_public_contributors: true
ms.service: sql-server
---

# Decode-SqlName

## SYNOPSIS
Decodes an encoded SQL Server identifier name.

## SYNTAX

## DESCRIPTION
The **Decode-SqlName** cmdlet decodes an encoded SQL Server identifier.
SQL Server delimited identifiers can contain special characters that are not normally supported in PowerShell object names.
These extended characters must be either encoded to their hexadecimal representation or escaped using the \` character.
Certain characters cannot be escaped.
The hexadecimal encoding is in the format %nn.
This cmdlet converts the following encodings to the corresponding characters: 

- %5C becomes \
- %3A becomes : 
- %2E becomes .
- %2F becomes /
- %25 becomes %
- %3C becomes \<
- %3E becomes \>
- %2A becomes *
- %3F becomes ?
- %5B becomes \[
- %5D becomes \]
- %7C becomes |

## EXAMPLES

### Example 1: Decode a SQL Server identifier that is encoded in a hexadecimal representation
```
PS C:\>Decode-SqlName -SqlName "My%3ATable`/"
My:Table/
```

This command decodes a SQL Server identifier that has been encoded in hexadecimal representation for the ':' character.
PowerShell also removes the escaping back-tick character (\`) from an escaped '/' character.

## PARAMETERS

### CommonParameters
This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable. For more information, see about_CommonParameters (http://go.microsoft.com/fwlink/?LinkID=113216).

## INPUTS

### String

## OUTPUTS

### String

## NOTES

## RELATED LINKS


