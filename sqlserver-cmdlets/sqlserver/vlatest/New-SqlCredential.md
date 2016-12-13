---
external help file: Microsoft.SqlServer.Management.PSSnapins.dll-Help.xml
online version: 
schema: 2.0.0
ms.assetid: 9A498878-903C-44D7-A0BD-6837BEED7738
updated_at: 12/8/2016 7:20 PM
ms.date: 12/8/2016
content_git_url: https://github.com/MicrosoftDocs/sql-docs-powershell/blob/master/sqlserver-cmdlets/sqlserver/vlatest/New-SqlCredential.md
original_content_git_url: https://github.com/MicrosoftDocs/sql-docs-powershell/blob/master/sqlserver-cmdlets/sqlserver/vlatest/New-SqlCredential.md
gitcommit: https://github.com/MicrosoftDocs/sql-docs-powershell/blob/b925b18b49186ab91cfeb5201e061d569d0eeae2/sqlserver-cmdlets/sqlserver/vlatest/New-SqlCredential.md
ms.topic: reference
author: stevestein
ms.author: sstein
keywords: powershell, cmdlet
manager: jhubbard
open_to_public_contributors: true
ms.service: sql-server
---

# New-SqlCredential

## SYNOPSIS
Creates a SQL Server credential object.

## SYNTAX

### ByPath (Default)
```
New-SqlCredential -Identity <String> [-Secret <SecureString>] [-ProviderName <String>] [-Name] <String>
 [[-Path] <String>] [-Script] [-InformationAction <ActionPreference>] [-InformationVariable <String>] [-WhatIf]
 [-Confirm] [<CommonParameters>]
```

### ByObject
```
New-SqlCredential -Identity <String> [-Secret <SecureString>] [-ProviderName <String>] [-Name] <String>
 [-InputObject] <Server> [-Script] [-InformationAction <ActionPreference>] [-InformationVariable <String>]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

## DESCRIPTION
The **New-SqlCredential** cmdlet creates a new SQL Server credential object.
A SQL Server credential object is used to store authentication information.
The SQL Server credential is required when backing up to or restoring from the Windows Azure storage service, and is used to store the Windows Azure storage account name and access key information.

## EXAMPLES

### Example 1: Create a SQL credential for the current instance of SQL Server
```
PS C:\>cd SQLServer:\SQL\Computer\Instance
PS SQLServer:\SQL\Computer\Instance> New-SqlCredential -Name "MySqlCredential" -Identity "MyWindowsAzureStorageAccount" -Secret "P4ssw0rd"
```

The first command changes the directory to SQLServer:\SQL\Computer\Instance.

The second command creates a SQL credential named MySqlCredential in the current instance of SQL Server.

### Example 2: Create a SQL credential for all instances of SQL Server
```
PS C:\>cd SQLServer:\SQL\Computer\Instance
PS SQLServer:\SQL\Computer\Instance> $SecureString = ConvertTo-SecureString "P4ssw0rd" -AsPlainText -Force
PS SQLServer:\SQL\Computer\Instance> $Instances = Get-ChildItem
PS SQLServer:\SQL\Computer\Instance> $Instances | New-SqlCredential -Name "MySqlCredential" -Identity "MyWindowsAzureStorageAccount" -Secret $SecureString
```

The first command changes the directory to SQLServer:\SQL\Computer\Instance.

The second command converts the supplied password to a secured string as plaintext and stores the result in the variable named $SecureString.

The third command gets the list of SQL Server instances and stores those instances in the variable named $Instances.

The forth command uses the pipeline to pass the instances to the **New-SqlCredential** to create a SQL Credential named MySqlCredential on all the instances of SQL Server.

## PARAMETERS

### -Identity
Specifies the name of user or account.
For Windows Azure storage service authentication, this is the name of the Windows Azure storage account.

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

### -Secret
Specifies the password for the user or account.
For Windows Azure storage service authentication, this is the storage account access key value.

```yaml
Type: SecureString
Parameter Sets: (All)
Aliases: 

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ProviderName
Specifies the cryptographic provider name for the Enterprise Key Management Provider (EKM).

```yaml
Type: String
Parameter Sets: (All)
Aliases: 

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Name
Specifies the name of the credential.

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

### -Path
Specifies the path of the instance of SQL Server for which this cmdlet runs the operation.
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
Specifies the **Server** object where the credential should be created.

```yaml
Type: Server
Parameter Sets: ByObject
Aliases: 

Required: True
Position: 2
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

[Get-SqlCredential](xref:sqlserver/vlatest/Get-SqlCredential.md)

[Remove-SqlCredential](xref:sqlserver/vlatest/Remove-SqlCredential.md)

[Set-SqlCredential](xref:sqlserver/vlatest/Set-SqlCredential.md)


