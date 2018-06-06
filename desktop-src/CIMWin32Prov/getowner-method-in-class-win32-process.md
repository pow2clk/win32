---
Description: The GetOwner&\#8194;WMI class method retrieves the user name and domain name under which the process is running.
audience: developer
author: REDMOND\\markl
manager: REDMOND\\markl
ms.assetid: bbd6d22b-ca54-42f3-8098-d3034048ec4d
ms.prod: windows-server-dev
ms.technology:
- cimwin32
- windows-management-instrumentation
ms.tgt_platform: multiple
title: GetOwner method of the Win32\_Process class
ms.author: windowssdkdev
ms.topic: article
ms.date: 05/31/2018
---

# GetOwner method of the Win32\_Process class

The **GetOwner** [WMI class](https://msdn.microsoft.com/library/aa393244) method retrieves the user name and domain name under which the process is running.

This topic uses Managed Object Format (MOF) syntax. For more information about using this method, see [Calling a Method](https://msdn.microsoft.com/library/aa384832).

## Syntax


```mof
uint32 GetOwner(
  [out] string User,
  [out] string Domain
);
```



## Parameters

<dl> <dt>

*User* \[out\]
</dt> <dd>

Returns the user name of the owner of this process.

</dd> <dt>

*Domain* \[out\]
</dt> <dd>

Returns the domain name under which this process is running.

</dd> </dl>

## Return value

Returns zero (0) to indicate success. Any other number indicates an error. For additional error codes, see [**WMI Error Constants**](https://msdn.microsoft.com/library/aa394559) or [**WbemErrorEnum**](https://msdn.microsoft.com/library/aa393978). For general **HRESULT** values, see [System Error Codes](https://msdn.microsoft.com/library/windows/desktop/ms681381).

<dl> <dt>

**Successful completion** (0)
</dt> <dt>

**Access denied** (2)
</dt> <dt>

**Insufficient privilege** (3)
</dt> <dt>

**Unknown failure** (8)
</dt> <dt>

**Path not found** (9)
</dt> <dt>

**Invalid parameter** (21)
</dt> <dt>

**Other** (22 4294967295)
</dt> </dl>

## Examples

[The Monitor Process CPU Pct by Name with Owner](https://Gallery.TechNet.Microsoft.Com/Monitor-Process-CPU-Pct-by-0f3a5a1c) VBScript sample collects the CPU or Processor utilization percent and looks up the process owner.

The [Get all servers that a list of users is logged onto](https://Gallery.TechNet.Microsoft.Com/Get-all-servers-that-a-aecc07ef) PowerShell sample querys WMI for the owner of all explorer.exe processes.

The following VBScript code example obtains the owner for each running process.


```VB
strComputer = "."
Set colProcesses = GetObject("winmgmts:" & _
   "{impersonationLevel=impersonate}!\\" & strComputer & _
   "\root\cimv2").ExecQuery("Select * from Win32_Process")

For Each objProcess in colProcesses

    Return = objProcess.GetOwner(strNameOfUser)
    If Return <> 0 Then
        Wscript.Echo "Could not get owner info for process " & _  
            objProcess.Name & VBNewLine _
            & "Error = " & Return
    Else 
        Wscript.Echo "Process " _
            & objProcess.Name & " is owned by " _ 
            & "\" & strNameOfUser & "."
    End If
Next
```



## Requirements



|                                     |                                                                                         |
|-------------------------------------|-----------------------------------------------------------------------------------------|
| Minimum supported client<br/> | Windows Vista<br/>                                                                |
| Minimum supported server<br/> | Windows Server 2008<br/>                                                          |
| Namespace<br/>                | Root\\CIMV2<br/>                                                                  |
| MOF<br/>                      | <dl> <dt>CIMWin32.mof</dt> </dl> |
| DLL<br/>                      | <dl> <dt>CIMWin32.dll</dt> </dl> |



## See also

<dl> <dt>

[Operating System Classes](https://msdn.microsoft.com/library/aa392727)
</dt> <dt>

[**Win32\_Process**](win32-process.md)
</dt> </dl>

 

 



