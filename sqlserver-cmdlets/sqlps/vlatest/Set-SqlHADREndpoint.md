---
external help file: Microsoft.SqlServer.Management.PSSnapins.dll-Help.xml
online version: 
schema: 2.0.0
ms.assetid: 7BBEF9E5-35B2-450D-8128-EF070DE75D15
updated_at: 12/8/2016 7:20 PM
ms.date: 12/8/2016
content_git_url: https://github.com/MicrosoftDocs/sql-docs-powershell/blob/master/sqlserver-cmdlets/sqlps/vlatest/Set-SqlHADREndpoint.md
original_content_git_url: https://github.com/MicrosoftDocs/sql-docs-powershell/blob/master/sqlserver-cmdlets/sqlps/vlatest/Set-SqlHADREndpoint.md
gitcommit: https://github.com/MicrosoftDocs/sql-docs-powershell/blob/b925b18b49186ab91cfeb5201e061d569d0eeae2/sqlserver-cmdlets/sqlps/vlatest/Set-SqlHADREndpoint.md
ms.topic: reference
author: stevestein
ms.author: sstein
keywords: powershell, cmdlet
manager: jhubbard
open_to_public_contributors: true
ms.service: sql-server
---

# Set-SqlHADREndpoint

## SYNOPSIS
Sets the properties of a database mirroring endpoint.

## SYNTAX

### ByPath (Default)
```
Set-SqlHADREndpoint [-Owner <String>] [-Certificate <String>] [-IpAddress <IPAddress>]
 [-AuthenticationOrder <EndpointAuthenticationOrder>] [-Encryption <EndpointEncryption>]
 [-EncryptionAlgorithm <EndpointEncryptionAlgorithm>] [-Port <Int32>] [-State <EndpointState>]
 [[-Path] <String>] [-Script] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### ByObject
```
Set-SqlHADREndpoint [-Owner <String>] [-Certificate <String>] [-IpAddress <IPAddress>]
 [-AuthenticationOrder <EndpointAuthenticationOrder>] [-Encryption <EndpointEncryption>]
 [-EncryptionAlgorithm <EndpointEncryptionAlgorithm>] [-Port <Int32>] [-State <EndpointState>]
 [-InputObject] <Endpoint> [-Script] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## DESCRIPTION
The **Set-SqlHADREndpoint** cmdlet changes the properties of a database mirroring endpoint.

## EXAMPLES

### Example 1: Set the port number of a database mirroring endpoint
```
PS C:\>Set-SqlHADREndpoint -Path "SQLSERVER:\Sql\Computer\Instance\Endpoints\MainDbmEndpoint" -Port 5050
```

This command sets the port number of the database mirroring endpoint named MainDbmEndpoint to 5050 on the server instance named Computer\Instance.

### Example 2: Start a database mirroring endpoint
```
PS C:\>Set-SqlHADREndpoint -Path "SQLSERVER:\Sql\Computer\Instance\Endpoints\MainDbmEndpoint" -State Started
```

This command starts the database mirroring endpoint named MainDbmEndpoint on the server instance Computer\Instance.

## PARAMETERS

### -AuthenticationOrder
Specifies the order and type of authentication that is used by the endpoint.
. If the specified option calls for a certificate, the **Certificate** parameter must be set unless a certificate is already associated with the endpoint.
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
- NtlmCertificate

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

### -Certificate
Specifies the name of the certificate the endpoint will use to authenticate connections.
The far endpoint must have a certificate with the public key matching the private key of the specified certificate.

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

### -Encryption
Specifies the endpoint encryption setting.
Valid values are: 

- Disabled
- Supported
- Required

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

NOTE: The RC4 algorithm is only supported for backward compatibility.
New material can only be encrypted using RC4 or RC4_128 when the database is in compatibility level 90 or 100, but this is not recommended.
For improved security, use a newer algorithm such as one of the AES algorithms instead.

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

### -InputObject
Specifies the endpoint that to modify.
This must be a database mirroring endpoint.

```yaml
Type: Endpoint
Parameter Sets: ByObject
Aliases: 

Required: True
Position: 2
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -IpAddress
Specifies the IP address on which the endpoint will listen.

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

### -Owner
Specifies the owner of the endpoint.

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

### -Path
Specifies the path to the database mirroring endpoint.
This is an optional parameter.
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

### -Port
Specifies the TCP port number used by the endpoint to listen for connections.

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

### -Script
Indicates that this cmdlet outputs a Transact-SQL script that performs the task.

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

### -State
Specifies the state of the endpoint.
Valid values are: 

- Started
- Stopped
-  Disabled

```yaml
Type: EndpointState
Parameter Sets: (All)
Aliases: 

Required: False
Position: Named
Default value: None
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

### CommonParameters
This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable. For more information, see about_CommonParameters (http://go.microsoft.com/fwlink/?LinkID=113216).

## INPUTS

### SMO.Endpoint

## OUTPUTS

### SMO.Endpoint

## NOTES

## RELATED LINKS

[New-SqlHADREndpoint](xref:sqlps/vlatest/New-SqlHADREndpoint.md)


