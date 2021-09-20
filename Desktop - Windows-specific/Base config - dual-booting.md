#  Dual-booting with Linux or another OS

## Disable Fast start-up in Windows 10

Dual booting often needs to allow reading Windows data from Linux In "fast start-up" mode, Windows will restart the system and hibernate instead of just shutting down, thus keeping the NTFS partition "in use" and potentially triggering weird hardware states that your computer or hypervisor may not recover from.

1. Open the traditional Control Panel
2. Go to `Power Options -> Change what the power buttons do`
3. Untick `Turn on fast start-up (recommended)`

## Setting hardware RTC interpretation to UTC

Linux expects the RTC to be in UTC, Windows in localtime. The solution is to either match Linux configuration with Windows defaults, or vice versa. There's an undocumented .reg fix that when applied, makes Windows read the RTC as UTC time. Online reports claim it may be buggy, but it works well enough for me.

