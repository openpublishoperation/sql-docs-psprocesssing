---
external help file: Microsoft.SqlServer.Management.PSSnapins.dll-Help.xml
online version: 
schema: 2.0.0
ms.assetid: 594723B8-DC49-4D51-9677-D9050C1F66AB
updated_at: 1/5/2017 8:57 AM
ms.date: 1/5/2017
content_git_url: https://github.com/MicrosoftDocs/sql-docs-powershell/blob/master/sqlserver-cmdlets/sqlserver-module/vlatest/Add-SqlLogin.md
original_content_git_url: https://github.com/MicrosoftDocs/sql-docs-powershell/blob/master/sqlserver-cmdlets/sqlserver-module/vlatest/Add-SqlLogin.md
gitcommit: https://github.com/MicrosoftDocs/sql-docs-powershell/blob/0d97835841eb5cfbe37d096037375a2e0c3eb87c/sqlserver-cmdlets/sqlserver-module/vlatest/Add-SqlLogin.md
ms.topic: reference
author: stevestein
ms.author: sstein
keywords: powershell, cmdlet
manager: jhubbard
open_to_public_contributors: true
ms.service: sql-server
---

# Add-SqlLogin

## SYNOPSIS
Creates a Login object in an instance of SQL Server.

## SYNTAX

### ByPath (Default)
```
Add-SqlLogin [-LoginName <String>] -LoginType <LoginType> [-DefaultDatabase <String>] [-EnforcePasswordPolicy]
 [-EnforcePasswordExpiration] [-MustChangePasswordAtNextLogin] [-Certificate <String>]
 [-AsymmetricKey <String>] [-CredentialName <String>] [-LoginPSCredential <PSCredential>] [-Enable]
 [-GrantConnectSql] [[-Path] <String>] [-Script] [-InformationAction <ActionPreference>]
 [-InformationVariable <String>] [<CommonParameters>]
```

### ByObject
```
Add-SqlLogin [-LoginName <String>] -LoginType <LoginType> [-DefaultDatabase <String>] [-EnforcePasswordPolicy]
 [-EnforcePasswordExpiration] [-MustChangePasswordAtNextLogin] [-Certificate <String>]
 [-AsymmetricKey <String>] [-CredentialName <String>] [-LoginPSCredential <PSCredential>] [-Enable]
 [-GrantConnectSql] [[-InputObject] <Server>] [-Script] [-InformationAction <ActionPreference>]
 [-InformationVariable <String>] [<CommonParameters>]
```

### ByName
```
Add-SqlLogin [-LoginName <String>] -LoginType <LoginType> [-DefaultDatabase <String>] [-EnforcePasswordPolicy]
 [-EnforcePasswordExpiration] [-MustChangePasswordAtNextLogin] [-Certificate <String>]
 [-AsymmetricKey <String>] [-CredentialName <String>] [-LoginPSCredential <PSCredential>] [-Enable]
 [-GrantConnectSql] [[-ServerInstance] <String[]>] [-Credential <PSCredential>] [-ConnectionTimeout <Int32>]
 [-Script] [-InformationAction <ActionPreference>] [-InformationVariable <String>] [<CommonParameters>]
```

## DESCRIPTION
The **Add-SqlLogin** cmdlet creates a **Login** object in an instance of SQL Server.

## EXAMPLES

### Example 1: Create an SqlLogin type
```
PS C:\> Add-SqlLogin -ServerInstance "MyServerInstance" -LoginName "MyLogin" -LoginType "SqlLogin" -DefaultDatabase "OtherDatabase"
Name                                          Login Type    Created
----                                          ----------    -------
MyLogin                                       SqlLogin      8/11/2016 3:19 PM
```

This command creates a **Login** object that is named MyLogin of the type SqlLogin.
The command specifies its default database as OtherDatabase in the server instance named MyServerInstance.
This command prompts you for a password for the **Login**.

