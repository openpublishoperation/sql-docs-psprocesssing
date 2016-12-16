---
external help file: Microsoft.SqlServer.Management.PSSnapins.dll-Help.xml
online version: 
schema: 2.0.0
ms.assetid: 588A3F9A-938D-4C64-BEEE-F83D1455960C
updated_at: 12/8/2016 7:20 PM
ms.date: 12/8/2016
content_git_url: https://github.com/MicrosoftDocs/sql-docs-powershell/blob/live/sqlserver-cmdlets/sqlps/vlatest/New-SqlAvailabilityGroupListener.md
original_content_git_url: https://github.com/MicrosoftDocs/sql-docs-powershell/blob/live/sqlserver-cmdlets/sqlps/vlatest/New-SqlAvailabilityGroupListener.md
gitcommit: https://github.com/MicrosoftDocs/sql-docs-powershell/blob/b925b18b49186ab91cfeb5201e061d569d0eeae2/sqlserver-cmdlets/sqlps/vlatest/New-SqlAvailabilityGroupListener.md
ms.topic: reference
author: stevestein
ms.author: sstein
keywords: powershell, cmdlet
manager: jhubbard
open_to_public_contributors: true
ms.service: sql-server
---

# New-SqlAvailabilityGroupListener

## SYNOPSIS
Creates an availability group listener and attaches it to an availability group.

## SYNTAX

### ByPath (Default)
```
New-SqlAvailabilityGroupListener [-DhcpSubnet <String>] [-StaticIp <String[]>] [-Port <Int32>] [-Name] <String>
 [[-Path] <String>] [-Script] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### ByObject
```
New-SqlAvailabilityGroupListener [-DhcpSubnet <String>] [-StaticIp <String[]>] [-Port <Int32>] [-Name] <String>
 [-InputObject] <AvailabilityGroup> [-Script] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## DESCRIPTION
The **New-SqlAvailabilityGroupListener** cmdlet creates an availability group listener, and attaches it to an availability group.
Run this cmdlet on the server instance that hosts the primary replica.

## EXAMPLES

### Example 1: Create a listener for an availability group
```
PS C:\>New-SqlAvailabilityGroupListener -Name "MainListener" -Path "SQLSERVER:\SQL\PrimaryServer\InstanceName\AvailabilityGroups\MainAG"
```

This command creates an availability group listener named MainListener for the availability group named MainAG.
This listener acquires a virtual IP address by using DHCP.
Run this command on the server instance that hosts the primary replica.

### Example 2: Create a listener for an availability group that has a non-default port
```
PS C:\>New-SqlAvailabilityGroupListener -Name "MainListener" -Path "SQLSERVER:\SQL\PrimaryServer\InstanceName\AvailabilityGroups\MainAG" -Port 1434
```

This command creates an availability group listener named MainListener for the availability group named MainAG.
As in the previous example, this listener acquires a virtual IP address by using DHCP.
This example assigns the port 1434 on which it listens.

### Example 3: Create a listener for an availability group that uses DHCP
```
PS C:\>New-SqlAvailabilityGroupListener -Name "MainListener" -DhcpSubnet "192.169.0.1/255.255.252.0" -Path "SQLSERVER:\SQL\PrimaryServer\InstanceName\AvailabilityGroups\MainAG"
```

This command creates an availability group listener named MainListener for the availability group named MainAG.
This listener acquires a virtual IP address in the specified subnet by using DHCP.

### Example 4: Create a listener for an availability group that uses a static address
```
PS C:\>New-SqlAvailabilityGroupListener -Name "MainListener" -StaticIp "192.168.3.1/255.255.252.0" -Path "SQLSERVER:\Sql\Computer\Instance\AvailabilityGroups\MainAG"
```

This command creates an availability group listener named MainListener for the availability group named MainAG.
This listener uses the IPv4 address specified by the **StaticIp** parameter as its virtual IP address.

### Example 5: Create a script that creates a listener
```
PS C:\>New-SqlAvailabilityGroupListener -Name "MainListener" -Path "SQLSERVER:\Sql\Computer\Instance\AvailabilityGroups\MainAG" -Script
```

This command creates a Transact-SQL script that creates an availability group listener named MainListener for the availability group named MainAG.
The command does not create a listener.

## PARAMETERS

### -DhcpSubnet
Specifies an IPv4 address and subnet mask of a network.
The listener determines the address on this network by using DHCP.
Specify the address in for following format: 192.168.0.1\255.255.255.0.

If you specify this parameter, do not specify the **StaticIp** parameter.

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

### -InputObject
Specifies the availability group, as an **AvailabilityGroup** object, to which this cmdlet attaches the listener.

```yaml
Type: AvailabilityGroup
Parameter Sets: ByObject
Aliases: 

Required: True
Position: 3
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -Name
Specifies a name for the listener.

```yaml
Type: String
Parameter Sets: (All)
Aliases: 

Required: True
Position: 2
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Path
Specifies the path of the availability group to which this cmdlet attaches a listener.
If you do not specify this parameter, this cmdlet uses current working location.

```yaml
Type: String
Parameter Sets: ByPath
Aliases: 

Required: False
Position: 3
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

### -StaticIp
Specifies an array of addresses.
Each address entry is either an IPv4 address and subnet mask or an IPv6 address.
The listener listens on the addresses that this parameter specifies.

If you specify this parameter, do not specify the **DhcpSubnet** parameter.

```yaml
Type: String[]
Parameter Sets: (All)
Aliases: 

Required: False
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

### Microsoft.SqlServer.Management.Smo.AvailabilityGroup

## OUTPUTS

## NOTES

## RELATED LINKS

[Add-SqlAvailabilityGroupListenerStaticIp](xref:sqlps/vlatest/Add-SqlAvailabilityGroupListenerStaticIp.md)

[Set-SqlAvailabilityGroupListener](xref:sqlps/vlatest/Set-SqlAvailabilityGroupListener.md)


