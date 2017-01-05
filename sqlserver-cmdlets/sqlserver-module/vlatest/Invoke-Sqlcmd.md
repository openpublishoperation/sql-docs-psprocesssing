---
external help file: Microsoft.SqlServer.Management.PSSnapins.dll-Help.xml
online version: 
schema: 2.0.0
ms.assetid: CEC02D90-7B4E-4973-AE57-30708B0F680A
updated_at: 1/5/2017 8:57 AM
ms.date: 1/5/2017
content_git_url: https://github.com/MicrosoftDocs/sql-docs-powershell/blob/live/sqlserver-cmdlets/sqlserver-module/vlatest/Invoke-Sqlcmd.md
original_content_git_url: https://github.com/MicrosoftDocs/sql-docs-powershell/blob/live/sqlserver-cmdlets/sqlserver-module/vlatest/Invoke-Sqlcmd.md
gitcommit: https://github.com/MicrosoftDocs/sql-docs-powershell/blob/0d97835841eb5cfbe37d096037375a2e0c3eb87c/sqlserver-cmdlets/sqlserver-module/vlatest/Invoke-Sqlcmd.md
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

### ByConnectionParameters (Default)
```
Invoke-Sqlcmd [-ServerInstance <PSObject>] [-Database <String>] [-EncryptConnection] [-Username <String>]
 [-Password <String>] [[-Query] <String>] [-QueryTimeout <Int32>] [-ConnectionTimeout <Int32>]
 [-ErrorLevel <Int32>] [-SeverityLevel <Int32>] [-MaxCharLength <Int32>] [-MaxBinaryLength <Int32>]
 [-AbortOnError] [-DedicatedAdministratorConnection] [-DisableVariables] [-DisableCommands]
 [-HostName <String>] [-NewPassword <String>] [-Variable <String[]>] [-InputFile <String>]
 [-OutputSqlErrors <Boolean>] [-IncludeSqlUserErrors] [-SuppressProviderContextWarning]
 [-IgnoreProviderContext] [-OutputAs <OutputType>] [-InformationAction <ActionPreference>]
 [-InformationVariable <String>] [<CommonParameters>]
```

### ByConnectionString
```
Invoke-Sqlcmd [[-Query] <String>] [-QueryTimeout <Int32>] [-ErrorLevel <Int32>] [-SeverityLevel <Int32>]
 [-MaxCharLength <Int32>] [-MaxBinaryLength <Int32>] [-AbortOnError] [-DisableVariables] [-DisableCommands]
 [-Variable <String[]>] [-InputFile <String>] [-OutputSqlErrors <Boolean>] [-IncludeSqlUserErrors]
 [-OutputAs <OutputType>] -ConnectionString <String> [-InformationAction <ActionPreference>]
 [-InformationVariable <String>] [<CommonParameters>]
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

This command reads a file containing Transact-SQL statements and SQLCMD commands, runs the file, and writes the output to another file.
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
PS C:\> Set-Location "SQLSERVER:\SQL\MyComputer\MainInstance"
PS C:\> Invoke-Sqlcmd -Query "SELECT SERVERPROPERTY('MachineName') AS ComputerName;" -ServerInstance (Get-Item .)
 ComputerName
 ------------
 MyComputer
```

This command uses **Set-Location** to navigate to the SQL ServerWindows PowerShell provider path for an instance of the SQL Database Engine.
Then it calls **Get-Item** to retrieve a SQL Management Object **Server** object for use as the *ServerInstance* parameter of **Invoke-Sqlcmd**.

### Example 5: Run a query and display verbose output
```
PS C:\> Invoke-Sqlcmd -Query "PRINT N'abc'" -Verbose
VERBOSE: abc
```

This command uses the Windows PowerShell*Verbose* parameter to return the message output of the SQL PRINT command.

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

### Example 7: Capture data into a DataSet object
```
PS C:\> $DS = Invoke-Sqlcmd -ServerInstance "MyComputer" -Query "SELECT  ID, Item FROM MyDB.dbo.MyTable" -As DataSet $DS.Tables[0].Rows | %{ echo "{ $($_['ID']), $($_['Item']) }" }
{ 10, AAA }
{ 20, BBB }
{ 30, CCC }
```

This command uses the *As DataSet* parameter to capture the data into a **.Net System.Data.DataSet** object and stores the result in the variable named $DS.
The object can be used for further processing.

### Example 8: Get specific column sets
```
PS C:\>$Tables = Invoke-Sqlcmd -ServerInstance "MyComputer" -Query "SELECT  Item, id FROM MyDatabase.dbo.MyTable; SELECT GETDATE() AS T" -As DataTables
PS C:\> $Tables[0].Rows | %{ echo $_.ID }
PS C:\> $Tables[1].Rows | %{ echo $_.T.DayOfWeek }
10
20
30

Monday
```

