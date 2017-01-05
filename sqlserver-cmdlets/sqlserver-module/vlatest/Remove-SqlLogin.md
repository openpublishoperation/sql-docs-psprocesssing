---
external help file: Microsoft.SqlServer.Management.PSSnapins.dll-Help.xml
online version: 
schema: 2.0.0
ms.assetid: D68F4E0B-249B-4173-AE2F-A63EE420AD40
updated_at: 1/5/2017 8:57 AM
ms.date: 1/5/2017
content_git_url: https://github.com/MicrosoftDocs/sql-docs-powershell/blob/live/sqlserver-cmdlets/sqlserver-module/vlatest/Remove-SqlLogin.md
original_content_git_url: https://github.com/MicrosoftDocs/sql-docs-powershell/blob/live/sqlserver-cmdlets/sqlserver-module/vlatest/Remove-SqlLogin.md
gitcommit: https://github.com/MicrosoftDocs/sql-docs-powershell/blob/0d97835841eb5cfbe37d096037375a2e0c3eb87c/sqlserver-cmdlets/sqlserver-module/vlatest/Remove-SqlLogin.md
ms.topic: reference
author: stevestein
ms.author: sstein
keywords: powershell, cmdlet
manager: jhubbard
open_to_public_contributors: true
ms.service: sql-server
---

# Remove-SqlLogin

## SYNOPSIS
Removes Login objects from an instance of SQL Server.

## SYNTAX

### ByPath (Default)
```
Remove-SqlLogin [-LoginName <String[]>] [-RemoveAssociatedUsers] [-Force] [[-Path] <String>] [-Script]
 [-InformationAction <ActionPreference>] [-InformationVariable <String>] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

### ByObject
```
Remove-SqlLogin [-LoginName <String[]>] [-RemoveAssociatedUsers] [-Force] [-InputObject] <Login> [-Script]
 [-InformationAction <ActionPreference>] [-InformationVariable <String>] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

### ByName
```
Remove-SqlLogin [-LoginName <String[]>] [-RemoveAssociatedUsers] [-Force] [[-ServerInstance] <String[]>]
 [-Credential <PSCredential>] [-ConnectionTimeout <Int32>] [-Script] [-InformationAction <ActionPreference>]
 [-InformationVariable <String>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## DESCRIPTION
The **Remove-SqlLogin** cmdlet removes **Login** objects form an instance of SQL Server.
If you specify the name of the **Login** object, the cmdlet removes that specific object.

## EXAMPLES

### Example 1: Remove a Login object by name
```
PS C:\> Get-SqlLogin -ServerInstance "MyServerInstance" -LoginName "Login01" | Remove-SqlLogin
```

This command gets the **Login** object named Login01 on the specified instance by using the **Get-SqlLogin** cmdlet.
The command passes it to the current cmdlet by using the pipeline operator.
That cmdlet removes the **Login** object.

### Example 2: Remove objects that match a string
```
PS C:\> Get-SqlLogin -ServerInstance "MyServerInstance" -LoginName 'Login.*' -Regex | Remove-SqlLogin -RemoveAssociatedUsers
```

This command gets the **Login** objects that contain the string Login.* as a regular expression on the specified instance by using **Get-SqlLogin**.
The command passes it to the current cmdlet.
That cmdlet removes the **Login** objects.
The command removes associated users.

### Example 3: Remove several Login objects
```
PS C:\> Remove-Login -ServerInstance "MyServerInstance" -LoginName "login01","login02","login03"
```

This command removes the **Login** objects named login01, login02, and login03.

## PARAMETERS

### -LoginName
Specifies an array of names of **Login** objects that this cmdlet removes.
The case sensitivity is the same as that of the instance of SQL Server.

```yaml
Type: String[]
Parameter Sets: (All)
Aliases: Name

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -RemoveAssociatedUsers
Indicates that this cmdlet removes the users that are associated with the **Login** object.

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

### -Force
Forces the command to run without asking for user confirmation.

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
Specifies an SQL Server Management Objects (SMO) object that represents the **Login** object that this cmdlet removes.

```yaml
Type: Login
Parameter Sets: ByObject
Aliases: 

Required: True
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

[Get-SqlLogin](xref:sqlserver-module/vlatest/Get-SqlLogin.md)
