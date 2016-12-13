---
external help file: Microsoft.SqlServer.Management.PSSnapins.dll-Help.xml
online version: 
schema: 2.0.0
ms.assetid: 026CFF52-6BDF-411E-95C2-9B32362C7A32
updated_at: 12/8/2016 7:20 PM
ms.date: 12/8/2016
content_git_url: https://github.com/MicrosoftDocs/sql-docs-powershell/blob/master/sqlserver-cmdlets/sqlserver/vlatest/Enable-SqlAlwaysOn.md
original_content_git_url: https://github.com/MicrosoftDocs/sql-docs-powershell/blob/master/sqlserver-cmdlets/sqlserver/vlatest/Enable-SqlAlwaysOn.md
gitcommit: https://github.com/MicrosoftDocs/sql-docs-powershell/blob/b925b18b49186ab91cfeb5201e061d569d0eeae2/sqlserver-cmdlets/sqlserver/vlatest/Enable-SqlAlwaysOn.md
ms.topic: reference
author: stevestein
ms.author: sstein
keywords: powershell, cmdlet
manager: jhubbard
open_to_public_contributors: true
ms.service: sql-server
---

# Enable-SqlAlwaysOn

## SYNOPSIS
Enables the AlwaysOn availability groups feature.

## SYNTAX

### ByPath (Default)
```
Enable-SqlAlwaysOn [[-Path] <String>] [-NoServiceRestart] [-Force] [-Credential <PSCredential>]
 [-InformationAction <ActionPreference>] [-InformationVariable <String>] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

### ByObject
```
Enable-SqlAlwaysOn [-InputObject] <Server> [-NoServiceRestart] [-Force] [-Credential <PSCredential>]
 [-InformationAction <ActionPreference>] [-InformationVariable <String>] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

### ByName
```
Enable-SqlAlwaysOn -ServerInstance <String> [-NoServiceRestart] [-Force] [-Credential <PSCredential>]
 [-InformationAction <ActionPreference>] [-InformationVariable <String>] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

## DESCRIPTION
The **Enable-SqlAlwaysOn** cmdlet enables AlwaysOn on an instance of SQL Server.
If the AlwaysOn availability groups feature is enabled while the SQL Server service is running, the database engine service must be restarted for the changes to complete.
Unless you specify the **Force** parameter, the cmdlet prompts you to restart the service.

If the AlwaysOn availability groups feature is already enabled, no action is performed.

This cmdlet can run against a remote service.

You must have Administrator permissions to execute this cmdlet.

## EXAMPLES

### Example 1: Enable AlwaysOn availability groups at the specified path
```
PS C:\>Enable-SqlAlwaysOn -Path "SQLSERVER:\Sql\Computer\Instance"
```

This command enables AlwaysOn availability groups on the instance of SQL Server located at the specified path.
This change requires restarting the instance, and you will be prompted to confirm this restart.

### Example 2: Enable AlwaysOn availability groups at the specified path and restart the server without confirmation
```
PS C:\>Enable-SqlAlwaysOn -Path "SQLSERVER:\Sql\Computer\Instance" -Force
```

This command enables AlwaysOn availability groups on the instance of SQL Server located at the specified path.
The  *Force* option causes the server instance to be restarted without prompting you for confirmation.

### Example 3: Enable AlwaysOn availability groups for the specified server instance
```
PS C:\>Enable-SqlAlwaysOn -ServerInstance "Computer\Instance"
```

This command enables AlwaysOn availability groups on the instance of SQL Server named Computer\Instance.
This change requires restarting the instance and you will be prompted to confirm this restart.

### Example 4: Enable AlwaysOn availability groups for the specified server instance using Windows authentication
```
PS C:\>Enable-SqlAlwaysOn -ServerInstance "Computer\Instance" -Credential (Get-Credential "DOMAIN\Username")
```

This command enables AlwaysOn availability groups on the instance of SQL Server named Computer\Instance using Windows authentication.
You will be prompted to enter the password for the specified account.
This change requires restarting the instance, and you will also be prompted to confirm this restart.

### Example 5: Enable AlwaysOn availability groups at the specified path without restarting the server
```
PS C:\>Enable-SqlAlwaysOn -Path "SQLSERVER:\Sql\Computer\Instance" -NoServiceRestart
```

This command enables AlwaysOn availability groups on the SQL Server instance located at the specified path, but the command does not restart the instance.
The change will not take effect until you manually restart this server instance.

## PARAMETERS

### -Path
Specifies the path to the SQL Server instance.
This is an optional parameter.
If not specified, the current working location is used.

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

### -NoServiceRestart
Indicates that the user is not prompted to restart the SQL Server service.
You must manually restart the SQL Server service for changes to take effect.
When this parameter is set, **Force** is ignored.

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

### -Credential
Specifies the name of the SQL Server instance on which to enable the AlwaysOn availability groups feature.
The format is MACHINENAME\INSTANCE.
To enable this setting on a remote server, use this along with the **Credential** parameter.

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
Specifies the server object of the SQL Server instance.

```yaml
Type: Server
Parameter Sets: ByObject
Aliases: 

Required: True
Position: 1
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -ServerInstance
Specifies the name of the SQL Server instance.
The format is MACHINENAME\INSTANCE.
To enable this setting on a remote server, use this along with the **Credential** parameter.

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

### CommonParameters
This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable. For more information, see about_CommonParameters (http://go.microsoft.com/fwlink/?LinkID=113216).

## INPUTS

## OUTPUTS

## NOTES

## RELATED LINKS

[Disable-SqlAlwaysOn](xref:sqlserver/vlatest/Disable-SqlAlwaysOn.md)


