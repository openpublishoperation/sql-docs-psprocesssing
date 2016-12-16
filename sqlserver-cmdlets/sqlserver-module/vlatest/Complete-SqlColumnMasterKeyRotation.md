---
external help file: Microsoft.SqlServer.Management.PSSnapins.dll-Help.xml
online version: 
schema: 2.0.0
ms.assetid: 371329D7-C412-4EF3-A2A2-8B3D7BF47E0F
updated_at: 12/13/2016 8:09 PM
ms.date: 12/13/2016
content_git_url: https://github.com/MicrosoftDocs/sql-docs-powershell/blob/live/sqlserver-cmdlets/sqlserver-module/vlatest/Complete-SqlColumnMasterKeyRotation.md
original_content_git_url: https://github.com/MicrosoftDocs/sql-docs-powershell/blob/live/sqlserver-cmdlets/sqlserver-module/vlatest/Complete-SqlColumnMasterKeyRotation.md
gitcommit: https://github.com/MicrosoftDocs/sql-docs-powershell/blob/f97823fbeb2d71358573a8e4b5c2c322a3a5c138/sqlserver-cmdlets/sqlserver-module/vlatest/Complete-SqlColumnMasterKeyRotation.md
ms.topic: reference
author: stevestein
ms.author: sstein
keywords: powershell, cmdlet
manager: jhubbard
open_to_public_contributors: true
ms.service: sql-server
---

# Complete-SqlColumnMasterKeyRotation

## SYNOPSIS
Completes the rotation of a column master key.

## SYNTAX

### ByObject
```
Complete-SqlColumnMasterKeyRotation -SourceColumnMasterKeyName <String> [-InputObject] <Database> [-Script]
 [-InformationAction <ActionPreference>] [-InformationVariable <String>] [<CommonParameters>]
```

### ByPath
```
Complete-SqlColumnMasterKeyRotation -SourceColumnMasterKeyName <String> [[-Path] <String>] [-Script]
 [-InformationAction <ActionPreference>] [-InformationVariable <String>] [<CommonParameters>]
```

## DESCRIPTION
The **Complete-SqlColumnMasterKeyRotation** cmdlet completes the process of replacing an existing column master key with a new, target, column master key for the Always Encrypted feature.
The cmdlet gets all column encryption key objects containing encrypted key values that are encrypted with the specified source column master key.
The cmdlet then updates each column encryption key object to remove the entry for an encrypted value that was produced using the specified column master key.
As a result, each impacted column encryption key object will have only one encrypted value entry, produced using the column master key that is the target of the rotation.

## EXAMPLES

### Example 1: Complete the process of rotating the column master key
```
PS C:\>Cleanup-SqlColumnMasterKey -SourceColumnMasterKeyName "CMK1"
```

This command completes the process of rotating the column master key named CMK1.

## PARAMETERS

### -SourceColumnMasterKeyName
Specifies the name of the source column master key.

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

### -InputObject
Specifies the SQL database object for which this cmdlet runs the operation.

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
Indicates that this cmdlet runs a script to complete the rotation of a column master key.

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
Specifies the path to the SQL database, for which this cmdlet runs the operation.
If you do not specify a value for the parameter, the cmdlet uses the current working location.

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

## NOTES

## RELATED LINKS

[Configure Always Encrypted using PowerShell](https://msdn.microsoft.com/library/mt755926.aspx)

[Invoke-SqlColumnMasterKeyRotation](xref:sqlserver-module/vlatest/Invoke-SqlColumnMasterKeyRotation.md)


