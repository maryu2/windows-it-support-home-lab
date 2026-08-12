# Windows IT Support Troubleshooting Home Lab

## Overview

A hands-on Windows troubleshooting home lab created to develop and demonstrate practical IT Support skills.

The lab uses a Windows 11 virtual machine running in Oracle VirtualBox. Common Windows issues are deliberately created in a controlled environment, investigated using built-in Windows tools and command-line utilities, resolved, and documented.

Each troubleshooting exercise follows a structured process:

**Problem → Investigation → Root Cause → Fix → Verification**

The purpose of this project is to build practical troubleshooting experience and demonstrate the ability to investigate, resolve, test, and document common Windows IT Support issues.

---

## Lab Environment

- **Operating System:** Windows 11
- **Virtualisation Platform:** Oracle VirtualBox
- **PowerShell**
- **Command Prompt**
- **Event Viewer**
- **Device Manager**
- **Task Manager**
- **Windows Services**
- **GitHub**

---

# Troubleshooting Labs

## Lab 01 — Windows User Account Troubleshooting

**Status:** Completed

A local Windows user account was deliberately disabled to simulate a user login problem.

The issue was investigated using PowerShell. The account status was checked, the root cause was identified, the account was re-enabled, and the solution was verified by successfully logging into Windows as the affected user.

### Skills Demonstrated

- Windows user account troubleshooting
- Local user administration
- PowerShell
- Administrator privileges
- Root-cause identification
- Troubleshooting methodology
- Problem resolution
- Verification and testing
- Technical documentation

### Tools Used

- Windows 11
- Oracle VirtualBox
- PowerShell
- Local User Management

[View Lab 01 — Windows User Account Troubleshooting](labs/01-user-account-troubleshooting.md)

---

## Lab 02 — Windows DNS Troubleshooting

**Status:** Completed

A controlled DNS configuration problem was deliberately created in the Windows virtual machine.

The investigation used `ipconfig`, `ipconfig /all`, `ping`, `nslookup`, and `netsh` to determine whether the issue was related to general network connectivity or DNS resolution.

The VM was able to communicate with an external IP address while DNS resolution was failing. The DNS configuration was investigated, the incorrect DNS server was identified, the original configuration was restored, and DNS resolution was successfully verified.

### Skills Demonstrated

- Windows DNS troubleshooting
- Network connectivity testing
- DNS resolution testing
- IP configuration
- Command-line diagnostics
- Network configuration
- Root-cause identification
- Troubleshooting methodology
- Problem resolution
- Verification and testing
- Technical documentation

### Tools Used

- Windows 11
- Oracle VirtualBox
- Command Prompt
- `ipconfig`
- `ping`
- `nslookup`
- `netsh`

[View Lab 02 — Windows DNS Troubleshooting](labs/02-dns-troubleshooting.md)

---

## Lab 03 — Windows Service Troubleshooting

**Status:** Completed

A Windows Print Spooler service problem was deliberately created in the Windows virtual machine to simulate a service-related printing issue.

The Print Spooler service was stopped and investigated using PowerShell and Windows service management tools. The service status and configuration were checked, the root cause was identified, the service was restarted, and the result was verified.

### Skills Demonstrated

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

### Tools Used

- Windows 11
- Oracle VirtualBox
- PowerShell
- Windows Services
- Service Control Manager
- Windows Event Log

[View Lab 03 — Windows Service Troubleshooting](labs/03-windows-service-troubleshooting.md)

---

# Evidence

Completed labs include supporting screenshots documenting the troubleshooting process.

Evidence may include:

- Initial system state
- The deliberately created problem
- Investigation and diagnostic results
- Commands and tools used
- The identified root cause
- The applied fix
- Verification that the problem was resolved

Screenshots are stored in the repository's `screenshots/` directory and referenced from the relevant lab documentation.

---

# Troubleshooting Method

Each lab follows a consistent troubleshooting approach:

### 1. Problem

Identify and describe the issue from the user's perspective.

### 2. Investigation

Gather information using appropriate Windows tools and commands.

### 3. Root Cause

Identify the most likely cause based on the investigation and diagnostic results.

### 4. Fix

Apply an appropriate solution.

### 5. Verification

Test the system again to confirm that the problem has been resolved.

### 6. Documentation

Document the troubleshooting process, commands used, results, and supporting evidence.

---

# Skills Developed

Through this home lab, I have developed practical experience in:

- Windows troubleshooting
- User account administration
- PowerShell
- Command-line troubleshooting
- Network and DNS diagnostics
- Windows Services
- Event log investigation
- Root-cause analysis
- Problem resolution
- Verification and testing
- Technical documentation

---

# Project Goal

The goal of this project is to build practical Windows IT Support skills through hands-on troubleshooting in a controlled virtual environment.

Rather than only documenting theoretical knowledge, each lab involves deliberately creating a problem, investigating the symptoms, identifying the cause, applying a solution, and verifying the result.

This approach demonstrates a structured and methodical approach to IT Support troubleshooting.

---

# Lab Status

**Completed: 3 of 3 labs**

- [x] Lab 01 — Windows User Account Troubleshooting
- [x] Lab 02 — Windows DNS Troubleshooting
- [x] Lab 03 — Windows Service Troubleshooting

All three planned troubleshooting scenarios have been completed and documented.
