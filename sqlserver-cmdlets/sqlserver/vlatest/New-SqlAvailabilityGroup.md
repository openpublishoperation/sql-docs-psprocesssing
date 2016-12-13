---
external help file: Microsoft.SqlServer.Management.PSSnapins.dll-Help.xml
online version: 
schema: 2.0.0
ms.assetid: EEBC7D3F-7161-4474-AE0D-6F64A5009BA3
updated_at: 12/8/2016 7:20 PM
ms.date: 12/8/2016
content_git_url: https://github.com/MicrosoftDocs/sql-docs-powershell/blob/master/sqlserver-cmdlets/sqlserver/vlatest/New-SqlAvailabilityGroup.md
original_content_git_url: https://github.com/MicrosoftDocs/sql-docs-powershell/blob/master/sqlserver-cmdlets/sqlserver/vlatest/New-SqlAvailabilityGroup.md
gitcommit: https://github.com/MicrosoftDocs/sql-docs-powershell/blob/b925b18b49186ab91cfeb5201e061d569d0eeae2/sqlserver-cmdlets/sqlserver/vlatest/New-SqlAvailabilityGroup.md
ms.topic: reference
author: stevestein
ms.author: sstein
keywords: powershell, cmdlet
manager: jhubbard
open_to_public_contributors: true
ms.service: sql-server
---

# New-SqlAvailabilityGroup

## SYNOPSIS
Creates an availability group.

## SYNTAX

### ByPath (Default)
```
New-SqlAvailabilityGroup -AvailabilityReplica <AvailabilityReplica[]> [-Database <String[]>]
 [-AutomatedBackupPreference <AvailabilityGroupAutomatedBackupPreference>]
 [-FailureConditionLevel <AvailabilityGroupFailureConditionLevel>] [-HealthCheckTimeout <Int32>]
 [-BasicAvailabilityGroup] [-DatabaseHealthTrigger] [-DtcSupportEnabled] [-Name] <String> [[-Path] <String>]
 [-Script] [-InformationAction <ActionPreference>] [-InformationVariable <String>] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

### ByObject
```
New-SqlAvailabilityGroup -AvailabilityReplica <AvailabilityReplica[]> [-Database <String[]>]
 [-AutomatedBackupPreference <AvailabilityGroupAutomatedBackupPreference>]
 [-FailureConditionLevel <AvailabilityGroupFailureConditionLevel>] [-HealthCheckTimeout <Int32>]
 [-BasicAvailabilityGroup] [-DatabaseHealthTrigger] [-DtcSupportEnabled] [-Name] <String>
 [-InputObject] <Server> [-Script] [-InformationAction <ActionPreference>] [-InformationVariable <String>]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

## DESCRIPTION
The **New-SqlAvailabilityGroup** cmdlet creates an availability group in AlwaysOn Availability Groups.
The **InputObject** or **Path** parameter specifies the server that hosts the initial primary replica.

## EXAMPLES

### Example 1: Create an availability group
```
PS C:\>$PrimaryServer = Get-Item "SQLSERVER:\SQL\PrimaryServer\Instance22"
PS C:\>$SecondaryServer = Get-Item "SQLSERVER:\SQL\SecondaryServer\Instance22"
PS C:\>$PrimaryReplica = New-SqlAvailabilityReplica -Name "PrimaryServer\Instance22" -EndpointUrl "TCP://PrimaryServer.domain:5022" -FailoverMode "Automatic" -AvailabilityMode "SynchronousCommit" -AsTemplate -Version ($PrimaryServer.Version)
PS C:\>$SecondaryReplica = New-SqlAvailabilityReplica -Name "SecondaryServer\Instance22" -EndpointUrl "TCP://SecondaryServer.domain:5022" -FailoverMode "Automatic" -AvailabilityMode "SynchronousCommit" -AsTemplate -Version ($SecondaryServer.Version) 
PS C:\>New-SqlAvailabilityGroup -InputObject $PrimaryServer -Name "MainAG" -AvailabilityReplica ($PrimaryReplica, $SecondaryReplica) -Database @("Database01","Database02")
```

The first command gets an instance of SQL Server on the primary server, and then stores it in the **$PrimaryServer** variable.

The second command gets an instance of SQL Server on the secondary server, and then stores it in the **$SecondaryServer** variable.

The third command creates a replica that includes the primary server instance by using the **New-SqlAvailabilityReplica** cmdlet, and then stores it in the **$PrimaryReplica** variable.
The command specifies the version of the server instance by using the **Version** property of **$PrimaryServer**.

