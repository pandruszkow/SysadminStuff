# VM UI improvement
VirtualBox has a lot of pointless chrome all around the UI. generally, I do the following to reduce it:

1. Go to VM's `Settings -> User Interface`
2. Untick bottom toolbar (generally useless unless one wants to track network/HDD activity in and out of the VM)
3. Untick `Mini toolbar -> Show in Full-screen/Seamless` (supremely and absolutely pointless for everyone - if I want the toolbar, I'll just exit fullscreen/seamless mode temporarily)
4. Unselect the top toolbar items for `File`, `Input`, `Debug`, and `Help`. Most of these are useless, most of the time. If I ever need them for a particular VM, I could just select them again.

# Dual-screen support (on Windows?)
This generally glitches out with a Windows host and Linux guest. For some reason the screen will stay "corrupted", with one VM display stuck on a black screen, and the other one unresponsive if one keeps switching between full-screen mode and not-fullscreen (e.g. to check Outlook).

Fix/workaround for this:
1. Enter fullscreen mode with dual VM display
2. Reproduce the screen crash
3. Switch to Scaled mode by pressing `Host+C`
4. Hard power-off the VM
5. Start the VM again

Your VM will now still use a dual-screen mode, but the displays will be scaled according to their previous fullscreen resolutions.

Simply maximise them with the usual Windows window controls, and you will receive a slightly squished version of the previous fullscreen set-up, but one that plays well with switching between the guest UI and the host UI.