### Example 2: Create an asymmetric key type
```
PS C:\> Add-SqlLogin -ServerInstance "MyServerInstance" -LoginName "MyLogin" -LoginType "AsymmetricKey" -AsymmetricKey "MyKey" -CredentialName "MyCredential"
Name                                          Login Type    Created
----                                          ----------    -------
MyLogin                                       AsymmetricKey 8/11/2016 4:08 PM
```

This command creates a **Login** object that is named MyLogin of the type AsymmetricKey.
It specifies an asymmetric key that is named MyKey.
Also it maps the credential called MyCredential to the new **Login** object.
The command operates in the server instance named MyServerInstance.

## PARAMETERS

### -LoginName
Specifies a name for the **Login** object.
The case sensitivity is the same as that of the instance of SQL Server.

```yaml
Type: String
Parameter Sets: (All)
Aliases: Name

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -LoginType
Specifies the type of the **Login** object as a **Microsoft.SqlServer.Management.Smo.LoginType** value.
The acceptable values for this parameter are:

- AsymmetricKey 
- Certificate 
- SqlLogin 
- WindowsGroup 
- WindowsUser 

At this time, the cmdlet does not support ExternalUser or ExternalGroup.

```yaml
Type: LoginType
Parameter Sets: (All)
Aliases: 

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -DefaultDatabase
Specify the default database for the **Login** object.
The default value is master.

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

### -EnforcePasswordPolicy
Indicates that the password policy is enforced for the **Login** object.

This parameter applies only SqlLogin type objects.

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

### -EnforcePasswordExpiration
Indicates that the password expiration policy is enforced for the **Login** object.

This parameter applies only SqlLogin type objects.
This parameter implies the *EnforcePasswordPolicy* parameter.
You do not have to specify both.

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

### -MustChangePasswordAtNextLogin
Indicates that the user must change the password at the next login.

This parameter applies only SqlLogin type objects.
This parameter implies the *EnforcePasswordExpiration* parameter.
You do not have to specify both.

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

### -Certificate
Specify the name of the certificate for the **Login** object.
If the *LoginType* parameter has the value Certificate, specify a certificate.

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

### -AsymmetricKey
Specify the name of the asymmetric key for the **Login** object.
If the *LoginType* parameter has the value AsymmetricKey, specify an asymmetric key.

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

### -CredentialName
Specify the name of the credential for the **Login** object.

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

### -LoginPSCredential
Specifies a **PSCredential** object that allows the **Login** object to provide name and password without a prompt.

```yaml
Type: PSCredential
Parameter Sets: (All)
Aliases: 

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Enable
Indicates that the **Login** object is enabled.
By default, **Login** objects are disabled.

WindowsGroup type objects are always enabled.
This parameter does not affect them.

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

### -GrantConnectSql
Indicates that the **Login** object is not denied permissions to connect to the database engine.
By default, **Login** objects are denied permissions to connect to the database engine.

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
Specifies the path of the SQL Server on which this cmdlet runs the operation.
The default value is the current working directory.

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

### -InputObject
Specifies an SQL Server Management Objects (SMO) object the SQL Server on which this cmdlet operates.

```yaml
Type: Server
Parameter Sets: ByObject
Aliases: 

Required: False
Position: 1
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -ServerInstance
Specifies the name of an instance of SQL Server.
For the default instance, specify the computer name.
For named instances, use the format ComputerName\InstanceName.

```yaml
Type: String[]
Parameter Sets: ByName
Aliases: 

Required: False
Position: 1
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -Credential
Specifies a **PSCredential** object for the connection to SQL Server.
To obtain a credential object, use the **Get-Credential** cmdlet.
For more information, type `Get-Help Get-Credential`.

```yaml
Type: PSCredential
Parameter Sets: ByName
Aliases: 

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ConnectionTimeout
Specifies the number of seconds to wait for a server connection before a time-out failure.
The time-out value must be an integer between 0 and 65534.
If 0 is specified, connection attempts do not time out.

```yaml
Type: Int32
Parameter Sets: ByName
Aliases: 

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

[Get-SqlLogin](xref:sqlserver-module/vlatest/Get-SqlLogin.md)

[Remove-SqlLogin](xref:sqlserver-module/vlatest/Remove-SqlLogin.md)
