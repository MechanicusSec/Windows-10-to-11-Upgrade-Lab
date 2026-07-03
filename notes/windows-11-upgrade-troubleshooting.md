# Windows 11 Upgrade Troubleshooting Notes

## Purpose

This document summarizes common issues that can appear during a Windows 10 to Windows 11 upgrade and how they can be checked or resolved in an IT support environment.

The notes are based on a local VMware lab upgrade from Windows 10 Pro to Windows 11 Pro.

---

## Common issue: TPM not detected

### Symptom

Windows 11 Setup says that the PC does not meet the requirements because TPM is missing.

### Possible causes

* TPM is disabled in firmware.
* The VM does not have a virtual TPM.
* The VM is not encrypted, so VMware cannot add a TPM.
* Windows does not detect the TPM correctly.

### Checks

```powershell
Get-Tpm
```

Expected result:

```text
TpmPresent : True
TpmReady   : True
```

### Fix

In VMware:

```text
VM Settings → Options → Access Control → Encrypt
VM Settings → Hardware → Add → Trusted Platform Module
```

---

## Common issue: Secure Boot not enabled

### Symptom

Windows 11 Setup says Secure Boot is required.

### Check

```powershell
Confirm-SecureBootUEFI
```

Expected result:

```text
True
```

### Fix

In VMware:

```text
VM Settings → Options → Advanced → Firmware type → UEFI
Enable Secure Boot
```

---

## Common issue: VM uses BIOS instead of UEFI

### Symptom

Secure Boot cannot be enabled or Windows 11 compatibility checks fail.

### Cause

The virtual machine was created using BIOS firmware instead of UEFI.

### Fix

Use UEFI firmware before installing Windows.

Changing firmware after an operating system installation can make the VM unbootable, so this should be planned before installation when possible.

---

## Common issue: Not enough disk space

### Symptom

Windows Setup reports that more disk space is needed.

### Check

```powershell
Get-PSDrive C
```

### Fix

* Remove temporary files.
* Run Disk Cleanup.
* Increase the virtual disk size in VMware if needed.
* Ensure there is enough free space for upgrade files and rollback files.

---

## Common issue: Windows Update gets stuck

### Symptom

Windows Update remains stuck downloading or installing.

### Checks

Restart the VM and check again:

```text
Settings → Windows Update → Check for updates
```

### Possible fixes

* Restart Windows.
* Check internet access.
* Check free disk space.
* Wait if the VM is slow.
* Retry Windows Update after reboot.

---

## Common issue: Ping fails but internet works

### Symptom

```powershell
ping microsoft.com
```

times out, but websites or updates still work.

### Explanation

Some hosts or firewalls block ICMP ping traffic. This does not always mean internet access is broken.

### Better test

```powershell
Test-NetConnection microsoft.com -CommonTCPPort HTTP
```

Expected result:

```text
TcpTestSucceeded : True
```

---

## Common issue: VMware Tools not detected

### Symptom

Mouse, display, clipboard or drivers behave poorly after installation or upgrade.

### Check

```powershell
Get-Service VMTools
```

Expected result:

```text
Running  VMTools  VMware Tools
```

### Fix

In VMware:

```text
VM → Install VMware Tools
```

Then inside Windows:

```text
This PC → VMware Tools DVD → setup.exe
```

Choose:

```text
Typical
```

Restart when prompted.

---

## Common issue: Windows version fields look confusing

### Symptom

PowerShell shows a Windows build that looks like Windows 11, but `WindowsProductName` may still show Windows 10.

### Example

```text
WindowsProductName : Windows 10 Pro
OsBuildNumber      : 26200
```

### Explanation

Some compatibility fields can retain Windows 10 naming internally.

### Better verification

Use:

```powershell
winver
```

Also check:

```powershell
Get-ComputerInfo | Select-Object WindowsProductName,WindowsVersion,OsBuildNumber
```

Use `winver` and the OS build as stronger evidence.

---

## Common issue: Setup wants to keep nothing

### Symptom

The Windows 11 Setup screen says it will keep nothing, or does not offer to keep personal files and apps.

### Cause

Possible causes include:

* Language mismatch.
* Edition mismatch.
* Unsupported upgrade path.
* Starting setup incorrectly.
* Booting from ISO instead of running setup from inside Windows.

### Fix

Start the upgrade from inside Windows 10:

```text
Mounted Windows 11 ISO → setup.exe
```

Confirm the ready screen says:

```text
Keep personal files and apps
```

Do not continue if it says:

```text
Keep nothing
```

---

## Common issue: Windows 11 ISO not mounted

### Symptom

The Windows 11 installation files do not appear in File Explorer.

### Possible causes

* The ISO is not attached to the VM.
* The virtual CD/DVD drive is disconnected.
* The wrong ISO is attached.
* The VM was started before the ISO was connected.

### Checks

In VMware:

```text
VM Settings → Hardware → CD/DVD (SATA)
```

Confirm:

```text
Use ISO image file
Connect at power on
```

### Fix

Attach the Windows 11 ISO again, then open:

```text
File Explorer → This PC → DVD Drive
```

---

## Common issue: Upgrade starts as a clean install

### Symptom

Windows Setup does not offer to keep personal files and apps.

### Cause

The VM may have booted from the ISO instead of running `setup.exe` from inside Windows 10.

### Fix

Start Windows 10 normally first.

Then open the mounted Windows 11 ISO from inside Windows 10 and run:

```text
setup.exe
```

This starts the in-place upgrade path.

---

## Common issue: Optional preview update appears after upgrade

### Symptom

Windows Update says the system is up to date but also shows an optional preview update.

### Explanation

Optional preview updates are not required for a normal upgrade validation lab.

They are optional non-security previews and can be skipped unless there is a specific reason to test them.

### Lab decision

The optional preview update was not installed.

---

## Lab result

The lab upgrade completed successfully.

The final upgrade path was:

```text
Windows 10 Pro → Windows 11 Pro
```

Files and apps were kept.

TPM, Secure Boot, VMware Tools, Device Manager and Windows Update were verified after upgrade.
