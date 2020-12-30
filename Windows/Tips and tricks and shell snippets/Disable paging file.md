# Why you might want to disable the paging file

- You're setting up/repurposing a very resource-constrained machine (like a thin client), and you're sure that you won't run out of RAM with the applications that are going to be running on it.
- Same as above, but you're setting up a special-purpose virtual machine instead and you're tight on space

Generally, *unless either of the above scenarios applies, you shouldn't disable the paging file*. It's more trouble than it's worth for a couple of gigabytes of space.

# Disable the pagefile via GUI


## Windows 7
1. Press `Win + PauseBreak`
3. On the left sidebar, click 'Advanced system settings'
4. Click 'Settings' button under '**Perfomance**'
5. Go to the 'Advanced' tab
6. Click 'Change...' button under 'Virtual memory'
7. Untick 'Automatically manage paging file size for all drives'
8. Select 'No paging file' radio button
9. Click 'Set' opposite that radio option
10. You will receive a warning that disabling the pagefile is a bad idea. It might well be. Click 'Yes' if you want to proceed.
10. Click OK for all three windows
11. Reboot the system


## Windows XP
1. Press `Win + PauseBreak`
2. Go to 'Advanced' tab
3. Click 'Settings' button under '**Perfomance**'
4. Go to 'Advanced' tab
5. Click 'Change...' button under 'Virtual memory'
6. Select 'No paging file' radio button
7. Click 'Set' opposite that radio option
8. Click OK for all three windows
9. Reboot the system


## Windows 10
\#TODO - probably different


# Disable the pagefile programmatically


**Assumptions:**
* you only have one pagefile on the system, under `C:\pagefile.sys`.
* you are not connected to anything else via WMIC. I am not responsible for any data loss or bricked machines if you are.


## Windows 7

In an elevated command line prompt, run:

```batchfile
REM Disable automatic paging file management - this has to be done so that we can deactivate the page file at all
wmic computersystem where name="%computername%" set AutomaticManagedPagefile=False
REM Tell Windows to stop using the pagefile
wmic pagefileset delete
```

The pagefile should be gone at the next reboot.

(With great thanks to [Moab's answer on StackOverflow](https://superuser.com/questions/952599/how-to-completely-disable-pagefile-use-wmic))


## Windows XP

This gunna be tricky. Windows XP doesn't clean up after itself like Windows 7 does.

1. Paste the text below to a `.reg` file somewhere. Once applied, this instructs Windows to remove `C:\pagefile.sys` on the next reboot. Fortunately, this also bypasses the Archive, Hidden and System `attrib` flags that would make it impossible to delete the file normally.

```reg
Windows Registry Editor Version 5.00

;The scary binary-encoded UTF-16 blob below is there because the multi-string key needs to end with two zero bytes, and we can't encode that in the format of a plain string.
[HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\Session Manager]
"PendingFileRenameOperations"=hex(7):5c,00,3f,00,3f,00,5c,00,43,00,3a,00,5c,00,\
  70,00,61,00,67,00,65,00,66,00,69,00,6c,00,65,00,2e,00,73,00,79,00,73,00,00,\
  00,00,00,00,00
```


2. Apply the `.reg` file from the previous step.

3. In an elevated command line prompt, run:

```batchfile
REM Tell Windows to stop using the file
wmic pagefileset delete
```
