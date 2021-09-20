# Via Registry (PendingFileRenameOperations)

1. Go to `HKLM\SYSTEM\CurrentControlSet\Control\Session Manager`
2. Under this key, add a Multi-String Value named `PendingFileRenameOperations`
3. Type in the full path of the file you want to delete, prefixed with `\??\`. Do not add any quoting if the filename contains spaces.
    - e.g. `C:\test 1.sys` would be written as `\??\C:\test 1.sys`
4. Save the value
5. Right-click on the value name, select `Modify Binary Data`
6. Click on the hex section on the left and add four hex zeroes (two zero bytes) at the end of the string.

The file should be gone on the next reboot.

(With thanks to [Q's Tech Babble article on this topic](https://qtechbabble.wordpress.com/2020/06/26/use-pendingfilerenameoperations-registry-key-to-automatically-delete-a-file-on-reboot/))
