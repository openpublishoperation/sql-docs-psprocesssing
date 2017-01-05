---
external help file: Microsoft.SqlServer.Management.PSSnapins.dll-Help.xml
online version: 
schema: 2.0.0
ms.assetid: B8074299-ED33-4209-9B5E-6EA4A5E3E513
updated_at: 1/5/2017 8:57 AM
ms.date: 1/5/2017
content_git_url: https://github.com/MicrosoftDocs/sql-docs-powershell/blob/master/sqlserver-cmdlets/sqlserver-module/vlatest/Get-SqlColumnEncryptionKey.md
original_content_git_url: https://github.com/MicrosoftDocs/sql-docs-powershell/blob/master/sqlserver-cmdlets/sqlserver-module/vlatest/Get-SqlColumnEncryptionKey.md
gitcommit: https://github.com/MicrosoftDocs/sql-docs-powershell/blob/0d97835841eb5cfbe37d096037375a2e0c3eb87c/sqlserver-cmdlets/sqlserver-module/vlatest/Get-SqlColumnEncryptionKey.md
ms.topic: reference
author: stevestein
ms.author: sstein
keywords: powershell, cmdlet
manager: jhubbard
open_to_public_contributors: true
ms.service: sql-server
---

# Get-SqlColumnEncryptionKey

## SYNOPSIS
Gets all column encryption key objects defined in the database, or gets one column encryption key object with the specified name.

## SYNTAX

### ByObject
```
Get-SqlColumnEncryptionKey [[-Name] <String>] [-InputObject] <Database> [-Script]
 [-InformationAction <ActionPreference>] [-InformationVariable <String>] [<CommonParameters>]
```

### ByPath
```
Get-SqlColumnEncryptionKey [[-Name] <String>] [[-Path] <String>] [-Script]
 [-InformationAction <ActionPreference>] [-InformationVariable <String>] [<CommonParameters>]
```

## DESCRIPTION
The **Get-SqlColumnEncryptionKey** cmdlet returns a column encryption key object for each column encryption key in the target database.
If the name of the column encryption key is provided, the cmdlet returns one specific column encryption key object.

## EXAMPLES

### Example 1: Get all column encryption keys from a database
```
PS C:\> Get-SqlColumnEncryptionKey
```

This command gets all column encryption keys from the database.

### Example 2: Get a column encryption key from a specified
```
PS C:\> Get-SqlColumnEncryptionKey -Name "CEK1"
```

This command gets a column encryption key from the column encryption key object named CEK1.

## PARAMETERS

### -Name
Specifies the name of the column encryption key object.

```yaml
Type: String
Parameter Sets: (All)
Aliases: 

Required: False
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
Indicates that this cmdlet runs a script to get the SQL column encryption key value.

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

### SqlColumnEncryptionKey[] or SqlColumnEncryptionKey

## NOTES

## RELATED LINKS

[Configure Always Encrypted using PowerShell](https://msdn.microsoft.com/library/mt755926.aspx)

[New-SqlColumnEncryptionKey](xref:sqlserver-module/vlatest/New-SqlColumnEncryptionKey.md)

[Remove-SqlColumnEncryptionKey](xref:sqlserver-module/vlatest/Remove-SqlColumnEncryptionKey.md)
