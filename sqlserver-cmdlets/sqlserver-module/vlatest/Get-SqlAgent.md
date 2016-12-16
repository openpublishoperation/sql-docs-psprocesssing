---
external help file: Microsoft.SqlServer.Management.PSSnapins.dll-Help.xml
online version: 
schema: 2.0.0
ms.assetid: F6A7569E-86DC-4DAE-9C2D-08A59F6D75EC
updated_at: 12/13/2016 8:09 PM
ms.date: 12/13/2016
content_git_url: https://github.com/MicrosoftDocs/sql-docs-powershell/blob/live/sqlserver-cmdlets/sqlserver-module/vlatest/Get-SqlAgent.md
original_content_git_url: https://github.com/MicrosoftDocs/sql-docs-powershell/blob/live/sqlserver-cmdlets/sqlserver-module/vlatest/Get-SqlAgent.md
gitcommit: https://github.com/MicrosoftDocs/sql-docs-powershell/blob/f97823fbeb2d71358573a8e4b5c2c322a3a5c138/sqlserver-cmdlets/sqlserver-module/vlatest/Get-SqlAgent.md
ms.topic: reference
author: stevestein
ms.author: sstein
keywords: powershell, cmdlet
manager: jhubbard
open_to_public_contributors: true
ms.service: sql-server
---

# Get-SqlAgent

## SYNOPSIS
Gets a SQL Agent object that is present in the target instance of SQL Server.

## SYNTAX

### ByPath (Default)
```
Get-SqlAgent [[-Path] <String>] [-InformationAction <ActionPreference>] [-InformationVariable <String>]
 [<CommonParameters>]
```

### ByObject
```
Get-SqlAgent [[-InputObject] <Server>] [-InformationAction <ActionPreference>] [-InformationVariable <String>]
 [<CommonParameters>]
```

### ByName
```
Get-SqlAgent [[-ServerInstance] <String[]>] [-Credential <PSCredential>] [-ConnectionTimeout <Int32>]
 [-InformationAction <ActionPreference>] [-InformationVariable <String>] [<CommonParameters>]
```

## DESCRIPTION
The **Get-SqlAgent** cmdlet gets a SQL Agent object that is present in the target instance of the SQL Server.

This cmdlet supports the following modes of operation:

- Specify the **ServerInstance** object of the target instance of SQL Server. 
- Specify the *Path* parameter of an instance of SQL Server. 
- Invoke the cmdlet in a valid context.

## EXAMPLES

### Example 1: Get the SQL Agent of a server instance
```
PS C:\>Get-SqlAgent -ServerInstance "MyServerInstance"
'MyServerInstance'AgentDomainGroup          : NT SERVICE\SQLSERVERAGENT
AgentLogLevel             : Errors, Warnings
AgentMailType             : SqlAgentMail
AgentShutdownWaitTime     : 15
```

This command gets the SQL Agent of the server instance named.
MyServerInstance.

## PARAMETERS

### -Path
Specifies the path to the instance of SQL Server on which this cmdlet runs the operation.
If you do not specify a value for this parameter, the cmdlet uses the current working location.

```yaml
Type: String
Parameter Sets: ByPath
Aliases: 

Required: False
Position: 1
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

### -InputObject
Specifies the server object of the target instance.

```yaml
Type: Server
Parameter Sets: ByObject
Aliases: 

Required: False
Position: 1
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -ServerInstance
Specifies the name of an instance of SQL Server, as an array, that becomes the target of the operation.

```yaml
Type: String[]
Parameter Sets: ByName
Aliases: 

Required: False
Position: 1
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -Credential
Specifies a **PSCredential** object used to specify the credentials for a SQL Server login that has permission to perform this operation.

```yaml
Type: PSCredential
Parameter Sets: ByName
Aliases: 

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ConnectionTimeout
Specifies the number of seconds to wait for a SQL Server connection before a timeout failure.
The timeout value must be an integer value between 0 and 65534.
If 0 is specified, connection attempts do not time out.

```yaml
Type: Int32
Parameter Sets: ByName
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

[Get-SqlAgentJob](xref:sqlserver-module/vlatest/Get-SqlAgentJob.md)

[Get-SqlAgentJobHistory](xref:sqlserver-module/vlatest/Get-SqlAgentJobHistory.md)

[Get-SqlAgentJobSchedule](xref:sqlserver-module/vlatest/Get-SqlAgentJobSchedule.md)

[Get-SqlAgentJobStep](xref:sqlserver-module/vlatest/Get-SqlAgentJobStep.md)


