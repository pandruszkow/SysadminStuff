Desktop
=======
- Windows improvements applied
  - Classic Start Menu installed and configured from the XML backup
- Windows bugfixes applied

- Daily driver programs installed
  - Vivaldi (serious work)
  - Firefox (personal/research work)
  - Notepad++ (notes+scratch+source reading)
  - Keepass 2 (password manager)
  - VirtualBox (for VMs, **WITHOUT VBOX ADDITIONS**, those aren't licensed for commercial use)
  - Rambox (Community Edition, for Teams if used in your organisation)
  
- Utility programs installed
  - 7-Zip (sane+compatible compression)
  - WinMerge (or work-alike)
  - WinDirStat (or work-alike, QDirStat on Linux)
  - MobaXterm (Linux access)
  - WinSCP (Linux access - todo: is this obsolete?)
  - Python 3 (generic scripting)
  - Git for Windows (git, Unix utilities on Windows)
  - jq (JSON parsing)
  
~~- Keybase installed to be able to sync personal but company-related data (invoices for reimbursed items, payslips,...)~~
  - note: Keybase isn't healthy any more, so 
- Data + browser profile transferred over
  - Vivaldi
  - Firefox
- Remove unneeded shortcuts from desktop, taskbar and Start Menu
- Put daily use shortcuts on desktop
- Pin daily use programs to taskbar
- Pin frequent use programs/settings panels to Start Menu
- Rearrange `All Programs` in Start Menu to
  - only hold the programs you need (can always re-add from Program Files if suddenly needed, usually)
  - reorganise programs into logical folders (per vendor - Microsoft Office and other software suites, per category - Utilities, move driver/third-party vendor control panels under `Windows System`)
  - set existing shortcuts to hidden and system, in case their removal is overwritten by organisation-based app updates
- Ensure date is set ISO8601 format: yyyy-MM-dd
- Ensure clock is set to 24h
- Ensure the keyboard is set to the Polish layout (remove UK layout as well)

Power settings (laptop)
=========================

#### In Windows:
  1. Reconfigure the "Performance" mode
      1. Set lid close to do nothing when plugged in, sleep/hibernate when unplugged
      2. Set sleep timeout to never
      3. Set minimum CPU power to 100% when plugged in, 5% when unplugged
  2. Create a "Lid closed always-on" mode
      1. Set lid close to do nothing, whether plugged in or not
      2. Set minimum CPU power to 5%, maximum 20% when plugged in, maximum 10% when unplugged
      3. Set display timeout to 5 minutes if plugged in, 2 minuted if unplugged

#### In BIOS/firmware (if options below are available):
1. Enable Numlock on boot (if laptop is generally used in a docked setup)
2. Enable slow boot and USB device emulation (if needed for inputting text from USB keyboard while in legacy/bootloader mode/DOS)
3. Enable power on when lid is opened
4. Enable power on when AC adapter is plugged in


Custom keyboard shortcuts
=========================
This can be set up in 2 ways on Windows (both don't require admin access):

- Set `Shortcut key` property on an application shortcut file
  - **Pro**: no third-party software needed
  - **Con**: limited selection of shortcut combinations (for example, can't bind Ctrl+Alt+T to terminal as is customary for Linux)

- Use [AutoHotkey](https://autohotkey.com/)
  - **Pro**: is a fully-fledged scripting language (more powerful than launching an application - can control volume, close windows, native DLL calls etc.)
  - **Pro**: can use any shortcut combination imaginable
  - **Pro**: can compile script to a standalone, self-contained executable
  - **Con**: is a fully-fledged scripting language with a syntax of its own, so some web searching will be necessary to set it up
  - **Con**: occasionally flagged as false-positive by AV and anti-malware programs **(make sure you get it from the official project website!)**
  - **Con**: doesn't work if running third-party software is disallowed
