# Windows 10 to Windows 11 Upgrade Lab — Logbook

## 2026-07-03 — Part 1: Project setup

### Goal

Create the documentation structure for the Windows 10 to Windows 11 Upgrade Lab.

### Work completed

* Created the main project folder.
* Created documentation folders.
* Created `README.md`.
* Created `logbook.md`.
* Created `.gitkeep` files so Git can track empty folders.
* Opened the project in VS Code.
* Prepared the lab for step-by-step documentation.

### Project structure

```text
Windows-10-to-11-Upgrade-Lab/
├── docs/
│   └── .gitkeep
├── notes/
│   └── .gitkeep
├── results/
│   └── .gitkeep
├── screenshots/
│   └── .gitkeep
├── logbook.md
└── README.md
```

### Commands used

```powershell
cd C:\Users\*****
mkdir Windows-10-to-11-Upgrade-Lab
cd Windows-10-to-11-Upgrade-Lab

mkdir docs
mkdir screenshots
mkdir results
mkdir notes

New-Item README.md
New-Item logbook.md
New-Item docs\.gitkeep
New-Item screenshots\.gitkeep
New-Item results\.gitkeep
New-Item notes\.gitkeep

code .
```

### Command purpose

| Command | Purpose |
| --- | --- |
| `cd C:\Users\*****` | Moves PowerShell to the user folder. |
| `mkdir Windows-10-to-11-Upgrade-Lab` | Creates the main project folder. |
| `cd Windows-10-to-11-Upgrade-Lab` | Moves into the project folder. |
| `mkdir docs` | Creates the documentation folder. |
| `mkdir screenshots` | Creates the screenshot evidence folder. |
| `mkdir results` | Creates the command output and result folder. |
| `mkdir notes` | Creates the troubleshooting notes folder. |
| `New-Item README.md` | Creates the main project overview file. |
| `New-Item logbook.md` | Creates the step-by-step project logbook. |
| `New-Item .gitkeep` | Creates placeholder files so Git can track empty folders. |
| `code .` | Opens the project folder in VS Code. |

### Notes

This part created the documentation base for the lab.

The project will be documented step by step so the Windows 10 to Windows 11 upgrade process can be used as a portfolio project.

No real passwords, private account names, production devices, company data or license keys should be included in public documentation.

### Evidence

Screenshot:

![screenshot-01-project-structure.png](screenshots/screenshot-01-project-structure.png)

---

## 2026-07-03 — Part 2: Windows 10 ISO preparation

### Goal

Download and prepare a Windows 10 ISO for use in VMware.

### Work completed

* Downloaded the Windows 10 ISO with the Microsoft Media Creation Tool.
* Located the ISO after download.
* Reviewed the ISO folder.
* Identified that other ISO files in the folder were not Windows 10.
* Verified that the Windows Server ISO was not the correct Windows 10 file.
* Copied the Windows 10 ISO from OneDrive to a local ISO folder.
* Renamed the ISO to a clear lab filename.
* Confirmed VMware detected the ISO as Windows 10 x64.

### ISO files reviewed

| File | Result |
| --- | --- |
| `SERVER_EVAL_x64FRE_en-us.iso` | Windows Server evaluation ISO, not used |
| `rhel-10.1-x86_64-dvd.iso` | Red Hat Enterprise Linux ISO, not used |
| `Win11_25H2_EnglishInternational_x64_v2.iso` | Windows 11 ISO, kept for later upgrade |
| `Win10_22H2_English_x64.iso` | Windows 10 ISO, used for this lab |

### Commands used

```powershell
Get-ChildItem "C:\Users\*****\Documents\ISO" | Select-Object Name,Length,LastWriteTime

Get-ChildItem "C:\Users\*****" -Filter *.iso -Recurse -ErrorAction SilentlyContinue |
Select-Object FullName,Length,LastWriteTime

Copy-Item "C:\Users\*****\OneDrive\Dokument\Windows.iso" "C:\Users\*****\Documents\ISO\Win10_22H2_English_x64.iso"

Get-ChildItem "C:\Users\*****\Documents\ISO" | Select-Object Name,Length,LastWriteTime
```

### Command purpose

