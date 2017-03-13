---
external help file: Microsoft.SqlServer.Management.PSSnapins.dll-Help.xml
online version: 
schema: 2.0.0
ms.assetid: D15D3DE9-B1B2-45F7-A80B-D62E837D8C43
updated_at: 1/4/2017 6:38 PM
ms.date: 1/4/2017
content_git_url: https://github.com/MicrosoftDocs/sql-docs-powershell/blob/live/sqlserver-cmdlets/sqlps/vlatest/New-SqlAvailabilityReplica.md
original_content_git_url: https://github.com/MicrosoftDocs/sql-docs-powershell/blob/live/sqlserver-cmdlets/sqlps/vlatest/New-SqlAvailabilityReplica.md
gitcommit: https://github.com/MicrosoftDocs/sql-docs-powershell/blob/4c48bd1c26220ff873e612527853aeeef98777da/sqlserver-cmdlets/sqlps/vlatest/New-SqlAvailabilityReplica.md
ms.topic: reference
author: stevestein
ms.author: sstein
keywords: powershell, cmdlet
manager: jhubbard
open_to_public_contributors: True
ms.service: sql-server
---

# New-SqlAvailabilityReplica

## SYNOPSIS
Creates an availability replica.

## SYNTAX

### ByPath (Default)
```
New-SqlAvailabilityReplica -AvailabilityMode <AvailabilityReplicaAvailabilityMode>
 -FailoverMode <AvailabilityReplicaFailoverMode> -EndpointUrl <String> [-SessionTimeout <Int32>]
 [-ConnectionModeInPrimaryRole <AvailabilityReplicaConnectionModeInPrimaryRole>]
 [-ConnectionModeInSecondaryRole <AvailabilityReplicaConnectionModeInSecondaryRole>] [-BackupPriority <Int32>]
 [-ReadOnlyRoutingList <String[]>] [-ReadonlyRoutingConnectionUrl <String>] [-Name] <String> [[-Path] <String>]
 [-Script] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### AsTemplate
```
New-SqlAvailabilityReplica -AvailabilityMode <AvailabilityReplicaAvailabilityMode>
 -FailoverMode <AvailabilityReplicaFailoverMode> -EndpointUrl <String> [-SessionTimeout <Int32>]
 [-ConnectionModeInPrimaryRole <AvailabilityReplicaConnectionModeInPrimaryRole>]
 [-ConnectionModeInSecondaryRole <AvailabilityReplicaConnectionModeInSecondaryRole>] [-BackupPriority <Int32>]
 [-ReadOnlyRoutingList <String[]>] [-ReadonlyRoutingConnectionUrl <String>] [-AsTemplate]
 [-Version <ServerVersion>] [-Name] <String> [-Script] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### ByObject
