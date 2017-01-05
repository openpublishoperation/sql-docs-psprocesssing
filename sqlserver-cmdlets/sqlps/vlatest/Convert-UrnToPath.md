---
external help file: Microsoft.SqlServer.Management.PSProvider.dll-Help.xml
online version: 
schema: 2.0.0
ms.assetid: 40A494F2-8238-4DB3-9F6E-B0A1A53A8FED
updated_at: 1/4/2017 6:38 PM
ms.date: 1/4/2017
content_git_url: https://github.com/MicrosoftDocs/sql-docs-powershell/blob/live/sqlserver-cmdlets/sqlps/vlatest/Convert-UrnToPath.md
original_content_git_url: https://github.com/MicrosoftDocs/sql-docs-powershell/blob/live/sqlserver-cmdlets/sqlps/vlatest/Convert-UrnToPath.md
gitcommit: https://github.com/MicrosoftDocs/sql-docs-powershell/blob/4c48bd1c26220ff873e612527853aeeef98777da/sqlserver-cmdlets/sqlps/vlatest/Convert-UrnToPath.md
ms.topic: reference
author: stevestein
ms.author: sstein
keywords: powershell, cmdlet
manager: jhubbard
open_to_public_contributors: true
ms.service: sql-server
---

# Convert-UrnToPath

## SYNOPSIS
Converts a SQL Server Management Object URN to a Windows PowerShell provider path.

## SYNTAX

```
Convert-UrnToPath -Urn <String> [<CommonParameters>]
```

## DESCRIPTION
The **Convert-UrnToPath** cmdlet converts a SQL Server Management Object Uniform Resource Name (URN) to a SQL Server provider path.
SQL Server Management Objects have a Urn property that returns a string indicating their location in the SQL Server object hierarchy.
If nodes in the Urn are SQL Server delimited identifiers with extended characters that are not supported in Windows PowerShell path nodes, the extended characters are encoded with their hexadecimal representation.
For example, a table name "Main:Table" is encoded as "Main%3ATable".

## EXAMPLES

### Example 1: Get a string containing the current path
```
PS C:\> Set-Location "SQLSERVER:\SQL\MyComputer\MyInstance\Databases\AdventureWorks2014"
PS SQLSERVER:\SQL\MyComputer\MyInstance\Databases\AdventureWorks2014> Convert-UrnToPath -Urn (Get-Item .).Urn.ToString()
SQLSERVER:\SQL\MyComputer\MyInstance\Databases\AdventureWorks2014
```

This command returns a string that contains the current path.
The example uses the ToString() function of the Urn property to return the Urn as a string.

### Example 2: Set the path location based on a URN
```
PS C:\> Set-Location (Convert-UrnToPath -Urn "Server[@Name='MyComputer']/Database[@Name='AdventureWorks']/Table[@Name='Address' and @Schema = 'Person']")
```

This command sets the path to the location specified in a SQL Server Management Object URN.

### Example 3: Get database paths
```
PS C:\> Set-Location "SQLSERVER:\SQL\MyComputer\DEFAULT\Databases"
PS SQLSERVER:\SQL\MyComputer\DEFAULT\Databases> ForEach ($Item in Get-ChildItem) { $Item.Urn.ToString() | Convert-UrnToPath }
SQLSERVER:\SQL\MyComputer\DEFAULT\Databases\AdventureWorks2014
```

This command returns an array of strings that contain the path to a database in the default instance.
The pipeline operator is used to pass the current node URN to **Convert-UrnToPath**.

## PARAMETERS

### -Urn
Specifies a SQL Server URN that identifies the location of an object in the SQL Server hierarchy.

```yaml
Type: String
Parameter Sets: (All)
Aliases: 

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### CommonParameters
This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable. For more information, see about_CommonParameters (http://go.microsoft.com/fwlink/?LinkID=113216).

## INPUTS

### String
Specifies a string that represents a SQL Server Management Object URN.

## OUTPUTS

### String
Specifies a string that represents a SQL Server PowerShell provider path.

## NOTES

## RELATED LINKS
