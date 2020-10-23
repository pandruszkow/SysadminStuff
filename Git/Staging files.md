# Selective staging of changes
If you have made changes in more than one part of a file, Git will also allow you to select which ones go into the staging area. Simply run the command as follows:

`git add -p <file>` 

Git will now go through each fragment of the file that's been changed and show you a diff between the old and new version. You can choose to accept/reject/edit etc each fragment as you see fit.

**TODO:** figure out how to make this a BBS-style option selection, so that Git moves directly to the next fragment as soon as `y`/`n` is pressed on the keyboard.