The first command uses the *As DataTables* parameter to capture the data into a collection of **.Net System.Data.DataTable** objects.
The command gets two tables with different column sets.

The second command displays the column set of the first row of the table.

The third command displays the column set of the second row of the table.

Each table can be processed individually, based on its own schema.

### Example 9: Gain full control of a connection
```
PS C:\> Invoke-Sqlcmd -Query "SELECT COUNT(*) AS Count FROM MyTable" -ConnectionString "Data Source=MYSERVER;Initial Catalog=MyDatabase;Integrated Security=True;ApplicationIntent=ReadOnly"
Count
-----
127432
```

This command users the *ConnectionString* parameter to gain full control of the connection that this cmdlet establishes, instead of the **Invoke-Sqlcmd** to build the connection string based on the parameters passed on the command line.
This is useful for less-common properties that you may want to use.

## PARAMETERS

### -ServerInstance
Specifies a character string or SQL Server Management Objects (SMO) object that specifies the name of an instance of the Database Engine.
For default instances, only specify the computer name: MyComputer.
For named instances, use the format ComputerName\InstanceName.

```yaml
Type: PSObject
Parameter Sets: ByConnectionParameters
Aliases: 

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -Database
Specifies the name of a database.
This cmdlet connects to this database in the instance that is specified in the *ServerInstance* parameter.

If the *Database* parameter is not specified, the database that is used depends on whether the current path specifies both the SQLSERVER:\SQL folder and a database name.
If the path specifies both the SQL folder and a database name, this cmdlet connects to the database that is specified in the path.
If the path is not based on the SQL folder, or the path does not contain a database name, this cmdlet connects to the default database for the current login ID.
If you specify the *IgnoreProviderContext* parameter switch, this cmdlet does not consider any database specified in the current path, and connects to the database defined as the default for the current login ID.

```yaml
Type: String
Parameter Sets: ByConnectionParameters
Aliases: 

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -EncryptConnection
Indicates that this cmdlet uses Secure Sockets Layer (SSL) encryption for the connection to the instance of the Database Engine specified in the *ServerInstance* parameter.
If this parameter is specified, SSL encryption is used.
If you do not specify this parameter, specified encryption is not used.

```yaml
Type: SwitchParameter
Parameter Sets: ByConnectionParameters
Aliases: 

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Username
Specifies the login ID for making a SQL Server Authentication connection to an instance of the Database Engine.
The password must be specified through the *Password* parameter.
If *Username* and *Password* are not specified, this cmdlet attempts a Windows Authentication connection using the Windows account running the Windows PowerShell session.
When possible, use Windows Authentication.

```yaml
Type: String
Parameter Sets: ByConnectionParameters
Aliases: 

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Password
Specifies the password for the SQL Server Authentication login ID that was specified in the *Username* parameter.
Passwords are case-sensitive.
When possible, use Windows Authentication.
Do not use a blank password, when possible use a strong password.

If you specify the *Password* parameter followed by your password, the password is visible to anyone who can see your monitor.
If you code *Password* followed by your password in a .ps1 script, anyone reading the script file will see your password.
Assign the appropriate NTFS permissions to the file to prevent other users from being able to read the file.

```yaml
Type: String
Parameter Sets: ByConnectionParameters
Aliases: 

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Query
Specifies one or more queries that this cmdlet runs.
The queries can be Transact-SQL or XQuery statements, or sqlcmd commands.
Multiple queries separated by a semicolon can be specified.
Do not specify the sqlcmd GO separator.
Escape any double quotation marks included in the string.
Consider using bracketed identifiers such as \[MyTable\] instead of quoted identifiers such as "MyTable".

```yaml
Type: String
Parameter Sets: (All)
Aliases: 

Required: False
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -QueryTimeout
Specifies the number of seconds before the queries time out.
If a timeout value is not specified, the queries do not time out.
The timeout must be an integer value between 1 and 65535.

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

### -ConnectionTimeout
Specifies the number of seconds when this cmdlet times out if it cannot successfully connect to an instance of the Database Engine.
The timeout value must be an integer value between 0 and 65534.
If 0 is specified, connection attempts do not time out.

