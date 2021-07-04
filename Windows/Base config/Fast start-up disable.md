## Disable Fast start-up in Windows 10

1. Open the traditional Control Panel
2. Go to `Power Options -> Change what the power buttons do`
3. Untick `Turn on fast start-up (recommended)`

### Why?

Dual booting with the need to read Windows data from Linux, or VM/hardware bugs. In "fast start-up" mode, Windows will restart the system and hibernate instead of just shutting down, thus keeping the NTFS partition "in use" and potentially triggering weird hardware states that your computer or hypervisor may not recover from.
