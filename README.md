# MSSQL-audit-scripts

Scripts that can be used when auditing a MSSQL Server.
This script has currently been tested on MSSQL 2012 and MSSQL 2016.

[+] Tested on MSSQL 2017 and it works perfectly  
[+] Expected output: A .html file on the same directory

### Pre-Requisite
Open CMD and run the command to get the Host Name:
```
C:\Windows\system32> systeminfo
```
```
Host Name:                 RALPH
OS Name:                   Microsoft Windows Server 2016 Standard
OS Version:                10.0.14393 N/A Build 14393
OS Manufacturer:           Microsoft Corporation
OS Configuration:          Standalone Server
OS Build Type:             Multiprocessor Free
Registered Owner:          Windows User
......
```

From here we will obtain the hostname **RALPH** which is the servername, do note that IP address 127.0.0.1 does not work for the parameter here

### Command that Works: Running on Powershell (Not CMD)
1. The default will use the following command, it requires **NT/Authority System** privilege (Administrator Privilege) to run the script
- Run this on CMD as Administrator to bypass the system execution policy so we can run the script peacefully
```
powershell -ep bypass
```
- Then run the script on the PowerShell prompt
```
PS C:\Users\Administrator\Desktop> .\MSSQL_Audit_Script.ps1 -Server "Servername" -WindowsAuthentication
```
- In the case above we will replace the "Servername" to **RALPH** for the example above
```
PS C:\Users\Administrator\Desktop> .\MSSQL_Audit_Script.ps1 -Server "RALPH" -WindowsAuthentication
```

2. This will target specific database name, which will produce less result (cleaner than the previous execution)
```
.\MSSQL_Audit_Script.ps1 -Server "Servername" -Database "DatabaseName" -WindowsAuthentication
```
