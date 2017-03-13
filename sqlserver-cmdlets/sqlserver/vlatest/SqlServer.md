---
Module Name: SqlServer
Module Guid: 97C3B589-6545-4107-A061-3FE23A4E9195
Download Help Link: None
Help Version: 2.0.1.2
Locale: en-US
ms.assetid: E0E6D82E-FC57-4F9C-95C3-3BB167580003
updated_at: 3/13/2017 4:14 PM
ms.date: 3/13/2017
content_git_url: https://github.com/MicrosoftDocs/sql-docs-powershell/blob/master/sqlserver-cmdlets/sqlserver/vlatest/SqlServer.md
original_content_git_url: https://github.com/MicrosoftDocs/sql-docs-powershell/blob/master/sqlserver-cmdlets/sqlserver/vlatest/SqlServer.md
gitcommit: https://github.com/MicrosoftDocs/sql-docs-powershell/blob/6eefe64a0ce19459190f09768267a4c79f9a6af9/sqlserver-cmdlets/sqlserver/vlatest/SqlServer.md
uid: sqlserver/vlatest/SqlServer.md
ms.topic: conceptual
author: stevestein
ms.author: sstein
keywords: powershell, cmdlet
manager: jhubbard
open_to_public_contributors: True
ms.service: sql-server
---

# SqlServer Module
## Description
This section contains the help topics for the SQL Server PowerShell cmdlets.

## SqlServer Cmdlets
### [Add-SqlAvailabilityDatabase](./Add-SqlAvailabilityDatabase.md)
Adds primary databases to an availability group or joins secondary databases to an availability group.

### [Add-SqlAvailabilityGroupListenerStaticIp](./Add-SqlAvailabilityGroupListenerStaticIp.md)
Adds a static IP address to an availability group listener.

### [Add-SqlAzureAuthenticationContext](./Add-SqlAzureAuthenticationContext.md)
Performs authentication to Azure and acquires an authentication token.

### [Add-SqlColumnEncryptionKeyValue](./Add-SqlColumnEncryptionKeyValue.md)
Adds an encrypted value for an existing column encryption key object in the database.

### [Add-SqlFirewallRule](./Add-SqlFirewallRule.md)
Adds a Windows Firewall rule to allow connections to a specific instance of SQL Server.

### [Add-SqlLogin](./Add-SqlLogin.md)
Creates a Login object in an instance of SQL Server.

### [Backup-SqlDatabase](./Backup-SqlDatabase.md)
Backs up SQL Server database objects.

### [Complete-SqlColumnMasterKeyRotation](./Complete-SqlColumnMasterKeyRotation.md)
Completes the rotation of a column master key.

### [Convert-UrnToPath](./Convert-UrnToPath.md)
Converts a SQL Server Management Object URN to a Windows PowerShell provider path.

### [ConvertFrom-EncodedSqlName](./ConvertFrom-EncodedSqlName.md)
Returns the original SQL Server identifier when given an identifier that has been encoded into a format usable in Windows PowerShell paths.

### [ConvertTo-EncodedSqlName](./ConvertTo-EncodedSqlName.md)
Encodes extended characters in SQL Server names to formats usable in Windows PowerShell paths.

### [Disable-SqlAlwaysOn](./Disable-SqlAlwaysOn.md)
Disables the AlwaysOn availability groups feature for a server.

### [Enable-SqlAlwaysOn](./Enable-SqlAlwaysOn.md)
Enables the AlwaysOn availability groups feature.

### [Get-SqlAgent](./Get-SqlAgent.md)
Gets a SQL Agent object that is present in the target instance of SQL Server.

### [Get-SqlAgentJob](./Get-SqlAgentJob.md)
Gets a SQL Agent Job object for each job that is present in the target instance of SQL Agent.

### [Get-SqlAgentJobHistory](./Get-SqlAgentJobHistory.md)
Gets the job history present in the target instance of SQL Agent.

### [Get-SqlAgentJobSchedule](./Get-SqlAgentJobSchedule.md)
Gets a job schedule object for each schedule that is present in the target instance of SQL Agent Job.

### [Get-SqlAgentJobStep](./Get-SqlAgentJobStep.md)
Gets a SQL JobStep object for each step that is present in the target instance of SQL Agent Job.

