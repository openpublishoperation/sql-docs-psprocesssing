---
external help file: Microsoft.SqlServer.Management.PSSnapins.dll-Help.xml
online version: 
schema: 2.0.0
ms.assetid: 42BB2AC3-905C-4306-B504-464DCFCEE599
updated_at: 1/4/2017 6:38 PM
ms.date: 1/4/2017
content_git_url: https://github.com/MicrosoftDocs/sql-docs-powershell/blob/live/sqlserver-cmdlets/sqlps/vlatest/Set-SqlAvailabilityGroupListener.md
original_content_git_url: https://github.com/MicrosoftDocs/sql-docs-powershell/blob/live/sqlserver-cmdlets/sqlps/vlatest/Set-SqlAvailabilityGroupListener.md
gitcommit: https://github.com/MicrosoftDocs/sql-docs-powershell/blob/4c48bd1c26220ff873e612527853aeeef98777da/sqlserver-cmdlets/sqlps/vlatest/Set-SqlAvailabilityGroupListener.md
ms.topic: reference
author: stevestein
ms.author: sstein
keywords: powershell, cmdlet
manager: jhubbard
open_to_public_contributors: True
ms.service: sql-server
---

# Set-SqlAvailabilityGroupListener

## SYNOPSIS
Sets the port setting on an availability group listener.

## SYNTAX

### ByPath (Default)
```
Set-SqlAvailabilityGroupListener [-Port <Int32>] [[-Path] <String>] [-Script] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

### ByObject
```
Set-SqlAvailabilityGroupListener [-Port <Int32>] [-InputObject] <AvailabilityGroupListener> [-Script] [-WhatIf]
 [-Confirm] [<CommonParameters>]
```

## DESCRIPTION
The **Set-SqlAvailabilityGroupListener** cmdlet modifies the port setting on an existing availability group listener.
Run this cmdlet on the server instance that hosts the primary replica.

## EXAMPLES

### Example 1: Modify a listener for an availability group
```
PS C:\> Set-SqlAvailabilityGroupListener -Port 1535 -Path "SQLSERVER:\Sql\PrimaryServer\InstanceName\AvailabilityGroups\MainAG\AvailabilityGroupListeners\MainListener"
```

This command sets the port number for the availability group listener named MainListener to be 1535.
This port is used to listen for connections to the listener.

### Example 2: Create a script that modifies a listener
```
PS C:\> Set-SqlAvailabilityGroupListener -Port 1535 -Script -Path "SQLSERVER:\Sql\PrimaryServer\InstanceName\AvailabilityGroups\MainAG\AvailabilityGroupListeners\MainListener"
```

This command generates the Transact-SQL script that sets the port number for the availability group listener named MainListener to 1535.
This command does not make that change.

## PARAMETERS

### -InputObject
Specifies the listener, as an **AvailabilityGroupListener** object, that this cmdlet modifies.

```yaml
Type: AvailabilityGroupListener
Parameter Sets: ByObject
Aliases: 

Required: True
Position: 2
Default value: None
Accept pipeline input: True (ByValue)
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
Position: 2
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

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

### Microsoft.SqlServer.Management.Smo.AvailabilityGroupListener

## OUTPUTS

## NOTES

## RELATED LINKS

[Add-SqlAvailabilityGroupListenerStaticIp](xref:sqlps/vlatest/Add-SqlAvailabilityGroupListenerStaticIp.md)

[New-SqlAvailabilityGroupListener](xref:sqlps/vlatest/New-SqlAvailabilityGroupListener.md)
