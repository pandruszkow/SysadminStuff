List all open ports and applications listening on them (TCP)
===========================================================
To view all TCP-attached processes along with their PIDs, run:

    sudo ss -tnlp
    
Omitting the `sudo` elevation will mean that the PID/process names will be invisible for some of the services (those running as the system user). 


**For legacy Linux systems:** `ss` may be unavailable. Try the below `netstat` command instead (`netstat` is obsolete on modern Linux systems, per its manpage): 
    
    netstat -tulpn

(Thanks, [tecadmin.net](https://tecadmin.net/setup-mail-forwarding-in-postfix-on-linux/)!)

Convert an audio file into a video with a static background
===========================================================

Use the command below, and replace filenames as necessary.

(NOTE: you will need to have `ffmpeg` installed on your computer)

    ffmpeg -loop 1 -framerate 2 \
    -i background.jpg \
    -i audio.mp3 \
    -c:v libx264 -preset medium -tune stillimage -crf 18 -c:a copy -shortest -pix_fmt yuv420p \
    outp-video.mkv

Notification of command completion with a 'bell' character
==============================================================

When you launch a long-running process in the terminal windows, and wish to be alerted whenever it finishes, you can have the terminal output the ASCII bell character. This usually does one or more of the following things:

 * Flashes the terminal window by reversing the background and foreground colour for a fraction of a second
 * Produces a beep via the OS's audio system or the built-in PC speaker
 * Flashes or otherwise animates the taskbar button for the terminal window (if supported by your OS/desktop env./WM)

**Linux**

Use the command `tput bel` or `echo -e "\a"`.

I prefer the first form, since it makes the intent clearer and works better if shell quoting is playing havoc with your arguments. I've used this in my .gitconfig, since the alias quoting gets confusing and annoying very quickly

**Windows**

Type the command `echo ^G` (where `^G` is produced by typing Ctrl+G on the keyboard).

(Source: [Bell character article on Wikipedia](https://en.wikipedia.org/wiki/Bell_character))

Run a quick hashed index of the current directory
=================================================
The command below will recursively hash a directory, sorting it by name, and reverse the hashsum with the file path of each file. This can be used as an ad-hoc diff of two directories that can't be accessed simultaneously (like for VM snapshots). Simply run the script for each dir, then diff both output files and look for differences (missing/added lines, different hashes).

     find . -type f -exec sha256sum '{}' + | awk '{print $2,$1}' | sort > VM_Shared_Folder/dir-index.sha256.txt

Note: this may not be safe for paths that contain spaces or tabs.

(Thanks, [SvennD](https://www.svennd.be/recursively-md5sha1sha256sha512-a-directory-with-files/))
