---
external help file: Microsoft.SqlServer.Management.PSSnapins.dll-Help.xml
online version: 
schema: 2.0.0
ms.assetid: C1EA6377-55CF-4B3A-B89A-EB68BDFFFDE0
updated_at: 1/5/2017 8:57 AM
ms.date: 1/5/2017
content_git_url: https://github.com/MicrosoftDocs/sql-docs-powershell/blob/master/sqlserver-cmdlets/sqlserver-module/vlatest/Get-SqlLogin.md
original_content_git_url: https://github.com/MicrosoftDocs/sql-docs-powershell/blob/master/sqlserver-cmdlets/sqlserver-module/vlatest/Get-SqlLogin.md
gitcommit: https://github.com/MicrosoftDocs/sql-docs-powershell/blob/0d97835841eb5cfbe37d096037375a2e0c3eb87c/sqlserver-cmdlets/sqlserver-module/vlatest/Get-SqlLogin.md
ms.topic: reference
author: stevestein
ms.author: sstein
keywords: powershell, cmdlet
manager: jhubbard
open_to_public_contributors: true
ms.service: sql-server
---

# Get-SqlLogin

## SYNOPSIS
Returns Login objects in an instance of SQL Server.

## SYNTAX

### ByPath (Default)
```
Get-SqlLogin [-LoginName <String>] [-Disabled] [-Locked] [-PasswordExpired] [-HasAccess] [-RegEx] [-Wildcard]
 [-LoginType <LoginType>] [[-Path] <String>] [-InformationAction <ActionPreference>]
 [-InformationVariable <String>] [<CommonParameters>]
```

### ByObject
```
Get-SqlLogin [-LoginName <String>] [-Disabled] [-Locked] [-PasswordExpired] [-HasAccess] [-RegEx] [-Wildcard]
 [-LoginType <LoginType>] [[-InputObject] <Server>] [-InformationAction <ActionPreference>]
 [-InformationVariable <String>] [<CommonParameters>]
```

### ByName
```
Get-SqlLogin [-LoginName <String>] [-Disabled] [-Locked] [-PasswordExpired] [-HasAccess] [-RegEx] [-Wildcard]
 [-LoginType <LoginType>] [[-ServerInstance] <String[]>] [-Credential <PSCredential>]
 [-ConnectionTimeout <Int32>] [-InformationAction <ActionPreference>] [-InformationVariable <String>]
 [<CommonParameters>]
```

## DESCRIPTION
The **Get-SqlLogin** cmdlet returns **Login** objects in an instance of SQL Server.
If you specify the name of the **Login** object, the cmdlet removes that specific object.

## EXAMPLES

### Example 1: Get all Login objects for an instance
```
PS C:\> Get-SqlLogin -ServerInstance "MyServerInstance"
Name                                          Login Type    Created
----                                          ----------    -------
##MS_PolicyEventProcessingLogin##             SqlLogin      4/30/2016 12:46 AM
##MS_PolicyTsqlExecutionLogin##               SqlLogin      4/30/2016 12:46 AM
NT AUTHORITY\SYSTEM                           WindowsUser   6/16/2016 10:29 AM
NT Service\MSSQLSERVER                        WindowsUser   6/16/2016 10:29 AM
NT SERVICE\SQLSERVERAGENT                     WindowsUser   6/16/2016 10:29 AM
NT SERVICE\SQLTELEMETRY                       WindowsUser   6/16/2016 10:29 AM
NT SERVICE\SQLWriter                          WindowsUser   6/16/2016 10:29 AM
NT SERVICE\Winmgmt                            WindowsUser   6/16/2016 10:29 AM
sa                                            SqlLogin      4/8/2003 9:10 AM
```

This command returns all **Login** objects in the instance of SQL Server named MyServerInstance.

### Example 2: Get Login objects that match a regular expression
```
PS C:\> Get-SqlLogin -ServerInstance "MyServerInstance" -LoginName "\bNT.*" -RegEx
Name                                          Login Type    Created
----                                          ----------    -------
NT AUTHORITY\SYSTEM                           WindowsUser   6/16/2016 10:29 AM
NT Service\MSSQLSERVER                        WindowsUser   6/16/2016 10:29 AM
NT SERVICE\SQLSERVERAGENT                     WindowsUser   6/16/2016 10:29 AM
NT SERVICE\SQLTELEMETRY                       WindowsUser   6/16/2016 10:29 AM
NT SERVICE\SQLWriter                          WindowsUser   6/16/2016 10:29 AM
NT SERVICE\Winmgmt                            WindowsUser   6/16/2016 10:29 AM
```

This command returns **Login** objects that have names that match the regular expression \bNT.* in the instance of SQL Server named MyServerInstance.

### Example 3: Get Login objects of a type
```
PS C:\>Get-SqlLogin -ServerInstance "MyServerInstance" -LoginType SqlLogin
Name                                          Login Type    Created
----                                          ----------    -------
##MS_PolicyEventProcessingLogin##             SqlLogin      4/30/2016 12:46 AM
##MS_PolicyTsqlExecutionLogin##               SqlLogin      4/30/2016 12:46 AM
sa                                            SqlLogin      4/8/2003 9:10 AM
```

This command returns **Login** objects that are of type SqlLogin in the instance of SQL Server named MyServerInstance.

## PARAMETERS

### -LoginName
Specifies an array of names of **Login** objects that this cmdlet gets.
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

### -Disabled
Indicates that this cmdlet gets only disabled **Login** objects.

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

### -Locked
Indicates that this cmdlet gets only locked **Login** objects.

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

### -PasswordExpired
Indicates that this cmdlet gets only **Login** objects that have expired passwords.

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

### -HasAccess
Indicates that this cmdlet gets only **Login** objects that have access to the instance of SQL Server.

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

### -RegEx
Indicates that this cmdlet treats the value of the *LoginName* parameter as a regular expression.

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

### -Wildcard
Indicates that this cmdlet interprets wildcard characters in the value of the *LoginName* parameter.

```yaml
Type: SwitchParameter
Parameter Sets: (All)
Aliases: Like

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -LoginType
Specifies the type of the **Login** objects that this cmdlet gets.
The acceptable values for this parameter are:

- AsymmetricKey 
- Certificate 
- SqlLogin 
- WindowsGroup 
- WindowsUser

```yaml
Type: LoginType
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
Specifies a SQL Server Management Objects (SMO) object the SQL Server for which this cmdlet gets **Login** objects.

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

[Add-SqlLogin](xref:sqlserver-module/vlatest/Add-SqlLogin.md)

[Remove-SqlLogin](xref:sqlserver-module/vlatest/Remove-SqlLogin.md)
