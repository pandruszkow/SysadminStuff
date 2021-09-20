# Keyboard layout keeps changing - fix

As of the time of writing, Windows 10 decided to map Ctrl + Shift and/or Alt + Shift keyboard shortcuts so that they switch the keyboard layout. That's obviously Pretty Annoying(tm) when you're a programmer, because you probably hit those keys dozens of times a day.

Instructions to disable this behaviour:
1. Press `Win + R`, type `ms-settings:typing`, press Enter
2. Scroll down to the bottom, click `Advanced keyboard settings`
3. In the `Switching input methods` section, click `Language bar options`
4. Click on tab `Advanced Key Settings`
5. In the lower-right corner, click the button `Change Key Sequence...`
6. Change `Switch Input Language` to `Not assigned`
7. Change `Switch Keyboard Layout` to `Not assigned`
8. Press `OK`
