---
external help file: Microsoft.SqlServer.Management.PSSnapins.dll-Help.xml
online version: 
schema: 2.0.0
ms.assetid: 9136A0F5-E4EC-424F-874C-D317BA49CACB
updated_at: 12/13/2016 8:09 PM
ms.date: 12/13/2016
content_git_url: https://github.com/MicrosoftDocs/sql-docs-powershell/blob/live/sqlserver-cmdlets/sqlserver-module/vlatest/Get-SqlInstance.md
original_content_git_url: https://github.com/MicrosoftDocs/sql-docs-powershell/blob/live/sqlserver-cmdlets/sqlserver-module/vlatest/Get-SqlInstance.md
gitcommit: https://github.com/MicrosoftDocs/sql-docs-powershell/blob/f97823fbeb2d71358573a8e4b5c2c322a3a5c138/sqlserver-cmdlets/sqlserver-module/vlatest/Get-SqlInstance.md
ms.topic: reference
author: stevestein
ms.author: sstein
keywords: powershell, cmdlet
manager: jhubbard
open_to_public_contributors: true
ms.service: sql-server
---

# Get-SqlInstance

## SYNOPSIS
Gets a SQL Instance object for each instance of SQL Server that is present on the target computer.

## SYNTAX

```
Get-SqlInstance [-MachineName] <String[]> [[-Name] <String>] [-Credential] <PSCredential>
 [-AutomaticallyAcceptUntrustedCertificates] [-ManagementPublicPort <Int32>] [-RetryTimeout <Int32>]
 [-InformationAction <ActionPreference>] [-InformationVariable <String>] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

## DESCRIPTION
The **Get-SqlInstance** cmdlet gets a SQL Instance object for each instance of SQL Server that is present on the target computer.
If the name of the instance of SQL Server is provided, the cmdlet will only get this specific instance of SQL Server.

You must ensure that you run SQL Server Cloud Adapter on the computer that hosts the instance of SQL Server.

## EXAMPLES

### Example 1: Get an SQL Server instance on a computer
```
PS C:\>Get-SqlInstance -Credential $Credential -MachineName "Computer002" -Name "InstanceName" -AcceptSelfSignedCertificate;
```

This command gets the SQL Server instance named InstanceName on the computer named Computer002.
The self-signed certificate of the target machine will be automatically accepted without prompting the user.

### Example 2: Get all instances of SQL Server on a computer
```
PS C:\>Get-SqlInstance -Credential $Credential -MachineName "Computer005" -AcceptSelfSignedCertificate;
```

This command gets all instances of SQL Server on the computer named Computer005.
The self-signed certificate of the target machine will be automatically accepted without prompting the user.

## PARAMETERS

### -MachineName
Specifies the name, as a string array, of the target computer.

```yaml
Type: String[]
Parameter Sets: (All)
Aliases: 

Required: True
Position: 1
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -Name
Specifies the name of the instance of SQL Server, when you want to retrieve a specific instance of SQL Serveron the target machine.

```yaml
Type: String
Parameter Sets: (All)
Aliases: 

Required: False
Position: 2
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Credential
Specifies a **PSCredential** object for the connection to the SQL Server.
To obtain a credential object, use the Get-Credential cmdlet.
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
Specifies the public management port on the target computer.
This parameter should be used when the ports of the target machine are not directly accessible but are exposed through endpoints, which means that we need to connect to a different port.

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

### CommonParameters
This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable. For more information, see about_CommonParameters (http://go.microsoft.com/fwlink/?LinkID=113216).

## INPUTS

## OUTPUTS

## NOTES

## RELATED LINKS

[Start-SqlInstance](xref:sqlserver-module/vlatest/Start-SqlInstance.md)

[Stop-SqlInstance](xref:sqlserver-module/vlatest/Stop-SqlInstance.md)


