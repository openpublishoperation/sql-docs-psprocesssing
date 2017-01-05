---
external help file: Microsoft.SqlServer.Management.PSSnapins.dll-Help.xml
online version: 
schema: 2.0.0
ms.assetid: 4CC1D3F8-E533-4B66-8077-512EAC50A502
updated_at: 1/4/2017 6:38 PM
ms.date: 1/4/2017
content_git_url: https://github.com/MicrosoftDocs/sql-docs-powershell/blob/live/sqlserver-cmdlets/sqlps/vlatest/Disable-SqlAlwaysOn.md
original_content_git_url: https://github.com/MicrosoftDocs/sql-docs-powershell/blob/live/sqlserver-cmdlets/sqlps/vlatest/Disable-SqlAlwaysOn.md
gitcommit: https://github.com/MicrosoftDocs/sql-docs-powershell/blob/4c48bd1c26220ff873e612527853aeeef98777da/sqlserver-cmdlets/sqlps/vlatest/Disable-SqlAlwaysOn.md
ms.topic: reference
author: stevestein
ms.author: sstein
keywords: powershell, cmdlet
manager: jhubbard
open_to_public_contributors: true
ms.service: sql-server
---

# Disable-SqlAlwaysOn

## SYNOPSIS
Disables the AlwaysOn availability groups feature for a server.

## SYNTAX

### ByPath (Default)
```
Disable-SqlAlwaysOn [[-Path] <String>] [-NoServiceRestart] [-Force] [-Credential <PSCredential>] [-WhatIf]
 [-Confirm] [<CommonParameters>]
```

### ByObject
```
Disable-SqlAlwaysOn [-InputObject] <Server> [-NoServiceRestart] [-Force] [-Credential <PSCredential>] [-WhatIf]
 [-Confirm] [<CommonParameters>]
```

### ByName
```
Disable-SqlAlwaysOn -ServerInstance <String> [-NoServiceRestart] [-Force] [-Credential <PSCredential>]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

## DESCRIPTION
The **Disable-SqlAlwaysOn** cmdlet disables the AlwaysOn vailability groups feature on a SQL Server instance.
If the AlwaysOn availability groups feature is disabled while the SQL Server service is running, the database engine service must be restarted for the changes to complete.
Unless you specify the *Force* parameter, the cmdlet prompts you to restart the service.

If the AlwaysOn availability groups feature is already disabled, this cmdlet makes no changes.

This cmdlet can run against a remote service.

You must have Administrator permissions to execute this cmdlet.

## EXAMPLES

### Example 1: Disable AlwaysOn availability groups at the specified path
```
PS C:\> Disable-SqlAlwaysOn -Path "SQLSERVER:\Sql\Computer\Instance"
```

This command disables AlwaysOn availability groups on the instance of SQL Server located at the specified path.
This command requires restarting the server instance, and you will be prompted to confirm this restart.

### Example 2: Disable AlwaysOn availability groups at the specified path and restart the server without confirmation
```
PS C:\> Disable-SqlAlwaysOn -Path "SQLSERVER:\Sql\Computer\Instance" -Force
```

This command disables AlwaysOn availability groups on the instance of SQL Server located at the specified path.
The *Force* option causes the server instance to be restarted without prompting you for confirmation.

### Example 3: Disable AlwaysOn availability groups for the specified server instance
```
PS C:\> Disable-SqlAlwaysOn -ServerInstance "Computer\Instance"
```

This command disables AlwaysOn availability groups on the instance of SQL Server named Computer\Instance.
This command requires restarting the instance and you will be prompted to confirm this restart.

### Example 4: Disable AlwaysOn availability groups for the specified server instance using Windows authentication
```
PS C:\> Disable-SqlAlwaysOn -ServerInstance "Computer\Instance" -Credential (Get-Credential "DOMAIN\Username")
```

This command disables AlwaysOn availability groups on the instance of SQL Server named Computer\Instance using Windows authentication.
You will be prompted to enter the password for the specified account, DOMAIN\Username.
This change requires restarting the instance and you will also be prompted to confirm this restart.

### Example 5: Disable AlwaysOn availability groups at the specified path without restarting the server
```
PS C:\> Disable-SqlAlwaysOn -Path "SQLSERVER:\Sql\Computer\Instance" -NoServiceRestart
```

This command disables AlwaysOn availability groups on the instance of SQL Server located at the specified path, but the command does not restart the instance.
The change will not take effect until you manually restart this server instance.

## PARAMETERS

### -Credential
Specifies a windows credential that has permission to alter the AlwaysOn setting on the SQL Server instance.

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

### -Force
Forces the command to run without asking for user confirmation.
This parameter is provided to permit the construction of scripts.

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

### -InputObject
Specifies the server object of the instance of SQL Server where the AlwaysOn availability groups setting is disabled.

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

### -NoServiceRestart
Indicates that the user is not prompted to restart the SQL Server service.
You must manually restart the SQL Server service for changes to take effect.
When this parameter is set, *Force* is ignored.

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
Specifies the path to the instance of the SQL Server.
This is an optional parameter.
If not specified, the value of the current working location is used.

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

### -ServerInstance
Specifies the name of the instance of the SQL Server where AlwaysOn is disabled.
The format should be MACHINENAME\INSTANCE.
Use the *Credential* parameter to change the AlwaysOn setting on a remote server.

```yaml
Type: String
Parameter Sets: ByName
Aliases: 

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
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

### CommonParameters
This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable. For more information, see about_CommonParameters (http://go.microsoft.com/fwlink/?LinkID=113216).

## INPUTS

### SMO.Server

## OUTPUTS

## NOTES

## RELATED LINKS

[Enable-SqlAlwaysOn](xref:sqlps/vlatest/Enable-SqlAlwaysOn.md)
