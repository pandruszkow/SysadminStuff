## Disabling Microsoft Office AutoUpdate

You may have to stop the Microsoft AutoUpdate app first before removing it. If so, follow these steps:

1. Open a Terminal window
2. `ps -e | grep Microsoft`
3. Locate the PID of the Microsoft AutoUpdate app
4. `kill -9 <Microsoft AutoUpdate app PID`

Then, follow [this guide by Paul Horowitz from OSX Daily](https://osxdaily.com/2019/07/20/how-delete-microsoft-autoupdate-mac/).

1. In Finder, press `Cmd+Shift+G` to go to `/Library/Application Support/Microsoft/`
2. Locate the directory that contains the Microsoft AutoUpdate app (likely `MAU2.0` or similar`)
3. Drag the Microsoft AutoUpdate app file to Trash

If you'd prefer to not remove the updater, compress it into a ZIP archive instead.

## Outlook macro support

Not present in the macOS version. Use AppleScript instead.
