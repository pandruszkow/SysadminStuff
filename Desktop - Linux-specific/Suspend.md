# Suspend the machine (sleep mode)

## GNOME-based (Ubuntu 18.04)

GNOME as of Ubuntu 18.04 LTS allows triggering suspend (sleep) out of the box.

1. Click the system tray in the upper-rightmost corner
2. Click on `Power Off / Log Out`
3. To access the Sleep button (two parallel vertical lines, like a 'pause' button), either:
   - Hold down `Alt` so the Power Off button temporarily turns into the Suspend button, OR
   - Long-press the Power Off button, then release it. It will turn into the Suspend button, which you can now click.

It's worth noting that the first method is reminiscent of the Windows XP power-off dialog, in that suspending the machine required pressing down Shift to access this option.
The second method is less cumbersome if it's desirable to operate the suspend dialogue using only the mouse/touchpad.

## Command line (systemd)
(May require elevation)
```shell
systemctl suspend
```

## Command line (older power management systems)
(May require elevation)
```shell
pm-suspend
```
