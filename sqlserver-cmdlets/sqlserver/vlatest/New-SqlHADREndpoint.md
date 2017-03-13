---
external help file: Microsoft.SqlServer.Management.PSSnapins.dll-Help.xml
online version: 
schema: 2.0.0
ms.assetid: 5379F9EF-55E2-4170-BFBC-C3AC6595F586
updated_at: 3/13/2017 4:14 PM
ms.date: 3/13/2017
content_git_url: https://github.com/MicrosoftDocs/sql-docs-powershell/blob/master/sqlserver-cmdlets/sqlserver/vlatest/New-SqlHADREndpoint.md
original_content_git_url: https://github.com/MicrosoftDocs/sql-docs-powershell/blob/master/sqlserver-cmdlets/sqlserver/vlatest/New-SqlHADREndpoint.md
gitcommit: https://github.com/MicrosoftDocs/sql-docs-powershell/blob/6eefe64a0ce19459190f09768267a4c79f9a6af9/sqlserver-cmdlets/sqlserver/vlatest/New-SqlHADREndpoint.md
ms.topic: reference
author: stevestein
ms.author: sstein
keywords: powershell, cmdlet
manager: jhubbard
open_to_public_contributors: True
ms.service: sql-server
---

# New-SqlHADREndpoint

## SYNOPSIS
Creates a database mirroring endpoint on a SQL Server instance.

## SYNTAX

### ByPath (Default)
```
New-SqlHADREndpoint [-Port <Int32>] [-Owner <String>] [-Certificate <String>] [-IpAddress <IPAddress>]
 [-AuthenticationOrder <EndpointAuthenticationOrder>] [-Encryption <EndpointEncryption>]
 [-EncryptionAlgorithm <EndpointEncryptionAlgorithm>] [-Name] <String> [[-Path] <String>] [-Script]
 [-InformationAction <ActionPreference>] [-InformationVariable <String>] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

### ByObject
```
New-SqlHADREndpoint [-Port <Int32>] [-Owner <String>] [-Certificate <String>] [-IpAddress <IPAddress>]
 [-AuthenticationOrder <EndpointAuthenticationOrder>] [-Encryption <EndpointEncryption>]
 [-EncryptionAlgorithm <EndpointEncryptionAlgorithm>] [-Name] <String> [-InputObject] <Server> [-Script]
 [-InformationAction <ActionPreference>] [-InformationVariable <String>] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

## DESCRIPTION
The **New-SqlHADREndpoint** cmdlet creates a database mirroring endpoint on a SQL Server instance.
This endpoint is required on every server instance that hosts an availability replica for any availability group.
Each server instance can only have one database mirroring endpoint.
If a server instance possesses a database mirroring endpoint, use the existing endpoint.

## EXAMPLES

### Example 1: Create a database mirroring endpoint
```
PS C:\> New-SqlHADREndpoint -Path "SQLSERVER:\Sql\Computer\Instance" -Name "MainEndpoint"
```

This command creates a database mirroring endpoint named MainEndpoint on the server instance located at the specified path.
This endpoint uses the default port, 5022.

### Example 2: Create a database mirroring endpoint that requires encryption
```
PS C:\> New-SqlHADREndpoint -Path "SQLSERVER:\Sql\Computer\Instance" -Name "MainEndpoint" -Port 4022 -EncryptionAlgorithm Aes' -Encryption Required
```

This command creates a database mirroring endpoint named MainEndpoint on the server instance located at the specified path.
This endpoint listens on port 4022.
The endpoint uses the AES algorithm for encryption and requires that connections use encryption.

### Example 3: Create a database mirroring endpoint that is encrypted with a certificate
```
PS C:\> New-SqlHADREndpoint -Path "SQLSERVER:\Sql\Computer\Instance" -Name "MainEndpoint" -AuthenticationOrder 
Certificate -Certificate "EncryptionCertificate"
```

This command creates a database mirroring endpoint named MainEndpoint on the server instance located at the specified path.
This endpoint uses the certificate named EncryptionCertificate to authenticate connections.

### Example 4: Create a database mirroring endpoint script
```
PS C:\> New-SqlHADREndpoint -Path "SQLSERVER:\Sql\Computer\Instance" -Name "MainEndpoint" -Script
```

This command outputs the Transact-SQL script that creates a database mirroring endpoint named MainEndpoint on the server instance located at the specified path.
The endpoint is not actually created by this command.

## PARAMETERS

### -Port
Specifies the TCP port on which the endpoint will listen for connections.
The default is 5022.

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

### -Owner
Specifies the login of the owner of the endpoint.
By default, this is the current login.

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

### -Certificate
Specifies the name of the certificate that the endpoint will use to authenticate connections.
The far endpoint must have a certificate with the public key matching the private key of the certificate.

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

### -IpAddress
Specifies the IP address of the endpoint.
The default is ALL, which indicates that the listener accepts a connection on any valid IP address.

```yaml
Type: IPAddress
Parameter Sets: (All)
Aliases: 

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -AuthenticationOrder
Specifies the order and type of authentication that is used by the endpoint.
Valid values are: 

- Certificate
- CertificateKerberos
- CertificateNegotiate
- CertificateNtlm
- Kerberos
- KerberosCertificate
- Negotiate
- NegotiateCertificate
- Ntlm
- NtlmCertificate.

If the specified option calls for a certificate, the **Certificate** parameter must be set.

```yaml
Type: EndpointAuthenticationOrder
Parameter Sets: (All)
Aliases: 

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Encryption
Specifies the encryption option for the endpoint.
Valid values are: 

- Disabled
- Supported
- Required

Required is the default value.

```yaml
Type: EndpointEncryption
Parameter Sets: (All)
Aliases: 

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -EncryptionAlgorithm
Specifies the form of encryption used by the endpoint.
Valid values are: 

- Aes
- AesRC4
- None
- RC4
- RC4Aes

By default the endpoint will use Aes encryption.

The RC4 algorithm is only supported for backward compatibility.
New material can only be encrypted using RC4 or RC4_128 when the database is in compatibility level 90 or 100, but this is not recommended.
For increased security, use a newer algorithm such as one of the AES algorithms instead.

```yaml
Type: EndpointEncryptionAlgorithm
Parameter Sets: (All)
Aliases: 

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Name
Specifies the endpoint name.
This parameter is required.

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
Specifies the path to the SQL Server instance of the endpoint.
This parameter is optional.
If not specified, the current working location is used.

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
Indicates that this cmdlet returns a Transact-SQL script that performs the task.

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
Specifies the server object of the SQL Server instance where the endpoint is created.

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

### SMO.Server

## OUTPUTS

### SMO.Endpoint

## NOTES

## RELATED LINKS

[Set-SqlHADREndpoint](xref:sqlserver/vlatest/Set-SqlHADREndpoint.md)
