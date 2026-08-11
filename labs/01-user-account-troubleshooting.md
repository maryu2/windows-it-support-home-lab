# Lab 01 — Windows User Account Troubleshooting

## Scenario

A user reported that they were unable to log into their Windows computer.

I deliberately created the issue in a controlled Windows 11 virtual machine to practise troubleshooting a common IT Support problem.

## Environment

* **Operating System:** Windows 11
* **Virtualisation Platform:** Oracle VirtualBox
* **Administrator Account:** `admm`
* **Test User:** `TestUser`
* **Tool:** PowerShell

---

## 1. Problem

The `TestUser` local Windows account was unable to access Windows.

To simulate this support issue, I deliberately disabled the account.

---

## 2. Initial Check

I logged into the Windows 11 VM using the administrator account `admm`.

I checked the local user account using PowerShell:

```powershell
Get-LocalUser -Name "TestUser"
```

The account was initially enabled:

```text
TestUser    True
```

This confirmed that the account was initially enabled before the troubleshooting scenario was created.

### Evidence

![Initial TestUser account status](../screenshots/lab-01/01-account-working.png)

---

## 3. Creating the Problem

I deliberately disabled the account using:

```powershell
Disable-LocalUser -Name "TestUser"
```

I then checked the account:

```powershell
Get-LocalUser -Name "TestUser"
```

The account showed:

```text
Enabled : False
```

This confirmed that the account had been disabled.

### Evidence

![TestUser account disabled](../screenshots/lab-01/02-account-disabled.png)

---

## 4. Investigation

I investigated the affected account using PowerShell.

The account status showed:

```text
TestUser    False
```

This identified the cause of the login problem.

### Root Cause

The `TestUser` local Windows account was disabled.

---

## 5. Fix

I logged back into Windows using the administrator account `admm`.

I opened PowerShell with administrator privileges and ran:

```powershell
Enable-LocalUser -Name "TestUser"
```

I then verified the account status:

```powershell
Get-LocalUser -Name "TestUser"
```

The account showed:

```text
Enabled : True
```

### Evidence

![TestUser account re-enabled](../screenshots/lab-01/03-account-re-enabled.png)

---

## 6. Verification

I signed out of the administrator account and logged in as `TestUser`.

The login was successful, and I was able to access the Windows desktop.

### Evidence

![Successful TestUser login](../screenshots/lab-01/04-successful-login.png)

This confirmed that the fix was successful.

---

## 7. Troubleshooting Summary

| Stage             | Action                  | Result                   |
| ----------------- | ----------------------- | ------------------------ |
| **Problem**       | User unable to log in   | Login problem identified |
| **Investigation** | Checked local account   | Account was disabled     |
| **Root Cause**    | `TestUser` was disabled | Cause identified         |
| **Fix**           | Re-enabled `TestUser`   | Account enabled          |
| **Verification**  | Logged in as `TestUser` | Login successful         |

---

## 8. Commands Used

### View local users

```powershell
Get-LocalUser
```

### Check a specific account

```powershell
Get-LocalUser -Name "TestUser"
```

### Disable a local account

```powershell
Disable-LocalUser -Name "TestUser"
```

### Enable a local account

```powershell
Enable-LocalUser -Name "TestUser"
```

---

## 9. Tools Used

* Windows 11
* Oracle VirtualBox
* Windows PowerShell
* Local User Management
* GitHub

---

## 10. Skills Demonstrated

* Windows user account troubleshooting
* Local user administration
* PowerShell
* Administrator privileges
* Root-cause identification
* Troubleshooting methodology
* Problem resolution
* Verification and testing
* Technical documentation
* GitHub

---

## 11. Key Learning

This exercise demonstrated how to investigate a Windows login problem by checking the status of a local user account.

The issue was identified by checking the account with PowerShell. The account was found to be disabled, so it was re-enabled using PowerShell.

The solution was then verified by successfully logging in as the affected user.

The troubleshooting process followed:

**Problem → Investigation → Root Cause → Fix → Verification**