```yaml
Type: Int32
Parameter Sets: ByConnectionParameters
Aliases: 

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ErrorLevel
Specifies that this cmdlet display only error messages whose severity level is equal to or higher than the value specified.
All error messages are displayed if this parameter is not specified or set to 0.
Database Engine error severities range from 1 to 24.

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

### -SeverityLevel
Specifies the lower limit for the error message severity level this cmdlet returns to the ERRORLEVEL Windows PowerShell variable.
This cmdlet returns the highest severity level from the error messages generated by the queries it runs, provided that severity is equal to or higher than specified in the *SeverityLevel* parameter.
If *SeverityLevel* is not specified or set to 0, this cmdlet returns 0 to ERRORLEVEL.
The severity levels of Database Engine error messages range from 1 to 24.
This cmdlet does not report severities for informational messages that have a severity of 10

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
Specifies the maximum number of characters returned for columns with character or Unicode data types, such as char, nchar, varchar, and nvarchar.
The default value is 4,000 characters.

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

### -MaxBinaryLength
Specifies the maximum number of bytes returned for columns with binary string data types, such as binary and varbinary.
The default value is 1,024 bytes.

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

### -AbortOnError
Indicates that this cmdlet stops the SQL Server command and returns an error level to the Windows PowerShell ERRORLEVEL variable if this cmdlet encounters an error.
The error level returned is 1 if the error has a severity higher than 10, and the error level is 0 if the error has a severity of 10 or less.
If the *ErrorLevel* parameter is also specified, this cmdlet returns 1 only if the error message severity is also equal to or higher than the value specified for *ErrorLevel*.

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

### -DedicatedAdministratorConnection
Indicates that this cmdlet uses a Dedicated Administrator Connection (DAC) to connect to an instance of the Database Engine.
DAC is used by system administrators for actions such as troubleshooting instances that will not accept new standard connections.
The instance must be configured to support DAC.
If DAC is not enabled, this cmdlet reports an error and will not run.

```yaml
Type: SwitchParameter
Parameter Sets: ByConnectionParameters
Aliases: 

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -DisableVariables
Indicates that this cmdlet ignores sqlcmd scripting variables.
This is useful when a script contains many INSERT statements that may contain strings that have the same format as variables, such as $(variable_name).

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
Indicates that this cmdlet turns off some sqlcmd features that might compromise security when run in batch files.
It prevents Windows PowerShell variables from being passed in to the **Invoke-Sqlcmd** script.
The startup script specified in the SQLCMDINI scripting variable is not run.

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

### -HostName
Specifies a workstation name.
The workstation name is reported by the sp_who system stored procedure and in the hostname column of the sys.processes catalog view.
If this parameter is not specified, the default is the name of the computer on which **Invoke-Sqlcmd** is run.
This parameter can be used to identify different **Invoke-Sqlcmd** sessions.

```yaml
Type: String
Parameter Sets: ByConnectionParameters
Aliases: 

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -NewPassword
Specifies a new password for a SQL Server Authentication login ID.
This cmdlet changes the password and then exits.
You must also specify the *Username* and *Password* parameters, with *Password* that specifies the current password for the login.

```yaml
Type: String
Parameter Sets: ByConnectionParameters
Aliases: 

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Variable
Specifies, as a string array, a sqlcmd scripting variable for use in the sqlcmd script, and sets a value for the variable.
Use a Windows PowerShell array to specify multiple variables and their values.

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

### -InputFile
Specifies a file to be used as the query input to this cmdlet.
The file can contain Transact-SQL statements, XQuery statements, and sqlcmd commands and scripting variables.
Specify the full path to the file.
Spaces are not allowed in the file path or file name.

You should only run scripts from trusted sources.
Ensure all input scripts are secured with the appropriate NTFS permissions.

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
Indicates that this cmdlet displays error messages in the **Invoke-Sqlcmd** output.

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

### -IncludeSqlUserErrors
Indicates that this cmdlet returns SQL user script errors that are otherwise ignored by default.
If this parameter is specified, this cmdlet matches the default behavior of the sqlcmd utility.

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

### -SuppressProviderContextWarning
Indicates that this cmdlet suppresses the warning that this cmdlet has used in the database context from the current SQLSERVER:\SQL path setting to establish the database context for the cmdlet.

```yaml
Type: SwitchParameter
Parameter Sets: ByConnectionParameters
Aliases: 

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -IgnoreProviderContext
Indicates that this cmdlet ignores the database context that was established by the current SQLSERVER:\SQL path.
If the *Database* parameter is not specified, this cmdlet uses the default database for the current login ID or Windows account.

```yaml
Type: SwitchParameter
Parameter Sets: ByConnectionParameters
Aliases: 

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -OutputAs
Specifies the type of the results this cmdlet gets.

The acceptable values for this parameter are:

- DataSet
- DataTables
- DataRows

If you do not specify a value for this parameter, the cmdlet sets the value to DataRows.

```yaml
Type: OutputType
Parameter Sets: (All)
Aliases: As

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

### -ConnectionString
Specifies a connection string to connect to the server.

```yaml
Type: String
Parameter Sets: ByConnectionString
Aliases: 

Required: True
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

[SQL Server Cmdlets](xref:sqlserver-module/vlatest/SqlServer.md)