| Command | Purpose |
| --- | --- |
| `Get-ChildItem` | Lists files in a folder. |
| `Select-Object Name,Length,LastWriteTime` | Shows file name, file size and modified time. |
| `-Filter *.iso` | Searches only for ISO files. |
| `-Recurse` | Searches through subfolders. |
| `-ErrorAction SilentlyContinue` | Hides permission errors during searching. |
| `Copy-Item` | Copies the Windows ISO from OneDrive to a local ISO folder. |

### Notes

The ISO was copied away from OneDrive because large lab files are safer in a normal local folder.

OneDrive can sync, lock or interfere with large files, so local VM and ISO paths are preferred.

Written documentation should anonymize personal folder paths.

---

## 2026-07-03 — Part 3: VMware VM creation

### Goal

Create a VMware virtual machine for the Windows 10 to Windows 11 upgrade lab.

### Work completed

* Created a new VMware virtual machine.
* Selected the Windows 10 ISO.
* Confirmed VMware detected Windows 10 x64.
* Named the VM `Win10-to-Win11-Upgrade-Lab`.
* Set the VM location outside OneDrive.
* Set the virtual disk to 80 GB.
* Used split virtual disk files.
* Increased memory from 2 GB to 8 GB.
* Configured 2 CPU cores.
* Confirmed NAT networking.
* Enabled UEFI firmware.
* Enabled Secure Boot.
* Encrypted TPM support files.
* Added a virtual Trusted Platform Module.

### Final VM settings

| Setting | Value |
| --- | --- |
| VM name | Win10-to-Win11-Upgrade-Lab |
| Location | `C:\VirtualMachines` |
| Operating system | Windows 10 x64 |
| Firmware | UEFI |
| Secure Boot | Enabled |
| TPM | Present |
| Memory | 8 GB |
| CPU | 2 cores |
| Disk | 80 GB |
| Network | NAT |
| CD/DVD | Windows 10 ISO |

### Notes

The VM was configured to support a future Windows 11 upgrade.

UEFI, Secure Boot and TPM were configured before Windows 10 installation so the VM would match Windows 11 compatibility expectations.

VMware required encryption before adding a virtual TPM.

Only the files needed to support the virtual TPM were encrypted.

---

## 2026-07-03 — Part 4: Windows 10 installation

### Goal

Install Windows 10 Pro in the VMware virtual machine.

### Work completed

* Booted the VM from the Windows 10 ISO.
* Started Windows Setup.
* Installed Windows 10 to the 80 GB virtual disk.
* Selected Sweden as the region.
* Used a local/offline account instead of a personal Microsoft account.
* Created a generic lab user named `LabUser`.
* Completed Windows first-time setup.
* Reached the Windows 10 desktop.

### Installation choices

| Step | Selection |
| --- | --- |
| Region | Sweden |
| Account type | Offline/local account |
| Lab username | LabUser |
| Edition | Windows 10 Pro |
| Install type | Custom install |
| Disk | 80 GB virtual disk |

### Notes

A local account was used to avoid connecting personal Microsoft account data to the lab VM.

Generic lab names should be used in screenshots and documentation.

No real personal Microsoft account, private email address or real password was used.

---

## 2026-07-03 — Part 5: Windows 10 baseline verification

### Goal

Verify the installed Windows 10 version before preparing for the Windows 11 upgrade.

### Work completed

* Opened the Windows 10 desktop.
* Ran `winver`.
* Confirmed Windows 10 Pro was installed.
* Confirmed Windows 10 version 22H2.
* Confirmed OS Build 19045.3803.
* Confirmed the lab user is `LabUser`.

### Verification result

| Item | Result |
| --- | --- |
| Operating system | Windows 10 Pro |
| Version | 22H2 |
| OS Build | 19045.3803 |
| Lab user | LabUser |

### Command used

```powershell
winver
```

### Command purpose

| Command | Purpose |
| --- | --- |
| `winver` | Opens the About Windows dialog and shows Windows edition, version and build number. |

### Notes

This confirms that Windows 10 was installed successfully.

The VM is now ready for deeper baseline checks, including TPM, Secure Boot, UEFI, disk space, memory and update status.

### Evidence

Screenshot:

![screenshot-02-windows-10-winver.png](screenshots/screenshot-02-windows-10-winver.png)

### Result

Windows 10 Pro 22H2 was installed successfully and verified with `winver`.
