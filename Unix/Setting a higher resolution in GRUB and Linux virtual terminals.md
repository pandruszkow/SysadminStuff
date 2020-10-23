## Accessing Virtual Terminals from VirtualBox
Normally, to access a Virtual Terminal `n`, you would press Ctrl+Alt+F`n` on your computer. These keys may be sometimes bound as a VirtualBox host key, and so can't be used. In those cases, press <Host Key>+F`n` instead to switch to the corresponding virtual terminal.

## Forcing a higher screen resolution in the Linux console
Follow https://wiki.archlinux.org/index.php/kernel_mode_setting#Forcing_modes.

Example: if `vbeinfo` tells you your maximum supported resolution is 1600x1200x32 on monitor `VGA-1`, 
add the following to your kernel command line:

`video=VGA-1:1600x1200`

### Notes
- This may or may not be necessary together with forcing a higher resolution in GRUB
- If you're using the proprietary NVidia drivers, you're out of luck. Sorry.

## Forcing a higher screen resolution in GRUB
Follow https://askubuntu.com/a/509422, except Step 3 (it's not needed)