The fourth command creates a replica that includes the secondary server instance by using **New-SqlAvailabilityReplica**, and then stores it in the **$SeconayrReplica** variable.
The command specifies the version of the server instance by using the **Version** property of **$SeconardyServer**.

The final command creates the availability group.
It specifies the name, the primary server, the replicas, and other information.

## PARAMETERS

### -AvailabilityReplica
Specifies an array of availability replicas that this cmdlet includes in the availability group.
To obtain an **AvailabilityReplica**, use the New-SqlAvailabilityReplica cmdlet.
Specify the **AsTemplate** parameter.

```yaml
Type: AvailabilityReplica[]
Parameter Sets: (All)
Aliases: 

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Database
Specifies an array of local, read/write user databases.
These databases must use the full recovery model and must not use AUTO_CLOSE.
These databases cannot belong to another availability group and cannot be configured for database mirroring.
You must specify a value for this parameter.

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

### -AutomatedBackupPreference
Specifies the automated backup preference for the availability group.
The acceptable values for this parameter are:

- Primary.
Specifies that the backups always occur on the primary replica.
This option supports the use of features not available when backup runs on a secondary replica, such as differential backups.
- SecondaryOnly.
Specifies that backups are never performed on primary replicas.
If the primary replica is the only replica online, the backup does not occur.
- Secondary.
Specifies that backups occur on secondary replicas, unless the primary replica is the only replica online.
Then the backup occurs on the primary replica.
- None.
Specifies that the primary or secondary status is not taken into account when deciding which replica performs backups.
Instead, backup priority and online status determine which replica performs backups.

```yaml
Type: AvailabilityGroupAutomatedBackupPreference
Parameter Sets: (All)
Aliases: 

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -FailureConditionLevel
Specifies the automatic failover behavior of the availability group.
The acceptable values for this parameter are:

- OnServerDown.
Failover or restart if the SQL Server service stops.
- OnServerUnresponsive.
Failover or restart if any condition of lower value is satisfied, plus when the SQL Server service is connected to the cluster and the **HealthCheckTimeout** threshold is exceeded, or if the availability replica currently in primary role is in a failed state. 
- OnCriticalServerError.
Failover or restart if any condition of lower value is satisfied, plus when an internal critical Server error occurs, which include out of memory condition, serious write-access violation, or too much dumping. 
- OnModerateServerError.
Failover or restart if any condition of lower value is satisfied, plus if a moderate Server error occurs, which includes persistent out of memory condition. 
- OnAnyQualifiedFailureConditions.
Failover or restart if any condition of lower value is satisfied, plus if a qualifying failure condition occurs, which includes engine worker thread exhaustion and unsolvable deadlock detected.

```yaml
Type: AvailabilityGroupFailureConditionLevel
Parameter Sets: (All)
Aliases: 

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -HealthCheckTimeout
Specifies the length of time, in milliseconds, after which AlwaysOn availability groups declare an unresponsive server to be unhealthy.

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

### -BasicAvailabilityGroup


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

### -DatabaseHealthTrigger


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

### -DtcSupportEnabled


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

### -Name
Specifies the name of the availability group that this cmdlet creates.

```yaml
Type: String
Parameter Sets: (All)
Aliases: 

Required: True
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Path
Specifies the path of the instance of SQL Server that hosts the initial primary replica of the availability group that this cmdlet creates.
If you do not specify this parameter, this cmdlet uses current working location.
If you specify a value, the path must currently exist.

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
Specifies the instance of SQL Server that hosts the primary replica of the availability group that this cmdlet creates.

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

### Microsoft.SqlServer.Management.Smo.Server
You can pass a server instance to this cmdlet.

## OUTPUTS

### Microsoft.SqlServer.Management.Smo.AvailabilityGroup
This cmdlet returns an availability group.

## NOTES

## RELATED LINKS

[Join-SqlAvailabilityGroup](xref:sqlserver/vlatest/Join-SqlAvailabilityGroup.md)

[New-SqlAvailabilityReplica](xref:sqlserver/vlatest/New-SqlAvailabilityReplica.md)

[Remove-SqlAvailabilityGroup](xref:sqlserver/vlatest/Remove-SqlAvailabilityGroup.md)

[Set-SqlAvailabilityGroup](xref:sqlserver/vlatest/Set-SqlAvailabilityGroup.md)

[Switch-SqlAvailabilityGroup](xref:sqlserver/vlatest/Switch-SqlAvailabilityGroup.md)

[Test-SqlAvailabilityGroup](xref:sqlserver/vlatest/Test-SqlAvailabilityGroup.md)