### [Get-SqlAgentSchedule](./Get-SqlAgentSchedule.md)
Gets a SQL job schedule object for each schedule that is present in the target instance of SQL Agent.

### [Get-SqlColumnEncryptionKey](./Get-SqlColumnEncryptionKey.md)
Gets all column encryption key objects defined in the database, or gets one column encryption key object with the specified name.

### [Get-SqlColumnMasterKey](./Get-SqlColumnMasterKey.md)
Gets the column master key objects defined in the database or gets one column master key object with the specified name.

### [Get-SqlCredential](./Get-SqlCredential.md)
Gets a SQL credential object.

### [Get-SqlDatabase](./Get-SqlDatabase.md)
Gets a SQL database object for each database that is present in the target instance of SQL Server.

### [Get-SqlErrorLog](./Get-SqlErrorLog.md)
Gets the SQL Server error logs.

### [Get-SqlInstance](./Get-SqlInstance.md)
Gets a SQL Instance object for each instance of SQL Server that is present on the target computer.

### [Get-SqlLogin](./Get-SqlLogin.md)
Returns Login objects in an instance of SQL Server.

### [Get-SqlSmartAdmin](./Get-SqlSmartAdmin.md)
Gets the SQL Smart Admin object and its properties.

### [Invoke-PolicyEvaluation](./Invoke-PolicyEvaluation.md)
Invokes one or more SQL Server policy-based management policy evaluations.

### [Invoke-Sqlcmd](./Invoke-Sqlcmd.md)
Runs a script containing statements supported by the SQL Server SQLCMD utility.

### [Invoke-SqlColumnMasterKeyRotation](./Invoke-SqlColumnMasterKeyRotation.md)
Initiates the rotation of a column master key.

### [Join-SqlAvailabilityGroup](./Join-SqlAvailabilityGroup.md)
Joins the local secondary replica to an availability group.

### [New-SqlAvailabilityGroup](./New-SqlAvailabilityGroup.md)
Creates an availability group.

### [New-SqlAvailabilityGroupListener](./New-SqlAvailabilityGroupListener.md)
Creates an availability group listener and attaches it to an availability group.

### [New-SqlAvailabilityReplica](./New-SqlAvailabilityReplica.md)
Creates an availability replica.

### [New-SqlAzureKeyVaultColumnMasterKeySettings](./New-SqlAzureKeyVaultColumnMasterKeySettings.md)
Creates a SqlColumnMasterKeySettings object describing an asymmetric key stored in Azure Key Vault.

### [New-SqlBackupEncryptionOption](./New-SqlBackupEncryptionOption.md)
Creates the encryption options for the Backup-SqlDatabase cmdlet or the Set-SqlSmartAdmin cmdlet.

### [New-SqlCertificateStoreColumnMasterKeySettings](./New-SqlCertificateStoreColumnMasterKeySettings.md)
Creates a SqlColumnMasterKeySettings object referencing the specified certificate.

### [New-SqlCngColumnMasterKeySettings](./New-SqlCngColumnMasterKeySettings.md)
Creates a SqlColumnMasterKeySettings object describing an asymmetric key stored in a key store supporting the CNG API.

### [New-SqlColumnEncryptionKey](./New-SqlColumnEncryptionKey.md)
Crates a column encryption key object in the database.

### [New-SqlColumnEncryptionKeyEncryptedValue](./New-SqlColumnEncryptionKeyEncryptedValue.md)
Creates the encrypted value of a column encryption key.

### [New-SqlColumnEncryptionSettings](./New-SqlColumnEncryptionSettings.md)
Creates a SqlColumnEncryptionSettings object that encapsulates information about a single column's encryption, including CEK and encryption type.

### [New-SqlColumnMasterKey](./New-SqlColumnMasterKey.md)
Creates a column master key object in the database.

### [New-SqlColumnMasterKeySettings](./New-SqlColumnMasterKeySettings.md)
Creates a SqlColumnMasterKeySettings object.

### [New-SqlCredential](./New-SqlCredential.md)
Creates a SQL Server credential object.

### [New-SqlCspColumnMasterKeySettings](./New-SqlCspColumnMasterKeySettings.md)
Creates a SqlColumnMasterKeySettings object describing an asymmetric key stored in a key store with a CSP supporting CAPI.

### [New-SqlHADREndpoint](./New-SqlHADREndpoint.md)
Creates a database mirroring endpoint on a SQL Server instance.

