# Lab 03 — Windows Service Troubleshooting

## Scenario

A user reported that printing was not working on their Windows computer.

I deliberately stopped the Windows Print Spooler service in a controlled Windows 11 virtual machine to simulate a common IT Support service-related problem.

The issue was investigated using PowerShell and Windows service management tools. The service status and configuration were checked, the service was restarted, and the result was verified.

---

## 1. Problem

The Windows **Print Spooler** service was not running.

The Print Spooler is responsible for managing print jobs and communication with printers in Windows.

To simulate a service-related IT Support problem, I deliberately stopped the Print Spooler service.

---

## 2. Initial Check

I logged into the Windows 11 virtual machine using the administrator account `admm`.

I opened PowerShell with administrator privileges and checked the Print Spooler service:

```powershell
Get-Service -Name Spooler
```

The service was initially running:

```text
Status   Name      DisplayName
------   ----      -----------
Running  Spooler   Print Spooler
```

I also checked the service startup configuration:

```powershell
Get-Service -Name Spooler | Select-Object Name, Status, StartType
```

The result showed:

```text
Name     Status   StartType
----     ------   ---------
Spooler  Running  Automatic
```

This confirmed that the Print Spooler was operating normally before the troubleshooting scenario was created.

### Evidence

![Lab 03 - Print Spooler initially running](screenshots/01-spooler-working.png)

---

## 3. Creating the Problem

I deliberately stopped the Print Spooler service using:

```powershell
Stop-Service -Name Spooler
```

I then checked the service status:

```powershell
Get-Service -Name Spooler
```

The service showed:

```text
Status   Name      DisplayName
------   ----      -----------
Stopped  Spooler   Print Spooler
```

I also checked the startup configuration:

```powershell
Get-Service -Name Spooler | Select-Object Name, Status, StartType
```

The result showed:

```text
Name     Status   StartType
----     ------   ---------
Spooler  Stopped  Automatic
```

This confirmed that the service had been stopped while remaining configured for automatic startup.

### Evidence

![Lab 03 - Print Spooler stopped](screenshots/02-spooler-stopped.png)

---

## 4. Investigation

I investigated the Print Spooler service using PowerShell.

First, I checked the service details:

```powershell
Get-Service -Name Spooler | Format-List *
```

I also checked the Windows service configuration using:

```powershell
sc.exe qc Spooler
```

This provided information about the service configuration, including its startup type and service account.

I also checked the Windows System event log for Service Control Manager events:

```powershell
Get-WinEvent -LogName System -MaxEvents 50 |
Where-Object {$_.ProviderName -eq "Service Control Manager"} |
Select-Object -First 10 TimeCreated, Id, LevelDisplayName, Message
```

The investigation confirmed that the Print Spooler service was currently stopped.

Because this was a deliberately created lab scenario, the stopped service was identified as the cause of the simulated printing problem.

### Evidence

![Lab 03 - Print Spooler investigation](screenshots/03-spooler-investigation.png)

---

## 5. Root Cause

The Print Spooler service had been stopped.

### Root Cause

**The Windows Print Spooler service was not running.**

This would prevent Windows from processing print jobs correctly.

---

## 6. Fix

I restarted the Print Spooler service using PowerShell:

```powershell
Start-Service -Name Spooler
```

I then checked the service status:

```powershell
Get-Service -Name Spooler
```

The service showed:

```text
Status   Name      DisplayName
------   ----      -----------
Running  Spooler   Print Spooler
```

I also verified the startup configuration:

```powershell
Get-Service -Name Spooler | Select-Object Name, Status, StartType
```

The result showed:

```text
Name     Status   StartType
----     ------   ---------
Spooler  Running  Automatic
```

The service was therefore successfully restored.

### Evidence

![Lab 03 - Print Spooler restored](screenshots/04-spooler-fixed.png)

---

## 7. Verification

I performed a final service status check:

```powershell
Get-Service -Name Spooler
```

The service was confirmed as:

```text
Status   Name      DisplayName
------   ----      -----------
Running  Spooler   Print Spooler
```

This confirmed that the Print Spooler service had been successfully restored.

The troubleshooting process was completed successfully.

---

## 8. Troubleshooting Summary

| Stage | Action | Result |
|---|---|---|
| **Baseline** | Checked Print Spooler | Service running |
| **Problem Created** | Stopped Print Spooler | Service stopped |
| **Investigation** | Checked service status and configuration | Service confirmed stopped |
| **Root Cause** | Identified stopped service | Cause identified |
| **Fix** | Started Print Spooler | Service running |
| **Verification** | Performed final status check | Service operating correctly |

---

## 9. Commands Used

### Check service status

```powershell
Get-Service -Name Spooler
```

### Check service status and startup type

```powershell
Get-Service -Name Spooler | Select-Object Name, Status, StartType
```

### Stop the service

```powershell
Stop-Service -Name Spooler
```

### Start the service

```powershell
Start-Service -Name Spooler
```

### View detailed service information

```powershell
Get-Service -Name Spooler | Format-List *
```

### Check Windows service configuration

```powershell
sc.exe qc Spooler
```

### Check Service Control Manager events

```powershell
Get-WinEvent -LogName System -MaxEvents 50 |
Where-Object {$_.ProviderName -eq "Service Control Manager"} |
Select-Object -First 10 TimeCreated, Id, LevelDisplayName, Message
```

---

## 10. Tools Used

- Windows 11
- Oracle VirtualBox
- Windows PowerShell
- Windows Services
- Service Control Manager
- Windows Event Log

---

## 11. Skills Demonstrated

- Windows service troubleshooting
- PowerShell
- Windows administration
- Service status investigation
- Service configuration
- Event log investigation
- Root-cause identification
- Troubleshooting methodology
- Problem resolution
- Verification and testing
- Technical documentation

---

## 12. Key Learning

This exercise demonstrated how to troubleshoot a Windows service problem using PowerShell and built-in Windows service management tools.

The Print Spooler service was deliberately stopped to simulate a printing-related IT Support issue. The service status and configuration were investigated, the cause was identified, and the service was restarted.

The final service status was checked to confirm that the problem had been resolved.

The troubleshooting process followed:

**Problem → Investigation → Root Cause → Fix → Verification**
