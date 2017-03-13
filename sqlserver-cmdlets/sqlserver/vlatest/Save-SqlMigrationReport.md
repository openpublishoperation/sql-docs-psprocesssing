---
external help file: Microsoft.SqlServer.Management.PSSnapins.dll-Help.xml
online version: 
schema: 2.0.0
ms.assetid: 6719F4B4-3C72-490C-AA4D-307C4B5B9F5D
updated_at: 3/13/2017 4:14 PM
ms.date: 3/13/2017
content_git_url: https://github.com/MicrosoftDocs/sql-docs-powershell/blob/master/sqlserver-cmdlets/sqlserver/vlatest/Save-SqlMigrationReport.md
original_content_git_url: https://github.com/MicrosoftDocs/sql-docs-powershell/blob/master/sqlserver-cmdlets/sqlserver/vlatest/Save-SqlMigrationReport.md
gitcommit: https://github.com/MicrosoftDocs/sql-docs-powershell/blob/6eefe64a0ce19459190f09768267a4c79f9a6af9/sqlserver-cmdlets/sqlserver/vlatest/Save-SqlMigrationReport.md
ms.topic: reference
author: stevestein
ms.author: sstein
keywords: powershell, cmdlet
manager: jhubbard
open_to_public_contributors: True
ms.service: sql-server
---

# Save-SqlMigrationReport

## SYNOPSIS

## SYNTAX

```
Save-SqlMigrationReport [-Server <String>] [-Database <String>] [-Schema <String>] [-Username <String>]
 [-Password <String>] [-Object <String>] [-InputObject <SqlSmoObject>] [-MigrationType <MigrationType>]
 [-FolderPath <String>] [-InformationAction <ActionPreference>] [-InformationVariable <String>]
 [<CommonParameters>]
```

## DESCRIPTION

## EXAMPLES

## PARAMETERS

### -Server


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

### -Database
Specifies an array of user databases.
This cmdlet adds or joins  the databases that this parameter specifies to the availability group.
The databases that you specify must reside on the local instance of SQL Server.

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

### -Schema
Specifies the name of the schema for the table.

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

### -Username
Specifies the login ID for making a SQL Server Authentication connection to an instance of the Database Engine.
The password must be specified through the *Password* parameter.
If *Username* and *Password* are not specified, this cmdlet attempts a Windows Authentication connection using the Windows account running the Windows PowerShell session.
When possible, use Windows Authentication.

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
Parameter Sets: (All)
Aliases: 

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Object


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
Specifies the migration report group.

```yaml
Type: SqlSmoObject
Parameter Sets: (All)
Aliases: 

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -MigrationType


```yaml
Type: MigrationType
Parameter Sets: (All)
Aliases: 

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -FolderPath


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

### CommonParameters
This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable. For more information, see about_CommonParameters (http://go.microsoft.com/fwlink/?LinkID=113216).

## INPUTS

## OUTPUTS

## NOTES

## RELATED LINKS
