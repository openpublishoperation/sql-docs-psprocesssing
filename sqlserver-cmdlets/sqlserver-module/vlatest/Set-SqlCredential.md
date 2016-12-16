---
external help file: Microsoft.SqlServer.Management.PSSnapins.dll-Help.xml
online version: 
schema: 2.0.0
ms.assetid: F7BCEF94-2FF3-4B9C-AC8F-84977532F668
updated_at: 12/13/2016 8:09 PM
ms.date: 12/13/2016
content_git_url: https://github.com/MicrosoftDocs/sql-docs-powershell/blob/live/sqlserver-cmdlets/sqlserver-module/vlatest/Set-SqlCredential.md
original_content_git_url: https://github.com/MicrosoftDocs/sql-docs-powershell/blob/live/sqlserver-cmdlets/sqlserver-module/vlatest/Set-SqlCredential.md
gitcommit: https://github.com/MicrosoftDocs/sql-docs-powershell/blob/f97823fbeb2d71358573a8e4b5c2c322a3a5c138/sqlserver-cmdlets/sqlserver-module/vlatest/Set-SqlCredential.md
ms.topic: reference
author: stevestein
ms.author: sstein
keywords: powershell, cmdlet
manager: jhubbard
open_to_public_contributors: true
ms.service: sql-server
---

# Set-SqlCredential

## SYNOPSIS
Sets the properties for the SQL Credential object.

## SYNTAX

### ByPath (Default)
```
Set-SqlCredential [-Identity] <String> [[-Secret] <SecureString>] [[-Path] <String>] [-Script]
 [-InformationAction <ActionPreference>] [-InformationVariable <String>] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

### ByObject
```
Set-SqlCredential [-Identity] <String> [[-Secret] <SecureString>] [-InputObject] <Credential> [-Script]
 [-InformationAction <ActionPreference>] [-InformationVariable <String>] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

## DESCRIPTION
The **Set-SqlCredential** cmdlet sets the Identity and password properties for a SQL Credential object using this cmdlet.
This cmdlet supports the two following modes of operation:

- Specify the path or location of the credential including the credential name that uses the *Path* parameter. 
- Pass a **Smo.Credential** object to the object that uses the *InputObject* parameter.

## EXAMPLES

### Example 1: Set the identity of a SQL credential object
```
PS C:\>Set-SqlCredential -Path SQLSERVER:\SQL\Computer\Instance\Credentials\MySqlCredential -Identity "MyStorageAccount"
```

This command sets the identity of MySqlCredential to MyStorageAccount by specifying the path of the SQL Credential.

### Example 2: Set the identity of a SQL credential object using the pipeline
```
PS C:\>$Cred = Get-SqlCredential -Name "MySqlCredential"
PS C:\> $Cred | Set-SqlCredential -Identity "MyStorageAccount"
```

The first command gets the credential object from the **Get-Credential** cmdlet and stores the result in the variable named $Cred.

The second command pipes the result stored in the $Cred variable to the **Set-SqlCredential** cmdlet to set the identity of mySqlCrendential to MyStorageAccount.

### Example 3: Set the identity of a SQL credential object prompting the user
```
PS C:\>$Secret = Read-Host "Please enter the storage account access key"
PS C:\>  Set-SqlCredential -Identity "MyStorageAccount" -Secret $Secret
```

The first command prompts for the storage access key information and stores the result in the variable named $Secret.

The second command uses the **Set-SqlCredential** cmdlet to set the value stored in the variable named $Secret with the input value.

## PARAMETERS

### -Identity
Specifies the user or account name for the resource SQL Server needs to authenticate to.
For Windows Azure storage service, this is the name of the Windows Azure storage account.

```yaml
Type: String
Parameter Sets: (All)
Aliases: 

Required: True
Position: 2
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Secret
Specifies the password for the user or account.
For Windows Azure storage service, this is the access key value for the Windows Azure storage account.

```yaml
Type: SecureString
Parameter Sets: (All)
Aliases: 

Required: False
Position: 3
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Path
Specifies the path to the credential on which this cmdlet performs this operation.
For instance, SQLSERVER:\SQL\Computer\Instance\Credentials\Credential.

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
The cmdlet is not run.Shows what would happen if the cmdlet runs.
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
Prompts you for confirmation before running the cmdlet.Prompts you for confirmation before running the cmdlet.

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
Specifies an input **Credential** object.
To get this object, use the Get-SqlCredential cmdlet.

```yaml
Type: Credential
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


