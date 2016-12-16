---
external help file: Microsoft.SqlServer.Management.PSSnapins.dll-Help.xml
online version: 
schema: 2.0.0
ms.assetid: 18A59A49-87C3-48C3-99ED-8371D76E89C1
updated_at: 12/8/2016 7:20 PM
ms.date: 12/8/2016
content_git_url: https://github.com/MicrosoftDocs/sql-docs-powershell/blob/live/sqlserver-cmdlets/sqlps/vlatest/Add-SqlAvailabilityGroupListenerStaticIp.md
original_content_git_url: https://github.com/MicrosoftDocs/sql-docs-powershell/blob/live/sqlserver-cmdlets/sqlps/vlatest/Add-SqlAvailabilityGroupListenerStaticIp.md
gitcommit: https://github.com/MicrosoftDocs/sql-docs-powershell/blob/b925b18b49186ab91cfeb5201e061d569d0eeae2/sqlserver-cmdlets/sqlps/vlatest/Add-SqlAvailabilityGroupListenerStaticIp.md
ms.topic: reference
author: stevestein
ms.author: sstein
keywords: powershell, cmdlet
manager: jhubbard
open_to_public_contributors: true
ms.service: sql-server
---

# Add-SqlAvailabilityGroupListenerStaticIp

## SYNOPSIS
Adds a static IP address to an availability group listener.

## SYNTAX

### ByPath (Default)
```
Add-SqlAvailabilityGroupListenerStaticIp -StaticIp <String[]> [[-Path] <String[]>] [-Script] [-WhatIf]
 [-Confirm] [<CommonParameters>]
```

### ByObject
```
Add-SqlAvailabilityGroupListenerStaticIp -StaticIp <String[]> [-InputObject] <AvailabilityGroupListener[]>
 [-Script] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## DESCRIPTION
The **Add-SqlAvailabilityGroupListenerStaticIp** cmdlet adds a static IP address to an existing availability group listener configuration.
You can specify either an IPv4 address and subnet mask or an IPv6 address  Run this cmdlet on the server instance that hosts the primary replica.

## EXAMPLES

### Example 1: Add an IPv4 address
```
PS C:\>Add-SqlAvailabilityGroupListenerStaticIp -Path "SQLSERVER:\SQL\PrimaryServer\InstanceName\AvailabilityGroups\MainAG\AvailabilityGroupListeners\MainListener" -StaticIp "192.169.0.1/255.255.252.0"
```

This command adds a static IPv4 address to the availability group listener MainListener on the availability group named MainAG.
This IPv4 address serves as the virtual IP address of the listener on the subnet 255.255.252.0.
If the availability group spans multiple subnets, add a static IP address for each subnet to the listener.
Run this cmdlet  on the server instance that hosts the primary replica.

### Example 2: Add an IPv6 address
```
PS C:\>Add-SqlAvailabilityGroupListenerStaticIp -Path "SQLSERVER:\SQL\PrimaryServer\InstanceName\AvailabilityGroups\MainAG\AvailabilityGroupListeners\MainListener" -StaticIp "2001:0db8:85a3:0000:0000:8a2e:0370:7334"
```

This command adds a static IPv6 address to the listener MainListener on the availability group MainAG.

### Example 3: Create a script that adds an IPv4 address
```
PS C:\>Add-SqlAvailabilityGroupListenerStaticIp -Path "SQLSERVER:\SQL\PrimaryServer\InstanceName\AvailabilityGroups\MainAg\AvailabilityGroupListeners\MainListener" -StaticIp "192.168.0.1/255.255.255.0" -Script
```

This creates a Transact-SQL script that adds a static IPv4 address to the availability group listener MainListener on the availability group named 'MainAG'.

## PARAMETERS

### -InputObject
Specifies the listener, as an **AvailabilityGroupListener** object, that this cmdlet modifies.

```yaml
Type: AvailabilityGroupListener[]
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
Type: String[]
Parameter Sets: ByPath
Aliases: 

Required: False
Position: 2
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

### -StaticIp
Specifies an array of addresses.
Each address entry is either an IPv4 address and subnet mask or an IPv6 address.
The listener listens on the addresses that this parameter specifies.

```yaml
Type: String[]
Parameter Sets: (All)
Aliases: 

Required: True
Position: Named
Default value: None
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

### CommonParameters
This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable. For more information, see about_CommonParameters (http://go.microsoft.com/fwlink/?LinkID=113216).

## INPUTS

### Microsoft.SqlServer.Management.Smo.AvailabilityGroupListener

## OUTPUTS

## NOTES

## RELATED LINKS

[New-SqlAvailabilityGroupListener](xref:sqlps/vlatest/New-SqlAvailabilityGroupListener.md)

[Set-SqlAvailabilityGroupListener](xref:sqlps/vlatest/Set-SqlAvailabilityGroupListener.md)


