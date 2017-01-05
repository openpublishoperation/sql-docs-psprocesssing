---
external help file: Microsoft.SqlServer.Management.PSSnapins.dll-Help.xml
online version: 
schema: 2.0.0
ms.assetid: FD28AC62-EBB8-44DC-BD6A-E75B8ECD54BA
updated_at: 1/5/2017 8:57 AM
ms.date: 1/5/2017
content_git_url: https://github.com/MicrosoftDocs/sql-docs-powershell/blob/master/sqlserver-cmdlets/sqlserver-module/vlatest/Get-SqlSmartAdmin.md
original_content_git_url: https://github.com/MicrosoftDocs/sql-docs-powershell/blob/master/sqlserver-cmdlets/sqlserver-module/vlatest/Get-SqlSmartAdmin.md
gitcommit: https://github.com/MicrosoftDocs/sql-docs-powershell/blob/0d97835841eb5cfbe37d096037375a2e0c3eb87c/sqlserver-cmdlets/sqlserver-module/vlatest/Get-SqlSmartAdmin.md
ms.topic: reference
author: stevestein
ms.author: sstein
keywords: powershell, cmdlet
manager: jhubbard
open_to_public_contributors: true
ms.service: sql-server
---

# Get-SqlSmartAdmin

## SYNOPSIS
Gets the SQL Smart Admin object and its properties.

## SYNTAX

### ByPath (Default)
```
Get-SqlSmartAdmin [-Name <String>] [-DatabaseName <String>] [-ServerInstance <PSObject>] [[-Path] <String>]
 [-Script] [-InformationAction <ActionPreference>] [-InformationVariable <String>] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

### ByObject
```
Get-SqlSmartAdmin [-Name <String>] [-DatabaseName <String>] [-ServerInstance <PSObject>]
 [-InputObject] <Server> [-Script] [-InformationAction <ActionPreference>] [-InformationVariable <String>]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

### ByName
```
Get-SqlSmartAdmin [-Name <String>] [-DatabaseName <String>] [-ServerInstance <PSObject>] [-Script]
 [-InformationAction <ActionPreference>] [-InformationVariable <String>] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

## DESCRIPTION
The **Get-SqlSmartAdmin** cmdlet gets the SQL Smart Admin object.
The Smart Admin object includes SQL Server Managed Backup to Windows  Azure configuration settings.
This cmdlet supports the following modes of operation to return the object:

- Pass the name of the server instance using the *Name* parameter. For a default instance, specify only the computer name. For a named instance, use Computername\InstanceName.
- Pass the path of the instance of SQL Server to the *Path* parameter.

## EXAMPLES

### Example 1: Get a Smart Admin object properties from a computer
```
PS C:\>Get-SqlSmartAdmin -Name "Computer\MyInstance"
```

This command gets the smart admin object properties from the computer named Computer\MyInstance.

## PARAMETERS

### -Name
Specifies the name of the instance of the SQL Server in this format: Computer\Instance.

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

### -DatabaseName
Specifies the name of the database that this cmdlet gets the SQL Smart Admin object.

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

### -ServerInstance
Specifies the name of an instance of the SQL Server.
For default instances, only specify the computer name: MyComputer.
For named instances, use the format ComputerName\InstanceName.
Both the *Name* and the *ServerInstance* parameters allow you to specify the name of the instance, but *ServerInstance* also accepts pipeline input of the Server instance name, or the **SqInstanceInfo** object.

```yaml
Type: PSObject
Parameter Sets: ByPath, ByObject
Aliases: 

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

```yaml
Type: PSObject
Parameter Sets: ByName
Aliases: 

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -Path
Specifies the path to the instance of SQL Server.
If you do not specify a value for this parameter, the cmdlet sets the path to the current working location.

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
Indicates that this cmdlet runs a Transact-SQL script that performs the task.

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
Specifies the instance of the **Server** object.

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

[Set-SqlSmartAdmin](xref:sqlserver-module/vlatest/Set-SqlSmartAdmin.md)

[Test-SqlSmartAdmin](xref:sqlserver-module/vlatest/Test-SqlSmartAdmin.md)
