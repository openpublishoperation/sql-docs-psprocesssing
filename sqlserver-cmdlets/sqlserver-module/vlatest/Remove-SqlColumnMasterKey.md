---
external help file: Microsoft.SqlServer.Management.PSSnapins.dll-Help.xml
online version: 
schema: 2.0.0
ms.assetid: 736238C8-995A-4D62-8233-BA542A35715A
updated_at: 12/13/2016 8:09 PM
ms.date: 12/13/2016
content_git_url: https://github.com/MicrosoftDocs/sql-docs-powershell/blob/live/sqlserver-cmdlets/sqlserver-module/vlatest/Remove-SqlColumnMasterKey.md
original_content_git_url: https://github.com/MicrosoftDocs/sql-docs-powershell/blob/live/sqlserver-cmdlets/sqlserver-module/vlatest/Remove-SqlColumnMasterKey.md
gitcommit: https://github.com/MicrosoftDocs/sql-docs-powershell/blob/f97823fbeb2d71358573a8e4b5c2c322a3a5c138/sqlserver-cmdlets/sqlserver-module/vlatest/Remove-SqlColumnMasterKey.md
ms.topic: reference
author: stevestein
ms.author: sstein
keywords: powershell, cmdlet
manager: jhubbard
open_to_public_contributors: true
ms.service: sql-server
---

# Remove-SqlColumnMasterKey

## SYNOPSIS
Removes the column master key object from the database.

## SYNTAX

### ByObject
```
Remove-SqlColumnMasterKey [-Name] <String> [-InputObject] <Database> [-Script]
 [-InformationAction <ActionPreference>] [-InformationVariable <String>] [<CommonParameters>]
```

### ByPath
```
Remove-SqlColumnMasterKey [-Name] <String> [[-Path] <String>] [-Script] [-InformationAction <ActionPreference>]
 [-InformationVariable <String>] [<CommonParameters>]
```

## DESCRIPTION
The **Remove-SqlColumnMasterKey** cmdlet removes the column master key object with the specified name from the database.

## EXAMPLES

### Example 1: Remove a column master key object from the database
```
PS C:\>Remove-SqlColumnMasterKey -Name "CMK1"
```

This command removes the column master key object named CMK1 from the database.

## PARAMETERS

### -Name
Specifies the name of the column master key object that this cmdlet removes.

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
Specifies the SQL database object, for which this cmdlet performs the operation.

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

## NOTES

## RELATED LINKS

[Configure Always Encrypted using PowerShell](https://msdn.microsoft.com/library/mt755926.aspx)

[Get-SqlColumnMasterKey](xref:sqlserver-module/vlatest/Get-SqlColumnMasterKey.md)

[New-SqlColumnMasterKey](xref:sqlserver-module/vlatest/New-SqlColumnMasterKey.md)


