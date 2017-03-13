---
external help file: Microsoft.SqlServer.Management.PSSnapins.dll-Help.xml
online version: 
schema: 2.0.0
ms.assetid: 0AC14338-3BF1-46FE-BADE-D5EE6DA4E732
updated_at: 3/13/2017 4:14 PM
ms.date: 3/13/2017
content_git_url: https://github.com/MicrosoftDocs/sql-docs-powershell/blob/master/sqlserver-cmdlets/sqlserver/vlatest/Get-SqlDatabase.md
original_content_git_url: https://github.com/MicrosoftDocs/sql-docs-powershell/blob/master/sqlserver-cmdlets/sqlserver/vlatest/Get-SqlDatabase.md
gitcommit: https://github.com/MicrosoftDocs/sql-docs-powershell/blob/6eefe64a0ce19459190f09768267a4c79f9a6af9/sqlserver-cmdlets/sqlserver/vlatest/Get-SqlDatabase.md
ms.topic: reference
author: stevestein
ms.author: sstein
keywords: powershell, cmdlet
manager: jhubbard
open_to_public_contributors: True
ms.service: sql-server
---

# Get-SqlDatabase

## SYNOPSIS
Gets a SQL database object for each database that is present in the target instance of SQL Server.

## SYNTAX

### ByPath (Default)
```
Get-SqlDatabase [[-Name] <String>] [[-Path] <String>] [-Script] [-InformationAction <ActionPreference>]
 [-InformationVariable <String>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### ByName
```
Get-SqlDatabase [-ServerInstance] <String[]> [-Credential <PSCredential>] [-ConnectionTimeout <Int32>]
 [[-Name] <String>] [-Script] [-InformationAction <ActionPreference>] [-InformationVariable <String>] [-WhatIf]
 [-Confirm] [<CommonParameters>]
```

### ByObject
```
Get-SqlDatabase [[-Name] <String>] [-InputObject] <Server> [-Script] [-InformationAction <ActionPreference>]
 [-InformationVariable <String>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## DESCRIPTION
The **Get-SqlDatabase** cmdlet gets a SQL database object for each database that is present in the target instance of SQL Server.
If the name of the database is provided, the cmdlet will return only this specific database object.

This cmdlet supports the following modes of operation to get the SQL database object:

- Specify the instance Windows PowerShell path. 
- Specify the server object. 
- Specify the **ServerInstance** object of the target instance of SQL Server.

## EXAMPLES

### Example 1: Get a SQL database object
```
PS C:\> CD SQLSERVER:\SQL\Computer\Instance;
PS SQLSERVER:\SQL\Computer\Instance> Get-SqlDatabase -Name "DbName" -Credential $SqlCredential;
```

The first command changes the working directory to SQLSERVER:\SQL\Computer\Instance.

The second command gets the database object for the database named DbName of the server instance Computer\Instance.
The current working directory is used to determine the server instance where the operation occurs.

### Example 2: Get all instances of SQL Server on a computer
```
PS C:\> Get-SqlInstance -Credential $Credential -MachineName "Computer001" | Get-SqlDatabase -Credential $SqlCredential;
```

This command gets all instances of SQL Server on the computer named Computer001and returns all the databases that are present in the instances.

## PARAMETERS

### -Name
Specifies the name of the database that this cmdlet gets the SQL database object.

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

### -Path
Specifies the path to the instance of SQL Server on which this cmdlet runs the operation.
If you do not specify a value for this parameter, the cmdlet uses the current working location.

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
Indicates that this cmdlet generates a Transact-SQL script that runs the task.

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

### -ServerInstance
Specifies the name of an instance of SQL Server, as a string array, that becomes the target of the operation.

```yaml
Type: String[]
Parameter Sets: ByName
Aliases: 

Required: True
Position: 2
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### -Credential
Specifies a user account with Windows Administrator credentials on the target machine.

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
Specifies the number of seconds to wait for a SQL Server connection before a timeout failure.
The timeout value must be an integer value between 0 and 65534.
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

### -InputObject
Specifies the server object of the target instance.

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

## OUTPUTS

## NOTES

## RELATED LINKS

[Backup-SqlDatabase](xref:sqlserver/vlatest/Backup-SqlDatabase.md)

[Restore-SqlDatabase](xref:sqlserver/vlatest/Restore-SqlDatabase.md)
