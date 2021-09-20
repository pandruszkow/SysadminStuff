Handling executable paths containing spaces and brackets on Git Bash for Windows
================================================================================

You may find that you want to change your `$EDITOR` to something more graphical on Windows, such as Notepad++. By default, it's installed under `C:\Program Files (x86)\Notepad++\notepad++.exe` if you installed a 32-bit version of Notepad++ on a 64-bit Windows.

In my case, the `(` caused a path parsing error, which wasn't resolved by any amount of escaping with backslash characters, changing separators from slashes to backslashes, or changing the type of quotes wrapping the `$EDITOR` value. Symlinking `notepad++.exe` resulted in simply copying the executable file to a different location, which will not work if your workstation is locked down to only run a whitelist of executables.

Solution: use the [auto-generated DOS shortname](https://en.wikipedia.org/wiki/8.3_filename#VFAT_and_Computer-generated_8.3_filenames) of the directory as the path. This is a compatibility feature that ensured that files bearing a filename that didn't fit into the 8.3 filename size limitation could be still accessed from DOS. Fortunately, they kept it on until the newest versions of Windows, and we can now use this to solve our problem.

This shortname can be found by running the command `cygpath -d <file-path>`, like so:

    cygpath "/c/Program Files (x86)/Notepad++/notepad++.exe
    
which on my machine returns:

    C:\PROGRA~2\NOTEPA~1\NOTEPA~1.EXE

In my case, I'm changing the value of the `$EDITOR` variable, so I tweak the path a little and append the following to my `.profile`:

    export EDITOR='C:/progra~2/notepa~1/notepa~1.exe'
    
**Backslashes were changed here into forward slashes** to avoid escaping issues (Windows doesn't care either way, Unix shell might).
I used lower-cased version of the filename as I find that it looks less jarring in a config file (Windows filenames are not case-sensitive, so you can use either, Unix config files with uppercased paths look a bit out of place).
