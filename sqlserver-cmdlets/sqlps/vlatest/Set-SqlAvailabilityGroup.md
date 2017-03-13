---
external help file: Microsoft.SqlServer.Management.PSSnapins.dll-Help.xml
online version: 
schema: 2.0.0
ms.assetid: 32D36186-DA82-40BE-A9FD-7DEFACF63E76
updated_at: 1/4/2017 6:38 PM
ms.date: 1/4/2017
content_git_url: https://github.com/MicrosoftDocs/sql-docs-powershell/blob/master/sqlserver-cmdlets/sqlps/vlatest/Set-SqlAvailabilityGroup.md
original_content_git_url: https://github.com/MicrosoftDocs/sql-docs-powershell/blob/master/sqlserver-cmdlets/sqlps/vlatest/Set-SqlAvailabilityGroup.md
gitcommit: https://github.com/MicrosoftDocs/sql-docs-powershell/blob/4c48bd1c26220ff873e612527853aeeef98777da/sqlserver-cmdlets/sqlps/vlatest/Set-SqlAvailabilityGroup.md
ms.topic: reference
author: stevestein
ms.author: sstein
keywords: powershell, cmdlet
manager: jhubbard
open_to_public_contributors: True
ms.service: sql-server
---

# Set-SqlAvailabilityGroup

## SYNOPSIS
Sets settings on an availability group.

## SYNTAX

### ByPath (Default)
```
Set-SqlAvailabilityGroup [-AutomatedBackupPreference <AvailabilityGroupAutomatedBackupPreference>]
 [-FailureConditionLevel <AvailabilityGroupFailureConditionLevel>] [-HealthCheckTimeout <Int32>]
 [-DatabaseHealthTrigger <Boolean>] [[-Path] <String>] [-Script] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### ByObject
```
Set-SqlAvailabilityGroup [-AutomatedBackupPreference <AvailabilityGroupAutomatedBackupPreference>]
 [-FailureConditionLevel <AvailabilityGroupFailureConditionLevel>] [-HealthCheckTimeout <Int32>]
 [-DatabaseHealthTrigger <Boolean>] [-InputObject] <AvailabilityGroup> [-Script] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

## DESCRIPTION
The **Set-SqlAvailabilityGroup** cmdlet modifies settings on an existing availability group in AlwaysOn Availability Groups.
You can modify the automated backup preference, the failure condition level, and the health check timeout.
You must run this cmdlet on the server instance that hosts the primary replica.

## EXAMPLES

### Example 1: Change the health check timeout period
```
PS C:\> Set-SqlAvailabilityGroup -Path "SQLSERVER:\Sql\PrimaryServer\InstanceName\AvailabilityGroups\MAinAG" -HealthCheckTimeout 120000
```

This command changes the health check timeout property on the availability group named MainAG to 120,000 milliseconds, or two minutes.
If automatic failover is enabled, after this length of time, AlwaysOn Availability Groups initiates an automatic failover will be initiated.

### Example 2: Change automated backup preference
```
PS C:\> Set-SqlAvailabilityGroup -Path "SQLSERVER:\Sql\PrimaryServer\InstanceName\AvailabilityGroups\MainAG" -AutomatedBackupPreference SecondaryOnly
```

This command changes the automated backup preference on the availability group named MainAG to be SecondaryOnly.
Automated backups of databases in this availability group do not occur on the primary replica.
Instead, automated backups occur on the secondary replica that has the highest backup priority.

### Example 3: Change the failure condition level
```
PS C:\> Set-SqlAvailabilityGroup -Path "SQLSERVER:\Sql\PrimaryServer\InstanceName\AvailabilityGroups\MainAG" -FailureConditionLevel OnServerDown
```

This command changes the failure condition level on the availability group named MainAG to be OnServerDown.
If the server instance that hosts the primary replica goes offline and if automatic failover is enabled, AlwaysOn Availability Groups starts an automatic failover.

## PARAMETERS

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
Failover or restart if any condition of lower value is satisfied, plus when the SQL Server service is connected to the cluster and the *HealthCheckTimeout* threshold is exceeded, or if the availability replica currently in primary role is in a failed state. 
- OnCriticalServerError.
Failover or restart if any condition of lower value is satisfied, plus when an internal critical server error occurs, which include out of memory condition, serious write-access violation, or too much dumping. 
- OnModerateServerError.
Failover or restart if any condition of lower value is satisfied, plus if a moderate Server error occurs, wich includes persistent out of memory condition. 
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
Specifies the length of time, in milliseconds, after which AlwaysOn Availability Groups declares an unresponsive server to be unhealthy.

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

### -InputObject
Specifies the availability group, as an **AvailabilityGroup** object, that this cmdlet modifies.

```yaml
Type: AvailabilityGroup
Parameter Sets: ByObject
Aliases: 

Required: True
Position: 2
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -Path
Specifies the path of the availability database that cmdlet modifies.
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

### -DatabaseHealthTrigger


```yaml
Type: Boolean
Parameter Sets: (All)
Aliases: 

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters
This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable. For more information, see about_CommonParameters (http://go.microsoft.com/fwlink/?LinkID=113216).

## INPUTS

## OUTPUTS

## NOTES

## RELATED LINKS

[Join-SqlAvailabilityGroup](xref:sqlps/vlatest/Join-SqlAvailabilityGroup.md)

[New-SqlAvailabilityGroup](xref:sqlps/vlatest/New-SqlAvailabilityGroup.md)

[Remove-SqlAvailabilityGroup](xref:sqlps/vlatest/Remove-SqlAvailabilityGroup.md)

[Switch-SqlAvailabilityGroup](xref:sqlps/vlatest/Switch-SqlAvailabilityGroup.md)

[Test-SqlAvailabilityGroup](xref:sqlps/vlatest/Test-SqlAvailabilityGroup.md)
