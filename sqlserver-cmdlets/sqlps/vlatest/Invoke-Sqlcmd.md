---
external help file: Microsoft.SqlServer.Management.PSSnapins.dll-Help.xml
online version: 
schema: 2.0.0
ms.assetid: CEC02D90-7B4E-4973-AE57-30708B0F680A
updated_at: 1/4/2017 6:38 PM
ms.date: 1/4/2017
content_git_url: https://github.com/MicrosoftDocs/sql-docs-powershell/blob/live/sqlserver-cmdlets/sqlps/vlatest/Invoke-Sqlcmd.md
original_content_git_url: https://github.com/MicrosoftDocs/sql-docs-powershell/blob/live/sqlserver-cmdlets/sqlps/vlatest/Invoke-Sqlcmd.md
gitcommit: https://github.com/MicrosoftDocs/sql-docs-powershell/blob/4c48bd1c26220ff873e612527853aeeef98777da/sqlserver-cmdlets/sqlps/vlatest/Invoke-Sqlcmd.md
ms.topic: reference
author: stevestein
ms.author: sstein
keywords: powershell, cmdlet
manager: jhubbard
open_to_public_contributors: true
ms.service: sql-server
---

# Invoke-Sqlcmd

## SYNOPSIS
Runs a script containing statements supported by the SQL Server SQLCMD utility.

## SYNTAX

```
Invoke-Sqlcmd [-ServerInstance <PSObject>] [-Database <String>] [-EncryptConnection] [-Username <String>]
 [-Password <String>] [[-Query] <String>] [-QueryTimeout <Int32>] [-ConnectionTimeout <Int32>]
 [-ErrorLevel <Int32>] [-SeverityLevel <Int32>] [-MaxCharLength <Int32>] [-MaxBinaryLength <Int32>]
 [-AbortOnError] [-DedicatedAdministratorConnection] [-DisableVariables] [-DisableCommands]
 [-HostName <String>] [-NewPassword <String>] [-Variable <String[]>] [-InputFile <String>]
 [-OutputSqlErrors <Boolean>] [-IncludeSqlUserErrors] [-SuppressProviderContextWarning]
 [-IgnoreProviderContext] [<CommonParameters>]
```

## DESCRIPTION
The **Invoke-Sqlcmd** cmdlet runs a script containing the languages and commands supported by the SQL Server SQLCMD utility.
The commands supported are Transact-SQL statements and the subset of the XQuery syntax that is supported by the database engine.
This cmdlet also accepts many of the commands supported natively by SQLCMD, such as GO and QUIT.
This cmdlet also accepts the SQLCMD scripting variables, such as SQLCMDUSER.
By default, this cmdlet does not set SQLCMD scripting variables.

This cmdlet does not support the use of commands that are primarily related to interactive script editing.
The commands not supported include :!!, :connect, :error, :out, :ed, :list, :listvar, :reset, :perftrace, and :serverlist.

When this cmdlet is run, the first result set that the script returns is displayed as a formatted table.
If subsequent result sets contain different column lists than the first, those result sets are not displayed.
If subsequent result sets after the first set have the same column list, their rows are appended to the formatted table that contains the rows that were returned by the first result set.

You can display SQL Server message output, such as those that result from the SQL PRINT statement, by specifying the *Verbose* parameter.

## EXAMPLES

### Example 1: Connect to a named instance and run a script
```
PS C:\> Invoke-Sqlcmd -Query "SELECT GETDATE() AS TimeOfQuery;" -ServerInstance "MyComputer\MainInstance"
 TimeOfQuery
 -----------
 5/13/2010 8:49:43 PM
```

This command connects to a named instance of the SQL Database Engine on a computer and runs a basic Transact-SQL script.

### Example 2: Invoke commands in a script file and save the output in a text file
```
PS C:\> Invoke-Sqlcmd -InputFile "C:\ScriptFolder\TestSqlCmd.sql" | Out-File -FilePath "C:\ScriptFolder\TestSqlCmd.rpt"
Output sent to TestSqlCmd.rpt.
```

This command reads a file containing Transact-SQL statements and SQLCMD commands, runs the file, and writes the  output to another file.
The output file may contain proprietary information, so you should secure the output files with the appropriate NTFS permissions.

### Example 3: Invoke a script and pass in variable values from a string
```
PS C:\> $StringArray = "MYVAR1='String1'", "MYVAR2='String2'"
PS C:\> Invoke-Sqlcmd -Query "SELECT `$(MYVAR1) AS Var1, `$(MYVAR2) AS Var2;" -Variable $StringArray
Var1     Var2
----     ----
String1  String2
```

This command uses an array of character strings as input to the *Variable* parameter.
The array defines multiple SQLCMD variables.
The $ signs in the SELECT statement that identify the SQLCMD variables are escaped using the back-tick (\`) character.

### Example 4: Invoke a script and pass in variables from the SQL database engine
```
PS C:\>Set-Location "SQLSERVER:\SQL\MyComputer\MainInstance"
PS C:\>Invoke-Sqlcmd -Query "SELECT SERVERPROPERTY('MachineName') AS ComputerName;" -ServerInstance (Get-Item .)
 ComputerName
 ------------
 MyComputer
```

This command uses **Set-Location** to navigate to the SQL Server Windows PowerShell provider path for an instance of the SQL Database Engine.
Then it calls **Get-Item** to retrieve a SQL Management Object **Server** object for use as the *ServerInstance* parameter of **Invoke-Sqlcmd**.

### Example 5: Run a query and display verbose output
```
PS C:\> Invoke-Sqlcmd -Query "PRINT N'abc'" -Verbose
VERBOSE: abc
```

This command uses the Windows PowerShell *Verbose* parameter to return the message output of the SQL PRINT command.

### Example 6: Invoke a command using a positional string as input
```
PS C:\> Invoke-Sqlcmd "SELECT DB_NAME() AS DatabaseName;"
 WARNING: Using provider context. Server = MyComputer, Database = AdventureWorks2014. 

 DatabaseName
 ------------
 AdventureWorks2014
```

This command uses a positional string to supply the input to the *Query* parameter.
It also demonstrates how  **Invoke-Sqlcmd** uses the current path to set the database context to AdventureWorks2014.

## PARAMETERS

### -AbortOnError


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

### -ConnectionTimeout


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

### -Database


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

### -DedicatedAdministratorConnection


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

### -DisableCommands


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

### -DisableVariables


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

### -EncryptConnection


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

### -ErrorLevel


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

### -HostName


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

### -IgnoreProviderContext


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

### -IncludeSqlUserErrors


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

### -InputFile


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

### -MaxBinaryLength


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

### -MaxCharLength


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

### -NewPassword


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

### -OutputSqlErrors


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

### -Password


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

### -Query


```yaml
Type: String
Parameter Sets: (All)
Aliases: 

Required: False
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -QueryTimeout


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

### -ServerInstance


```yaml
Type: PSObject
Parameter Sets: (All)
Aliases: 

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -SeverityLevel


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

### -SuppressProviderContextWarning


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

### -Username


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

### -Variable


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

### CommonParameters
This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable. For more information, see about_CommonParameters (http://go.microsoft.com/fwlink/?LinkID=113216).

## INPUTS

### PSObject

## OUTPUTS

###  
Formatted table

## NOTES

## RELATED LINKS

[SQL Server 2016 with Windows PowerShell Cmdlets](xref:sqlps/vlatest/SQLPS.md)