```
New-SqlAvailabilityReplica -AvailabilityMode <AvailabilityReplicaAvailabilityMode>
 -FailoverMode <AvailabilityReplicaFailoverMode> -EndpointUrl <String> [-SessionTimeout <Int32>]
 [-ConnectionModeInPrimaryRole <AvailabilityReplicaConnectionModeInPrimaryRole>]
 [-ConnectionModeInSecondaryRole <AvailabilityReplicaConnectionModeInSecondaryRole>] [-BackupPriority <Int32>]
 [-ReadOnlyRoutingList <String[]>] [-ReadonlyRoutingConnectionUrl <String>] [-Name] <String>
 [-InputObject] <AvailabilityGroup> [-Script] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## DESCRIPTION
The **New-SqlAvailabilityReplica** cmdlet creates an availability replica.
Run this cmdlet on the instance of SQL Server that hosts the primary replica.

To create an availability replica before you create an availability group, specify the *AsTemplate* parameter.
To add a replica to an existing availability group, either the **InputObject** or *Path* parameter specifies the availability group.

## EXAMPLES

### Example 1: Creates a representation of an availability replica
```
PS C:\> $ServerObject = Get-Item "SQLSERVER:\Sql\PrimaryServer\InstanceName"
PS C:\> New-SqlAvailabilityReplica -Name "PrimaryServer\Instance" -EndpointUrl "TCP://PrimaryServerName.domain.com:5022" -FailoverMode Automatic -AvailabilityMode SynchronousCommit -AsTemplate -Version $ServerObject.Version
```

This example creates an in-memory representation of an availability replica.
No changes are committed to the server.
You can use this replica as a value for the *AvailabilityReplica* parameter of [New-SqlAvailabilityGroup](./New-SqlAvailabilityGroup.md)

The first command gets an instance of the primary server.

The second command creates the availability replica.
This replica uses the database mirroring endpoint located at the specified URL to communicate with other replicas in the availability group.
This replica supports automatic failover and the synchronous-commit availability mode. 
The *Version* parameter specifies the version of the server instance that will host this new replica.

### Example 2: Creates an availability replica that supports manual failover and the asynchronous-commit
```
PS C:\> $ServerObject = Get-Item "SQLSERVER:\Sql\PrimaryServer\InstanceName"
PS C:\> New-SqlAvailabilityReplica -Name "SecondaryServer\Instance" -EndpointUrl "TCP://PrimaryServerName.domain.com:5022" -FailoverMode Manual -AvailabilityMode AsynchronousCommit -AsTemplate -Version $ServerObject.Version
```

This example creates an in-memory representation of an availability replica.
No changes are committed to the server.

The first command gets an instance of the primary server.

The second command creates the availability replica.
This replica uses the database mirroring endpoint located at the specified URL to communicate with other replicas in the availability group.
This replica supports manual failover and the asynchronous-commit availability mode.
The *Version* parameter specifies the version of the server instance that will host this new replica.

### Example 3: Add an availability replica to an availability group
```
PS C:\> New-SqlAvailabilityReplica -Name "SecondaryServer\Instance" -EndpointUrl "TCP://PrimaryServerName.domain.com:5022" -FailoverMode Manual -AvailabilityMode AsynchronousCommit -ConnectionModeInSecondaryRole AllowAllConnections -Path "SQLSERVER:\Sql\PrimaryServer\InstanceName\AvailabilityGroups\MainAG"
```

This command adds an availability replica to an existing availability group named MainAG.
This replica supports manual failover and asynchronous-commit availability mode.
In the secondary role, this replica supports read access connections.
This configuration lets you offload read-only processing to this replica.

## PARAMETERS

### -AsTemplate
Indicates that this cmdlet creates a temporary **AvailabilityReplica** object in memory.
Specify this parameter to create an availability group before you create an availability replica.
Create an availability group by using the New-SqlAvailabilityGroup cmdlet.
Specify the temporary availability replica as the value of the *AvailabilityReplica* parameter.

If you specify *AsTemplate*, this cmdlet ignores values for the **InputObject** and *Path* parameters.

If you specify this parameter, you must also specify  a SQL Server version for the *Version* parameter, or your current session must have an active connection to an instance.

```yaml
Type: SwitchParameter
Parameter Sets: AsTemplate
Aliases: 

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

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

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -BackupPriority
Specifies the desired priority of the replicas in performing backups.
The acceptable values for this parameter are: integers from 0 through 100.
Of the set of replicas which are online and available, the replica that has the highest priority performs the backup.

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
Allow read/write connections
- AllowAllConnections.
Allow all connections

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
Disallows connections
- AllowReadIntentConnectionsOnly.
Allows only read-intent connections
- AllowAllConnections.
Allows all connections

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

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -FailoverMode
Specifies the failover mode.
The acceptable values for this parameter are:

- Automatic 
- Manual You can specify a value of $Null.

```yaml
Type: AvailabilityReplicaFailoverMode
Parameter Sets: (All)
Aliases: 

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -InputObject
Specifies the availability group, as an **AvailabilityGroup** object, to which the replica belongs.

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
Specifies a name for the availability replica in the following format: 

Computer\Instance

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
Specifies the path of the availability group to which the replica belongs.
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

### -Version
Specifies a SQL Server version.
If you specify the *AsTemplate* parameter, you must specify a version.
The template object is created in design mode on a server that includes this version.
You can specify an integer or a string, as in the following examples: 

- 13 
- "13.0.0"

```yaml
Type: ServerVersion
Parameter Sets: AsTemplate
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

### Microsoft.SqlServer.Management.Smo.AvailabilityGroup
You can pass an availability group to this cmdlet.

## OUTPUTS

### Microsoft.SqlServer.Management.Smo.AvailabilityReplica
This cmdlet returns an availability replica.

## NOTES

## RELATED LINKS

[New-SqlAvailabilityGroup](xref:sqlps/vlatest/New-SqlAvailabilityGroup.md)

[Set-SqlAvailabilityReplica](xref:sqlps/vlatest/Set-SqlAvailabilityReplica.md)

[Test-SqlAvailabilityReplica](xref:sqlps/vlatest/Test-SqlAvailabilityReplica.md)
