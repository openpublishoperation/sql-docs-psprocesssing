---
external help file: Microsoft.SqlServer.Management.PSSnapins.dll-Help.xml
online version: 
schema: 2.0.0
ms.assetid: 89D831A6-CC02-4BFD-9E86-0BCCCAC0BE54
updated_at: 1/5/2017 8:57 AM
ms.date: 1/5/2017
content_git_url: https://github.com/MicrosoftDocs/sql-docs-powershell/blob/master/sqlserver-cmdlets/sqlserver-module/vlatest/Add-SqlFirewallRule.md
original_content_git_url: https://github.com/MicrosoftDocs/sql-docs-powershell/blob/master/sqlserver-cmdlets/sqlserver-module/vlatest/Add-SqlFirewallRule.md
gitcommit: https://github.com/MicrosoftDocs/sql-docs-powershell/blob/0d97835841eb5cfbe37d096037375a2e0c3eb87c/sqlserver-cmdlets/sqlserver-module/vlatest/Add-SqlFirewallRule.md
ms.topic: reference
author: stevestein
ms.author: sstein
keywords: powershell, cmdlet
manager: jhubbard
open_to_public_contributors: true
ms.service: sql-server
---

# Add-SqlFirewallRule

## SYNOPSIS
Adds a Windows Firewall rule to allow connections to a specific instance of SQL Server.

## SYNTAX

### ByPath (Default)
```
Add-SqlFirewallRule [-Path <String[]>] [-Credential] <PSCredential> [-AutomaticallyAcceptUntrustedCertificates]
 [-ManagementPublicPort <Int32>] [-RetryTimeout <Int32>] [-InformationAction <ActionPreference>]
 [-InformationVariable <String>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### ByObject
```
Add-SqlFirewallRule -InputObject <Server[]> [-Credential] <PSCredential>
 [-AutomaticallyAcceptUntrustedCertificates] [-ManagementPublicPort <Int32>] [-RetryTimeout <Int32>]
 [-InformationAction <ActionPreference>] [-InformationVariable <String>] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

### ByName
```
Add-SqlFirewallRule -ServerInstance <String[]> [-Credential] <PSCredential>
 [-AutomaticallyAcceptUntrustedCertificates] [-ManagementPublicPort <Int32>] [-RetryTimeout <Int32>]
 [-InformationAction <ActionPreference>] [-InformationVariable <String>] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

## DESCRIPTION
The **Add-SqlFirewallRule** cmdlet adds a Windows Firewall rule to allow connections for the specified instance of SQL Server.

The SQL Server Cloud Adapter must be running and accessible on the computer that hosts the instance of SQL Server.

This cmdlet supports the following modes of operation:

- Specify the instance Windows PowerShell path. 
- Specify the server object. 
- Specify the server instance of the target instance of SQL Server.

## EXAMPLES

### Example 1: Add a Windows Firewall rule on the local computer
```
PS C:\> CD SQLSERVER:\SQL\Computer\Instance;
PS SQLSERVER:\SQL\Computer\Instance> Add-SqlFirewallRule -Credential $Credential -AcceptSelfSignedCertificate;
```

The first command changes directory to the SQL Server computer instance.

The second command adds a Windows Firewall rule on the local computer to allow connections to the instance of SQL Server.
The current working directory is used to determine the server instance where the operation should occur.
The self-signed certificate of the target machine is automatically accepted without prompting the user.

### Example 2: Add a Windows Firewall rule on the local computer through a pipe
```
PS C:\> Get-SqlInstance -Credential $Credential -MachineName "Computer001" | Add-SqlFirewallRule -Credential $Credential -AcceptSelfSignedCertificate;
```

This command gets the SQL Server instance based on the credentials stored in the variable named $Credentials.
The command then pipes the SQL Server instances of SQL Server on the computer named Computer001.
The command then adds Windows Firewall rules to allow connections for each one of the instances.
The self-signed certificate of the target machine is automatically accepted without prompting the user.

## PARAMETERS

### -Path
Specifies the path to the instance of SQL Server on which this cmdlet runs the operation.
If this parameter is not specified, the value of this parameter defaults to the current working location.

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
Specifies a **PSCredential** object for the connection to SQL Server.
To obtain a credential object, use the **Get-Credential** cmdlet.
For more information, type `Get-Help Get-Credential`.

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
Specifies the public management port on the target machine.
This parameter is used when the ports of the target machine are not directly accessible but are exposed through endpoints, which means that they need to be connected to a different port.

The SQL Server Cloud Adapter must be accessible by this port.

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
Specifies the time period to retry the command on the target server.
After the timeout expires, no retry is attempted.

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
Specifies the server object of the target instance of SQL Server.

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
Specifies the name of an instance of SQL Server, as an array, that becomes the target of the operation.

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

[Remove-SqlFirewallRule](xref:sqlserver-module/vlatest/Remove-SqlFirewallRule.md)