### [Read-SqlTableData](./Read-SqlTableData.md)
Reads data from a table of a SQL database.

### [Read-SqlViewData](./Read-SqlViewData.md)
Reads data from the view of a SQL database.

### [Remove-SqlAvailabilityDatabase](./Remove-SqlAvailabilityDatabase.md)
Removes an availability database from its availability group.

### [Remove-SqlAvailabilityGroup](./Remove-SqlAvailabilityGroup.md)
Removes an availability group.

### [Remove-SqlAvailabilityReplica](./Remove-SqlAvailabilityReplica.md)
Removes a secondary availability replica.

### [Remove-SqlColumnEncryptionKey](./Remove-SqlColumnEncryptionKey.md)
Removes the column encryption key object from the database.

### [Remove-SqlColumnEncryptionKeyValue](./Remove-SqlColumnEncryptionKeyValue.md)
Removes an encrypted value from an existing column encryption key object in the database.

### [Remove-SqlColumnMasterKey](./Remove-SqlColumnMasterKey.md)
Removes the column master key object from the database.

### [Remove-SqlCredential](./Remove-SqlCredential.md)
Removes the SQL credential object.

### [Remove-SqlFirewallRule](./Remove-SqlFirewallRule.md)
Disables the Windows Firewall rule that allows connections to a specific instance of SQL Server.

### [Remove-SqlLogin](./Remove-SqlLogin.md)
Removes Login objects from an instance of SQL Server.

### [Restore-SqlDatabase](./Restore-SqlDatabase.md)
Restores a database from a backup or transaction log records.

### [Resume-SqlAvailabilityDatabase](./Resume-SqlAvailabilityDatabase.md)
Resumes data movement on an availability database.

### [Save-SqlMigrationReport](./Save-SqlMigrationReport.md)


### [Set-SqlAuthenticationMode](./Set-SqlAuthenticationMode.md)
Configures the authentication mode of the target instance of SQL Server.

### [Set-SqlAvailabilityGroup](./Set-SqlAvailabilityGroup.md)
Sets settings on an availability group.

### [Set-SqlAvailabilityGroupListener](./Set-SqlAvailabilityGroupListener.md)
Sets the port setting on an availability group listener.

### [Set-SqlAvailabilityReplica](./Set-SqlAvailabilityReplica.md)
Sets the settings on an availability replica.

### [Set-SqlColumnEncryption](./Set-SqlColumnEncryption.md)
Encrypts, decrypts, or re-encrypts specified columns in the database.

### [Set-SqlCredential](./Set-SqlCredential.md)
Sets the properties for the SQL Credential object.

### [Set-SqlErrorLog](./Set-SqlErrorLog.md)
Sets or resets the maximum number of error log files before they are recycled.

### [Set-SqlHADREndpoint](./Set-SqlHADREndpoint.md)
Sets the properties of a database mirroring endpoint.

### [Set-SqlNetworkConfiguration](./Set-SqlNetworkConfiguration.md)
Sets the network configuration of the target instance of SQL Server.

### [Set-SqlSmartAdmin](./Set-SqlSmartAdmin.md)
Configures or modifies backup retention and storage settings.

### [Start-SqlInstance](./Start-SqlInstance.md)
Starts the specified instance of SQL Server.

### [Stop-SqlInstance](./Stop-SqlInstance.md)
Stops the specified instance of SQL Server.

### [Suspend-SqlAvailabilityDatabase](./Suspend-SqlAvailabilityDatabase.md)
Suspends data movement on an availability database.

### [Switch-SqlAvailabilityGroup](./Switch-SqlAvailabilityGroup.md)
Starts a failover of an availability group to a secondary replica.

### [Test-SqlAvailabilityGroup](./Test-SqlAvailabilityGroup.md)
Evaluates the health of an availability group.

### [Test-SqlAvailabilityReplica](./Test-SqlAvailabilityReplica.md)
Evaluates the health of availability replicas.

### [Test-SqlDatabaseReplicaState](./Test-SqlDatabaseReplicaState.md)
Evaluates the health of an availability database.

### [Test-SqlSmartAdmin](./Test-SqlSmartAdmin.md)
Tests the health of Smart Admin by evaluating SQL Server policy based management (PBM) policies.

### [Write-SqlTableData](./Write-SqlTableData.md)
Writes data to a table of a SQL database.



