# Canon NoteJet BN700

This repository contains a curated set of essential files used in my Canon NoteJet NB700.
The goal is to preserve drivers, Canon utilities, and required system components needed to keep the original hardware fully operational (display, built-in printer, and Canon software).

## 📁 Folder Structure

### **`CANON/`**

A full dump of the original **Canon utilities**, extracted from a previous working installation.
This includes tools, configuration files, and all software components required by the Canon integrated printer/scanner system.

### **`DRIVER/`**

Display and printer drivers 

This folder contains two standalone installer packages, retrieved from [archive.org](https://archive.org/details/CanonComputerSystemWebsiteFiles1997), required to enable the laptop’s built-in hardware:

* **`Suunj3cx.exe`** — Installer for the **Canon BJ printer drivers** used by the NoteJet’s integrated printer;
* **`Opti_95.exe`** — Installer for the **OPTi video chip drivers**, required for the graphic card.

### **`SYSTEM/`**

A selection of **DLLs and system files** required by Canon Utilities contained in the `CANON` folder.

These files must be manually copied into:

```
C:\Windows\System
```

**Note**: `Threed.vbx`and `Vbrun300.dll`should be already available in the Windows installation.

## 🛠️ System.ini Modifications

To ensure the Canon NoteJet utilities load correctly, you must manually update the **`system.ini`** file (located in `C:\Windows` folder).

### 1. Edit the `[boot]` section

Add the reference to `SBS.DRV`:

```ini
[boot]
system.drv=system.drv
drivers=mmsystem.dll power.drv C:\CANON\OTHERS\SBS.DRV
```

### 2. Edit the `[386Enh]` section

Add the following virtual device drivers:

```ini
[386Enh]
device=*enable
device=VDCPD.386
device=C:\CANON\OTHERS\VSMB.386
device=C:\CANON\OTHERS\VSBS.386
```

## 🖥️ Windows Version

The system is running **Windows 95 OSR2.1**, which can be downloaded from [WinWorld](https://winworldpc.com/product/windows-95/osr-21).
