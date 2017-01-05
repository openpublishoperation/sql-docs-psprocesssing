---
external help file: Microsoft.SqlServer.Management.PSSnapins.dll-Help.xml
online version: 
schema: 2.0.0
ms.assetid: C88DD9BC-471E-4170-89AA-FE992C3BDC06
updated_at: 1/5/2017 8:57 AM
ms.date: 1/5/2017
content_git_url: https://github.com/MicrosoftDocs/sql-docs-powershell/blob/live/sqlserver-cmdlets/sqlserver-module/vlatest/Add-SqlAzureAuthenticationContext.md
original_content_git_url: https://github.com/MicrosoftDocs/sql-docs-powershell/blob/live/sqlserver-cmdlets/sqlserver-module/vlatest/Add-SqlAzureAuthenticationContext.md
gitcommit: https://github.com/MicrosoftDocs/sql-docs-powershell/blob/0d97835841eb5cfbe37d096037375a2e0c3eb87c/sqlserver-cmdlets/sqlserver-module/vlatest/Add-SqlAzureAuthenticationContext.md
ms.topic: reference
author: stevestein
ms.author: sstein
keywords: powershell, cmdlet
manager: jhubbard
open_to_public_contributors: true
ms.service: sql-server
---

# Add-SqlAzureAuthenticationContext

## SYNOPSIS
Performs authentication to Azure and acquires an authentication token.

## SYNTAX

```
Add-SqlAzureAuthenticationContext [-Interactive] [[-ClientID] <String>] [[-Secret] <String>]
 [[-Tenant] <String>] [-InformationAction <ActionPreference>] [-InformationVariable <String>]
 [<CommonParameters>]
```

## DESCRIPTION
The **Add-SqlAzureAuthenticationContext** cmdlet authenticates the specified principal account to Azure Resource Manager.
This cmdlet is used in conjunction with some other SQL Windows PowerShell cmdlets that interact with Azure resources, such as Key Vault.
This cmdlet needs to be called to perform authentication, before any other cmdlet can interact with an Azure  resource.

## EXAMPLES

### Example 1: Prompt a user for credentials to authenticate a user to Azure Resource Manager
```
PS C:\> Add-SqlAzureAuthenticationContext -Interactive
```

This command prompts a user for a username and a password and then authenticates the user to Azure Resource Manager.

### Example 2: Authenticate a user to Azure Resource Manager
```
PS C:\> Add-SqlAzureAuthenticationContext -ClientID ad34ca5a-a479-4cf4-b166-a2177b32d33e -Secret YU!KaoUa/JI8gvf6wT0p4m9AQE+sGB6oFY/iUdk2DHk= -Tenant "41fb6cc6-96f4-479d-bafd-a2e4810eb100"
```

This command performs authentication of the application principal with the specified client ID, which has been defined in the specified tenant, to Azure Resource Manager.

## PARAMETERS

### -Interactive
Indicates that this cmdlet prompts the user for credentials.

```yaml
Type: SwitchParameter
Parameter Sets: (All)
Aliases: 

Required: False
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ClientID
Specifies the application client ID.

```yaml
Type: String
Parameter Sets: (All)
Aliases: 

Required: False
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Secret
Specifies the application secret.

```yaml
Type: String
Parameter Sets: (All)
Aliases: 

Required: False
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Tenant
Specifies a tenant in Azure.

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

### CommonParameters
This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable. For more information, see about_CommonParameters (http://go.microsoft.com/fwlink/?LinkID=113216).

## INPUTS

## OUTPUTS

## NOTES

## RELATED LINKS

[Configure Always Encrypted using PowerShell](https://msdn.microsoft.com/library/mt755926.aspx)

[SQL Server Cmdlets](xref:sqlserver-module/vlatest/SqlServer.md)
