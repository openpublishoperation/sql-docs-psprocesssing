---
external help file: Microsoft.SqlServer.Management.PSSnapins.dll-Help.xml
online version: 
schema: 2.0.0
ms.assetid: 42BB2AC3-905C-4306-B504-464DCFCEE599
updated_at: 12/13/2016 8:09 PM
ms.date: 12/13/2016
content_git_url: https://github.com/MicrosoftDocs/sql-docs-powershell/blob/master/sqlserver-cmdlets/sqlserver-module/vlatest/Set-SqlAvailabilityGroupListener.md
original_content_git_url: https://github.com/MicrosoftDocs/sql-docs-powershell/blob/master/sqlserver-cmdlets/sqlserver-module/vlatest/Set-SqlAvailabilityGroupListener.md
gitcommit: https://github.com/MicrosoftDocs/sql-docs-powershell/blob/f97823fbeb2d71358573a8e4b5c2c322a3a5c138/sqlserver-cmdlets/sqlserver-module/vlatest/Set-SqlAvailabilityGroupListener.md
ms.topic: reference
author: stevestein
ms.author: sstein
keywords: powershell, cmdlet
manager: jhubbard
open_to_public_contributors: true
ms.service: sql-server
---

# Set-SqlAvailabilityGroupListener

## SYNOPSIS
Sets the port setting on an availability group listener.

## SYNTAX

### ByPath (Default)
```
Set-SqlAvailabilityGroupListener [-Port <Int32>] [[-Path] <String>] [-Script]
 [-InformationAction <ActionPreference>] [-InformationVariable <String>] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

### ByObject
```
Set-SqlAvailabilityGroupListener [-Port <Int32>] [-InputObject] <AvailabilityGroupListener> [-Script]
 [-InformationAction <ActionPreference>] [-InformationVariable <String>] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

## DESCRIPTION
The **Set-SqlAvailabilityGroupListener** cmdlet modifies the port setting on an existing availability group listener.
Run this cmdlet on the server instance that hosts the primary replica.

## EXAMPLES

### Example 1: Modify a listener for an availability group
```
PS C:\>Set-SqlAvailabilityGroupListener -Port 1535 -Path "SQLSERVER:\Sql\PrimaryServer\InstanceName\AvailabilityGroups\MainAG\AvailabilityGroupListeners\MainListener"
```

This command sets the port number for the availability group listener named MainListener to be 1535.
This port is used to listen for connections to the listener.

### Example 2: Create a script that modifies a listener
```
PS C:\>Set-SqlAvailabilityGroupListener -Port 1535 -Script -Path "SQLSERVER:\Sql\PrimaryServer\InstanceName\AvailabilityGroups\MainAG\AvailabilityGroupListeners\MainListener"
```

This command generates the Transact-SQL script that sets the port number for the availability group listener named MainListener to 1535.
This command does not make that change.

## PARAMETERS

### -Port
Specifies the port on which the listener listens for connections.
The default port is TCP port 1433.

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

### -Path
Specifies the path of the availability group listener that this cmdlet modifies.
If you do not specify this parameter, this cmdlet uses current working location.

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
Specifies the listener, as an **AvailabilityGroupListener** object, that this cmdlet modifies.

```yaml
Type: AvailabilityGroupListener
Parameter Sets: ByObject
Aliases: 

Required: True
Position: 1
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### CommonParameters
This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable. For more information, see about_CommonParameters (http://go.microsoft.com/fwlink/?LinkID=113216).

## INPUTS

### Microsoft.SqlServer.Management.Smo.AvailabilityGroupListener

## OUTPUTS

## NOTES

## RELATED LINKS

[Add-SqlAvailabilityGroupListenerStaticIp](xref:sqlserver-module/vlatest/Add-SqlAvailabilityGroupListenerStaticIp.md)

[New-SqlAvailabilityGroupListener](xref:sqlserver-module/vlatest/New-SqlAvailabilityGroupListener.md)


