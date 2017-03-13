---
external help file: Microsoft.SqlServer.Management.PSSnapins.dll-Help.xml
online version: 
schema: 2.0.0
ms.assetid: F5C06E31-2E8A-493D-9825-9FA872458A58
updated_at: 3/13/2017 4:14 PM
ms.date: 3/13/2017
content_git_url: https://github.com/MicrosoftDocs/sql-docs-powershell/blob/master/sqlserver-cmdlets/sqlserver/vlatest/Set-SqlAuthenticationMode.md
original_content_git_url: https://github.com/MicrosoftDocs/sql-docs-powershell/blob/master/sqlserver-cmdlets/sqlserver/vlatest/Set-SqlAuthenticationMode.md
gitcommit: https://github.com/MicrosoftDocs/sql-docs-powershell/blob/6eefe64a0ce19459190f09768267a4c79f9a6af9/sqlserver-cmdlets/sqlserver/vlatest/Set-SqlAuthenticationMode.md
ms.topic: reference
author: stevestein
ms.author: sstein
keywords: powershell, cmdlet
manager: jhubbard
open_to_public_contributors: True
ms.service: sql-server
---

# Set-SqlAuthenticationMode

## SYNOPSIS
Configures the authentication mode of the target instance of SQL Server.

## SYNTAX

### ByPath (Default)
```
Set-SqlAuthenticationMode [-Mode] <ServerLoginMode> [[-SqlCredential] <PSCredential>] [-ForceServiceRestart]
 [-NoServiceRestart] [-Path <String[]>] [-Credential] <PSCredential>
 [-AutomaticallyAcceptUntrustedCertificates] [-ManagementPublicPort <Int32>] [-RetryTimeout <Int32>]
 [-InformationAction <ActionPreference>] [-InformationVariable <String>] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

### ByObject
```
Set-SqlAuthenticationMode [-Mode] <ServerLoginMode> [[-SqlCredential] <PSCredential>] [-ForceServiceRestart]
 [-NoServiceRestart] -InputObject <Server[]> [-Credential] <PSCredential>
 [-AutomaticallyAcceptUntrustedCertificates] [-ManagementPublicPort <Int32>] [-RetryTimeout <Int32>]
 [-InformationAction <ActionPreference>] [-InformationVariable <String>] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

### ByName
```
Set-SqlAuthenticationMode [-Mode] <ServerLoginMode> [[-SqlCredential] <PSCredential>] [-ForceServiceRestart]
 [-NoServiceRestart] -ServerInstance <String[]> [-Credential] <PSCredential>
 [-AutomaticallyAcceptUntrustedCertificates] [-ManagementPublicPort <Int32>] [-RetryTimeout <Int32>]
 [-InformationAction <ActionPreference>] [-InformationVariable <String>] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

## DESCRIPTION
The **Set-SqlAuthenticationMode** cmdlet configures the authentication mode of the target instance of SQL Server.

SQL ServerCloud Adapter must be running and accessible on the computer that hosts the instance of SQL Server.

This cmdlet supports the following modes of operation:

- Specify the instance Windows PowerShell path. 
- Specify the server object. 
- Specify the **ServerInstance** object of the target instance of SQL Server.

## EXAMPLES

### Example 1: Configure the SQL Server authentication mode
```
PS C:\> CD SQLSERVER:\SQL\Computer\Instance;
PS SQLSERVER:\SQL\Computer\Instance> Set-SqlAuthenticationMode -Credential $Credential -Mode Integrated -ForceServiceRestart -AcceptSelfSignedCertificate
```

The first command changes directory to the SQL Server instance SQLSERVER:\SQL\Computer\Instance.

The second command configures the authentication mode to Integrated for the server instance named Computer\Instance.
The current working directory is used to determine the server instance where the operation should occur.
The SQL Server service is automatically restarted, without prompting the user.
The self-signed certificate of the target machine is automatically accepted without prompting the user.

### Example 2: Configure the SQL Server authentication mode on all SQL Server instances
```
PS C:\> Get-SqlInstance -Credential $Credential -MachineName "Computer005" | Set-SqlAuthenticationMode -Credential $Credential -Mode Mixed -SqlCredential $sqlCredential -NoServiceRestart -AcceptSelfSignedCertificate
```

This command gets all instances of SQL Server on the computer named Computer005 and configures the authentication mode to Mixed, with the provided SQL credentials for each one of them.
The SQL Server service is not restarted automatically.
The self-signed certificate of the target machine is automatically accepted without prompting the user.

## PARAMETERS

### -Mode
Specifies the authentication mode that will be configured on the target instance of SQL Server.

The acceptable values for this parameter are:

- Normal
- Integrated
- Mixed
- Unknown

```yaml
Type: ServerLoginMode
Parameter Sets: (All)
Aliases: 

Required: True
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -SqlCredential
Specifies the administrator credentials that is created in the target instance of SQL Server if Mixed mode authentication is enabled.

```yaml
Type: PSCredential
Parameter Sets: (All)
Aliases: 

Required: False
Position: 2
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ForceServiceRestart
Indicates that this cmdlet forces the SQL Server service to restart, if necessary, without prompting the user.

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

### -NoServiceRestart
Indicates that this cmdlet prevents a restart of the SQL Server service without prompting the user.

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

### -Path
Specifies the path to the instance of SQL Server, as an array, on which this cmdlet runs the operation.
If you do not specify a value for this parameter, the cmdlet defaults to the current working location.

```yaml
Type: String[]
Parameter Sets: ByPath
Aliases: 

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Credential
Specifies a user account with Windows Administrator credentials on the target computer.

```yaml
Type: PSCredential
Parameter Sets: (All)
Aliases: 

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -AutomaticallyAcceptUntrustedCertificates
Indicates that this cmdlet automatically accepts untrusted certificates.

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

### -ManagementPublicPort
Specifies the public management port on the target computer.
This parameter should be used when the ports of the target computer are not directly accessible but are exposed through endpoints, which means that this cmdlet needs to connect to a different port.

SQL Server Cloud Adapter must be accessible by this port.

```yaml
Type: Int32
Parameter Sets: (All)
Aliases: 

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -RetryTimeout
Specifies the time period to retry the command on the target sever.
After the timeout expires, no retry will be attempted.

```yaml
Type: Int32
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
Specifies the server object, as an array, of the target instance.

```yaml
Type: Server[]
Parameter Sets: ByObject
Aliases: 

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -ServerInstance
Specifies, as a string array, the name of an instance of SQL Server that becomes the target of the operation.

```yaml
Type: String[]
Parameter Sets: ByName
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

## OUTPUTS

## NOTES

## RELATED LINKS

[SQL Server Cmdlets](xref:sqlserver/vlatest/SqlServer.md)
