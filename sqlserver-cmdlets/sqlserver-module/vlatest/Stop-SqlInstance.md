---
external help file: Microsoft.SqlServer.Management.PSSnapins.dll-Help.xml
online version: 
schema: 2.0.0
ms.assetid: F0D82BA4-E3A3-48E6-B40F-A713C3810FF2
updated_at: 12/13/2016 8:09 PM
ms.date: 12/13/2016
content_git_url: https://github.com/MicrosoftDocs/sql-docs-powershell/blob/live/sqlserver-cmdlets/sqlserver-module/vlatest/Stop-SqlInstance.md
original_content_git_url: https://github.com/MicrosoftDocs/sql-docs-powershell/blob/live/sqlserver-cmdlets/sqlserver-module/vlatest/Stop-SqlInstance.md
gitcommit: https://github.com/MicrosoftDocs/sql-docs-powershell/blob/f97823fbeb2d71358573a8e4b5c2c322a3a5c138/sqlserver-cmdlets/sqlserver-module/vlatest/Stop-SqlInstance.md
ms.topic: reference
author: stevestein
ms.author: sstein
keywords: powershell, cmdlet
manager: jhubbard
open_to_public_contributors: true
ms.service: sql-server
---

# Stop-SqlInstance

## SYNOPSIS
Stops the specified instance of SQL Server.

## SYNTAX

### ByPath (Default)
```
Stop-SqlInstance [-Path <String[]>] [-Credential] <PSCredential> [-AutomaticallyAcceptUntrustedCertificates]
 [-ManagementPublicPort <Int32>] [-RetryTimeout <Int32>] [-InformationAction <ActionPreference>]
 [-InformationVariable <String>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### ByObject
```
Stop-SqlInstance -InputObject <Server[]> [-Credential] <PSCredential>
 [-AutomaticallyAcceptUntrustedCertificates] [-ManagementPublicPort <Int32>] [-RetryTimeout <Int32>]
 [-InformationAction <ActionPreference>] [-InformationVariable <String>] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

### ByName
```
Stop-SqlInstance -ServerInstance <String[]> [-Credential] <PSCredential>
 [-AutomaticallyAcceptUntrustedCertificates] [-ManagementPublicPort <Int32>] [-RetryTimeout <Int32>]
 [-InformationAction <ActionPreference>] [-InformationVariable <String>] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

## DESCRIPTION
The **Stop-SqlInstance** cmdlet stops the specified instance of SQL Server.

SQL Server Cloud Adapter must be running and accessible on the computer that hosts the instance of SQL Server.

This cmdlet supports the following modes of operation:

- Specify the instance Windows PowerShell path.
- Specify the server object.
- Specify the **ServerInstance** object of the target instance of SQL Server.

## EXAMPLES

### Example 1: Stop an instance of SQL Server
```
PS C:\>CD SQLSERVER:\SQL\Computer\Instance;
PS SQLSERVER:\SQL\Computer\Instance> Stop-SqlInstance -Credential $Credential -AcceptSelfSignedCertificate;
```

The first command changes the working directory to SQLSERVER:\SQL\Computer\Instance.

The second commands stops the server instance Computer\Instance.
The current working directory is used to determine the server instance where the operation should occur.
The self-signed certificate of the target computer is automatically accepted without prompting the user.

### Example 2: Stop all instances of SQL Server on the specified computer
```
PS C:\>Get-SqlInstance -Credential $Credential -MachineName "Computer006" | Stop-SqlInstance -Credential $Credential -AcceptSelfSignedCertificate;
```

This command retrieves all instances of SQL Server on the machine named Computer006 and stops all the instances.
The self-signed certificate of the target computer is automatically accepted without prompting the user.

## PARAMETERS

### -Path
Specifies the path to the instance of SQL Server, as a string array, on which this cmdlet runs the operation.
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
Specifies the time period to retry the command on the target server.
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
Specifies the name of an instance of SQL Server, as a string array, that becomes the target of the operation.

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

[Get-SqlInstance](xref:sqlserver-module/vlatest/Get-SqlInstance.md)

[Start-SqlInstance](xref:sqlserver-module/vlatest/Start-SqlInstance.md)


