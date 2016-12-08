# SQL Server Cmdlet Reference

The Windows PowerShell components of SQL Server are included in both the SQL Server Management Studio (SSMS) tools installer as well as with the SQL Server engine install. In order to be able to ship SQL PowerShell updates, we had to change the identity of the SQL PowerShell module as well as the wrapper known as SQLPS.exe. Because of this change, there are now two SQL PowerShell modules, the **SQLPS** module and the **SqlServer** module. This change has an impact to scripts that call the Import-Module cmdlet. 

The SQL PowerShell module that is included with SSMS has changed from **SQLPS** to **SqlServer**. There is no change to the module used by SQL Server Agent. If you have a Windows PowerShell script that runs the command `Import-Module -Name SQLPS`, you must change it to `Import-Module -Name SqlServer` in order to take advantage of the new provider functionality and new cmdlets. The new module is installed to `%Program Files\WindowsPowerShell\Modules\SqlServer`. Therefore, you do not have to update the $env:PSModulePath variable. If you have scripts that use a third-party or community version of a module named **SqlServer**, use of the Prefix parameter to avoid name collisions. 

The motivation for these changes is that the tooling components are being moved to be "application local" and not share any components with the SQL Server engine. This is an important step to enable monthly tooling updates while not negatively impacting the components setup and updated by the SQL Server setup program. 

SSMS has been updated to integrate with SQLTOOLSPS.exe rather than SQLPS.exe. If you start Windows PowerShell from in SSMS, it starts Windows PowerShell and configures the session to include the new SQL Server module. We recommend that you avoid using these EXE wrappers. They exist for legacy reasons in SSMS and are likely to be removed in a future monthly update. 

The new version of SQL Server PowerShell included with SSMS does not update the version of Windows PowerShell that SQL Server uses. This means that scripts that SQL Server Agent runs are not able to use the new cmdlets. Updates to **SQLPS**, which is the version used by SQL Server Agent, are done through the traditional SQL Server update mechanisms. Specifically, major changes are done as part of the next major version of SQL Server as it becomes available.

Module | Description
------ | -----------
[SQLPS](/powershell/sqlserver/sqlps) | Module that is included with SQL Server 2016. This module is through product updates.
[SQLServer](/powershell/sqlserver/sqlserver)| Module that is included with the monthly SSMS releases. 
