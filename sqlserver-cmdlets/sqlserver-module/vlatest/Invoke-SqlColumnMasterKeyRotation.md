---
external help file: Microsoft.SqlServer.Management.PSSnapins.dll-Help.xml
online version: 
schema: 2.0.0
ms.assetid: A61D60F7-B821-4C18-92A4-E52CD86B1AFA
updated_at: 1/5/2017 8:57 AM
ms.date: 1/5/2017
content_git_url: https://github.com/MicrosoftDocs/sql-docs-powershell/blob/master/sqlserver-cmdlets/sqlserver-module/vlatest/Invoke-SqlColumnMasterKeyRotation.md
original_content_git_url: https://github.com/MicrosoftDocs/sql-docs-powershell/blob/master/sqlserver-cmdlets/sqlserver-module/vlatest/Invoke-SqlColumnMasterKeyRotation.md
gitcommit: https://github.com/MicrosoftDocs/sql-docs-powershell/blob/0d97835841eb5cfbe37d096037375a2e0c3eb87c/sqlserver-cmdlets/sqlserver-module/vlatest/Invoke-SqlColumnMasterKeyRotation.md
ms.topic: reference
author: stevestein
ms.author: sstein
keywords: powershell, cmdlet
manager: jhubbard
open_to_public_contributors: true
ms.service: sql-server
---

# Invoke-SqlColumnMasterKeyRotation

## SYNOPSIS
Initiates the rotation of a column master key.

## SYNTAX

### ByObject
```
Invoke-SqlColumnMasterKeyRotation -SourceColumnMasterKeyName <String> -TargetColumnMasterKeyName <String>
 [-InputObject] <Database> [-Script] [-InformationAction <ActionPreference>] [-InformationVariable <String>]
 [<CommonParameters>]
```

### ByPath
```
Invoke-SqlColumnMasterKeyRotation -SourceColumnMasterKeyName <String> -TargetColumnMasterKeyName <String>
 [[-Path] <String>] [-Script] [-InformationAction <ActionPreference>] [-InformationVariable <String>]
 [<CommonParameters>]
```

## DESCRIPTION
The **Invoke-SqlColumnMasterKeyRotation** cmdlet replaces an existing source column master key with a new target column master key for the Always Encrypted feature.
The cmdlet retrieves all column encryption key objects that contain encrypted key values that are encrypted with the specified source column master key.
Then, the cmdlet decrypts the current encrypted values, re-encrypts the resulting plaintext values with the target column master key, and then updates the impacted column encryption key objects to add the new encrypted values.
As a result, each impacted column encryption key contains two encrypted values: One produced using the current source column master key and another, produced using the target column master key.

## EXAMPLES

### Example 1: Initiate the process of rotating the column master key
```
PS C:\> Invoke-SqlColumnMasterKey -SourceColumnMasterKeyName "CMK1" -TargetColumnMasterKeyName "CMK2"
```

This command initiates the process of rotating the column master key named CMK1, and replacing it with the column master key named CMK2.

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

### -TargetColumnMasterKeyName
Specifies the name of the target column master key.

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
Indicates that this cmdlet runs a Transact-SQL script that performs the task.

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

## NOTES

## RELATED LINKS

[Configure Always Encrypted using PowerShell](https://msdn.microsoft.com/library/mt755926.aspx)

[Complete-SqlColumnMasterKeyRotation](xref:sqlserver-module/vlatest/Complete-SqlColumnMasterKeyRotation.md)
