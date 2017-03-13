---
external help file: Microsoft.SqlServer.Management.PSSnapins.dll-Help.xml
online version: 
schema: 2.0.0
ms.assetid: 3FC92A7F-BCB2-4418-9AB5-1C194226406B
updated_at: 3/13/2017 4:14 PM
ms.date: 3/13/2017
content_git_url: https://github.com/MicrosoftDocs/sql-docs-powershell/blob/master/sqlserver-cmdlets/sqlserver/vlatest/Set-SqlNetworkConfiguration.md
original_content_git_url: https://github.com/MicrosoftDocs/sql-docs-powershell/blob/master/sqlserver-cmdlets/sqlserver/vlatest/Set-SqlNetworkConfiguration.md
gitcommit: https://github.com/MicrosoftDocs/sql-docs-powershell/blob/6eefe64a0ce19459190f09768267a4c79f9a6af9/sqlserver-cmdlets/sqlserver/vlatest/Set-SqlNetworkConfiguration.md
ms.topic: reference
author: stevestein
ms.author: sstein
keywords: powershell, cmdlet
manager: jhubbard
open_to_public_contributors: True
ms.service: sql-server
---

# Set-SqlNetworkConfiguration

## SYNOPSIS
Sets the network configuration of the target instance of SQL Server.

## SYNTAX

### ByPath (Default)
```
Set-SqlNetworkConfiguration [-Protocol] <Protocols> [[-Port] <Int32>] [-Disable] [-ForceServiceRestart]
 [-NoServiceRestart] [-Path <String[]>] [-Credential] <PSCredential>
 [-AutomaticallyAcceptUntrustedCertificates] [-ManagementPublicPort <Int32>] [-RetryTimeout <Int32>]
 [-InformationAction <ActionPreference>] [-InformationVariable <String>] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

### ByObject
```
Set-SqlNetworkConfiguration [-Protocol] <Protocols> [[-Port] <Int32>] [-Disable] [-ForceServiceRestart]
 [-NoServiceRestart] -InputObject <Server[]> [-Credential] <PSCredential>
 [-AutomaticallyAcceptUntrustedCertificates] [-ManagementPublicPort <Int32>] [-RetryTimeout <Int32>]
 [-InformationAction <ActionPreference>] [-InformationVariable <String>] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

### ByName
```
Set-SqlNetworkConfiguration [-Protocol] <Protocols> [[-Port] <Int32>] [-Disable] [-ForceServiceRestart]
 [-NoServiceRestart] -ServerInstance <String[]> [-Credential] <PSCredential>
 [-AutomaticallyAcceptUntrustedCertificates] [-ManagementPublicPort <Int32>] [-RetryTimeout <Int32>]
 [-InformationAction <ActionPreference>] [-InformationVariable <String>] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

## DESCRIPTION
The **Set-SqlNetworkConfiguration** cmdlet sets the network configuration of the target instance of SQL Server.

SQL Server Cloud Adapter must be running and accessible on the machine that hosts the instance of SQL Server.

This cmdlet supports the following modes of operation:

- Specify the instance of the Windows PowerShell path. 
- Specify the server object. 
- Specify the **ServerInstance** object of the target instance of SQL Server.

## EXAMPLES

### Example 1: Set the network configuration of the target SQL Server
```
PS C:\> CD SQLSERVER:\SQL\Computer\Instance;
PS SQLSERVER:\SQL\Computer\Instance> Set-SqlNetworkConfiguration -Credential $credential -Protocol TCP -Port 1433-NoServiceRestart -AcceptSelfSignedCertificate;
```

The first command changes the directory to SQLSERVER:\SQL\Computer\Instance.
The second command sets the network configuration to accept TCP connections at port 1433 for the server instance named Computer\Instance.
The current working directory is used to determine the server instance where the operation occurs.
The SQL Server service is not restarted automatically.
The self-signed certificate of the target machine is automatically accepted without prompting the user.

### Example 2: Set the network configuration of the target SQL Server using the pipeline
```
PS C:\> Get-SqlInstance -Credential $Credential -MachineName "Computer006" | Set-SqlNetworkConfiguration -Credential $Credential -Protocol TCP -Disable -NoServiceRestart -AcceptSelfSignedCertificate;
```

This command gets all instances of SQL Server on the computer named Computer006 and disables TCP connections for each one of them.
The SQL Server service is not restarted automatically.
The self-signed certificate of the target machine is automatically accepted without prompting the user.

## PARAMETERS

### -Protocol
Specifies the network protocol that we want to configure on the target instance of SQL Server.

```yaml
Type: Protocols
Parameter Sets: (All)
Aliases: 

Required: True
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Port
Specifies the port to accept TCP connections.
To configure dynamic ports, this parameter should be set to zero.

```yaml
Type: Int32
Parameter Sets: (All)
Aliases: 

Required: False
Position: 2
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Disable
Indicates that this cmdlet disables the specified network protocol on the target instance of SQL Server.

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
Specifies the path, as an array, to the instance of SQL Server on which this cmdlet runs the operation.
If you do not specify a value for this parameter, the cmdlet uses the current working location.

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
This parameter is used when the ports of the target computer are not directly accessible but are exposed through endpoints.
This means that this cmdlet needs to connect to a different port.

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
Specifies an array of server objects of the target instance.

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
Specifies the name of an instance, as an array, of SQL Server that becomes the target of the operation.

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
