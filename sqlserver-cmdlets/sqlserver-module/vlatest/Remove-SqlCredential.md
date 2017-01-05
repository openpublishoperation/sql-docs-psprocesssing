---
external help file: Microsoft.SqlServer.Management.PSSnapins.dll-Help.xml
online version: 
schema: 2.0.0
ms.assetid: 175BEB2E-1087-48E6-AD60-B80CDE2F84DF
updated_at: 1/5/2017 8:57 AM
ms.date: 1/5/2017
content_git_url: https://github.com/MicrosoftDocs/sql-docs-powershell/blob/live/sqlserver-cmdlets/sqlserver-module/vlatest/Remove-SqlCredential.md
original_content_git_url: https://github.com/MicrosoftDocs/sql-docs-powershell/blob/live/sqlserver-cmdlets/sqlserver-module/vlatest/Remove-SqlCredential.md
gitcommit: https://github.com/MicrosoftDocs/sql-docs-powershell/blob/0d97835841eb5cfbe37d096037375a2e0c3eb87c/sqlserver-cmdlets/sqlserver-module/vlatest/Remove-SqlCredential.md
ms.topic: reference
author: stevestein
ms.author: sstein
keywords: powershell, cmdlet
manager: jhubbard
open_to_public_contributors: true
ms.service: sql-server
---

# Remove-SqlCredential

## SYNOPSIS
Removes the SQL credential object.

## SYNTAX

### ByPath (Default)
```
Remove-SqlCredential [-Path] <String[]> [-Script] [-InformationAction <ActionPreference>]
 [-InformationVariable <String>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### ByObject
```
Remove-SqlCredential [-InputObject] <Credential[]> [-Script] [-InformationAction <ActionPreference>]
 [-InformationVariable <String>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## DESCRIPTION
The **Remove-SqlCredential** cmdlet removes a SQL Server credential object.
This cmdlet supports the following two modes of operation:

- Specifies the path or location of the credential including the credential name using the *Path* parameter.
- Passes a **Smo.Credential** object to the object using the *InputObject* parameter.

## EXAMPLES

### Example 1: Remove a SQL credential
```
PS C:\> emove-SqlCredential -Path "SQLSERVER:\SQL\Computer\Instance\Credentials\MySqlCredential"
```

This command removes the SQL credential named MySqlCredential using the path specified in the *Path* parameter.

### Example 2: Remove a SQL credential through input pipe
```
PS C:\> $Cred = Get-SqlCredential -Name MySqlCredential $Cred | Remove-SqlCredential
```

The command gets the credential object from the **Get-Credential** cmdlet and then uses the pipeline to pass it to the **Remove-SqlCredential** cmdlet to remove the SQL credential named MySqlCredential.

## PARAMETERS

### -Path
Specifies the path of the credential, as an array, on which this cmdlet performs this operation.
For instance, SQLSERVER:\SQL\Computer\Instance\Credentials\Credential.

```yaml
Type: String[]
Parameter Sets: ByPath
Aliases: 

Required: True
Position: 1
Default value: None
Accept pipeline input: False
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

### -WhatIf
Shows what would happen if the cmdlet runs.
The cmdlet is not run.

```yaml
Type: SwitchParameter
Parameter Sets: (All)
Aliases: wi

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -Confirm
Prompts you for confirmation before running the cmdlet.

```yaml
Type: SwitchParameter
Parameter Sets: (All)
Aliases: cf

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -InputObject
Specifies an input credential object, as an array.
You can use the **Get-SqlCredential** to get the object.

```yaml
Type: Credential[]
Parameter Sets: ByObject
Aliases: 

Required: True
Position: 1
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### CommonParameters
This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable. For more information, see about_CommonParameters (http://go.microsoft.com/fwlink/?LinkID=113216).

## INPUTS

## OUTPUTS

## NOTES

## RELATED LINKS

[Get-SqlCredential](xref:sqlserver-module/vlatest/Get-SqlCredential.md)

[New-SqlCredential](xref:sqlserver-module/vlatest/New-SqlCredential.md)

[Set-SqlCredential](xref:sqlserver-module/vlatest/Set-SqlCredential.md)
