---
external help file: Microsoft.SqlServer.Management.PSSnapins.dll-Help.xml
online version: 
schema: 2.0.0
ms.assetid: 87470C13-E3F0-4709-AA61-8F740CC5AD99
updated_at: 1/4/2017 6:38 PM
ms.date: 1/4/2017
content_git_url: https://github.com/MicrosoftDocs/sql-docs-powershell/blob/master/sqlserver-cmdlets/sqlps/vlatest/Set-SqlAvailabilityReplica.md
original_content_git_url: https://github.com/MicrosoftDocs/sql-docs-powershell/blob/master/sqlserver-cmdlets/sqlps/vlatest/Set-SqlAvailabilityReplica.md
gitcommit: https://github.com/MicrosoftDocs/sql-docs-powershell/blob/4c48bd1c26220ff873e612527853aeeef98777da/sqlserver-cmdlets/sqlps/vlatest/Set-SqlAvailabilityReplica.md
ms.topic: reference
author: stevestein
ms.author: sstein
keywords: powershell, cmdlet
manager: jhubbard
open_to_public_contributors: True
ms.service: sql-server
---

# Set-SqlAvailabilityReplica

## SYNOPSIS
Sets the settings on an availability replica.

## SYNTAX

### ByPath (Default)
```
Set-SqlAvailabilityReplica [-AvailabilityMode <AvailabilityReplicaAvailabilityMode>]
 [-FailoverMode <AvailabilityReplicaFailoverMode>] [-EndpointUrl <String>] [-SessionTimeout <Int32>]
 [-ConnectionModeInPrimaryRole <AvailabilityReplicaConnectionModeInPrimaryRole>]
 [-ConnectionModeInSecondaryRole <AvailabilityReplicaConnectionModeInSecondaryRole>] [-BackupPriority <Int32>]
 [-ReadOnlyRoutingList <String[]>] [-ReadonlyRoutingConnectionUrl <String>] [[-Path] <String>] [-Script]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

### ByObject
```
Set-SqlAvailabilityReplica [-AvailabilityMode <AvailabilityReplicaAvailabilityMode>]
 [-FailoverMode <AvailabilityReplicaFailoverMode>] [-EndpointUrl <String>] [-SessionTimeout <Int32>]
 [-ConnectionModeInPrimaryRole <AvailabilityReplicaConnectionModeInPrimaryRole>]
 [-ConnectionModeInSecondaryRole <AvailabilityReplicaConnectionModeInSecondaryRole>] [-BackupPriority <Int32>]
 [-ReadOnlyRoutingList <String[]>] [-ReadonlyRoutingConnectionUrl <String>]
 [-InputObject] <AvailabilityReplica> [-Script] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## DESCRIPTION
The **Set-SqlAvailabilityReplica** cmdlet sets or modifies a variety of properties for an availability replica.
Run this cmdlet on the server instance that hosts the primary replica.

## EXAMPLES

### Example 1: Modify a replica availability mode and automatic failover
```
PS C:\> Set-SqlAvailabilityReplica -AvailabilityMode "SynchronousCommit" -FailoverMode Automatic -Path "SQLSERVER:\Sql\PrimaryServer\InstanceName\AvailabilityGroups\MainAG\AvailabilityReplicas\Replica02"
```

This command modifies the replica named Replica02 in the availability group named MainAG to use synchronous-commit availability mode and to support automatic failover.

### Example 2: Modify a replica to support forced manual failover
```
PS C:\> Set-SqlAvailabilityReplica -AvailabilityMode AsynchronousCommit -FailoverMode Manual -Path "SQLSERVER:\Sql\PrimaryServer\InstanceName\AvailabilityGroups\MainAG\AvailabilityReplicas\Replica02"
```

This command modifies the replica named Replica02 in the availability group named MainAG to use asynchronous-commit availability mode and to support only forced manual failover, which could incur data loss.

### Example 3: Allow all connections in the secondary role
```
PS C:\> Set-SqlAvailabilityReplica -ConnectionModeInSecondaryRole AllowAllConnections -Path "SQLSERVER:\Sql\PrimaryServer\InstanceName\AvailabilityGroups\MainAG\AvailabilityReplicas\Replica02"
```

This command modifies the replica 'Replica02' in the availability group MainAG to allow all connections in the secondary role.
This lets you offload read-only data processing workloads to secondary replicas.

### Example 4: Configure a primary replica and secondary replica for read-only routing
```
PS C:\> Set-Location "SQLSERVER:\SQL\PrimaryServer\default\AvailabilityGroups\MainAG"
C:\PS> $PrimaryReplica = Get-Item "AvailabilityReplicas\PrimaryServer"
C:\PS> $SecondaryReplica = Get-Item "AvailabilityReplicas\SecondaryServer"
C:\PS> Set-SqlAvailabilityReplica -ReadOnlyRoutingConnectionUrl "TCP://PrimaryServer.domain.com:5022" -InputObject $PrimaryReplica
C:\PS> Set-SqlAvailabilityReplica -ReadOnlyRoutingConnectionUrl "TCP://SecondaryServer.domain.com:5022" -InputObject $SecondaryReplica
C:\PS> Set-SqlAvailabilityReplica -ReadOnlyRoutingList "SecondaryServer","PrimaryServer" -InputObject $PrimaryReplica
```

The first command changes location to a location in the SQLSERVER: provider.

The second command gets the replica for the primary server, and then stores it in the $PrimaryReplica variable.

The third command gets the replica for the secondary server, and then stores it in the $SecondaryReplica variable.

The fourth command assigns a read-only routing URL to the primary replica.
Then it sets the read-only routing list on the primary replica.

The fifth command assigns a read-only routing URL to the secondary replica.

The sixth command sets the read-only routing list on the primary replica.
Connections that have with the **ReadOnly** property connection string are redirected to the secondary replica.
If the secondary replica is not readable, the connection is directed back to the primary replica.

### Example 5: Modify backup priority
```
PS C:\> Set-SqlAvailabilityReplica -BackupPriority 60 -Path "SQLSERVER:\Sql\Computer\Instance\AvailabilityGroups\MainAG\AvailabilityReplicas\Replica02"
```

This command sets the backup priority of the availability replica 'Replica02' to 60.
This priority is used by the server instance that hosts the primary replica to decide which replica should service an automated backup request on a database in the availability group.
The replica that has the highest priority is chosen.

## PARAMETERS

### -AvailabilityMode
Specifies the replica availability mode.
The acceptable values for this parameter are:

- SynchronousCommit 
- AsynchronousCommit

You can specify a value of $Null.

```yaml
Type: AvailabilityReplicaAvailabilityMode
Parameter Sets: (All)
Aliases: 

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -BackupPriority
Specifies the desired priority of the replicas in performing backups.
The acceptable values for this parameter are: integers from 0 through 100.
Of the set of replicas which are online and available, the replica that has the highest priority performs the backup.

A value of zero (0) indicates that the replica is not a candidate.

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

### -ConnectionModeInPrimaryRole
Specifies how the availability replica handles connections when in the primary role.
The acceptable values for this parameter are:

- AllowReadWriteConnections.
Allow read/write connections.
- AllowAllConnections.
Allow all connections.

```yaml
Type: AvailabilityReplicaConnectionModeInPrimaryRole
Parameter Sets: (All)
Aliases: 

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ConnectionModeInSecondaryRole
Specifies how the availability replica handles connections when in the secondary role.
The acceptable values for this parameter are:

- AllowNoConnections.
Disallow connections.
- AllowReadIntentConnectionsOnly.
Allow only read-intent connections.
- AllowAllConnections.
Allow all connections.

```yaml
Type: AvailabilityReplicaConnectionModeInSecondaryRole
Parameter Sets: (All)
Aliases: 

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -EndpointUrl
Specifies the URL of the database mirroring endpoint.
This URL is a TCP address in the following form: 

TCP://system-address:port

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

### -FailoverMode
Specifies the failover mode.
The acceptable values for this parameter are:

- Automatic 
- Manual.
You can specify a value of $Null.

```yaml
Type: AvailabilityReplicaFailoverMode
Parameter Sets: (All)
Aliases: 

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -InputObject
Specifies the availability group, as an **AvailabilityGroup** object, to which the replica belongs.

```yaml
Type: AvailabilityReplica
Parameter Sets: ByObject
Aliases: 

Required: True
Position: 2
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -Path
Specifies the path of the availability group to which the replica belongs.
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

### -ReadonlyRoutingConnectionUrl
Specifies the fully-qualified domain name (FQDN) and port to use when routing to the replica for read only connections, as in the following example: 

`TCP://DBSERVER8.manufacturing.Contoso.com:7024`

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

### -ReadOnlyRoutingList
Specifies an ordered list of replica server names that represent the probe sequence for connection director to use when redirecting read-only connections through this availability replica.
This parameter applies if the availability replica is the current primary replica of the availability group.

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

### -SessionTimeout
Specifies the amount of time, in seconds, to wait for a response between the primary replica and this replica before the connection fails.

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

### Microsoft.SqlServer.Management.Smo.AvailabilityReplica

## OUTPUTS

## NOTES

## RELATED LINKS

[New-SqlAvailabilityReplica](xref:sqlps/vlatest/New-SqlAvailabilityReplica.md)

[Test-SqlAvailabilityReplica](xref:sqlps/vlatest/Test-SqlAvailabilityReplica.md)
