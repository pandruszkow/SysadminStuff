## Scenario

You have a Windows C: drive using the NTFS file system. You would like to move all or some of the data to a brand-new ext4 partition on the same drive, but you don't have a spare hard drive to store the data while you're working with the partitions.

**exFAT WILL NOT WORK WITH THIS GUIDE.** It cannot shrink or grow at all. **XFS, JFS and UFS2** cannot be shrunk, meaning you can migrate data _to_ them, but not _from_ them, using this technique.

### Warnings

0. DO NOT POWER OFF THE COMPUTER DURING STEP 9. THIS WILL DESTROY YOUR DATA.
1. THERE IS NO TL;DR. IT'S NOT SAFE TO SKIP READING ANY OF THE BELOW. Read the list in its entirety before starting. It's a complicated process, and you should understand it fully before attempting it. It will make your data into mincemeat if you miss crucial steps.
2. This process assumes you will not lose power to the computer at any point. If it's a laptop, use a charger.
3. Back up as much of the most important data before starting. You can usually find a spare USB drive with a few gigabytes free, or even put the data in the cloud temporarily. This process _usually_ won't create problems, but if you care about the data, make that backup.
4. DO NOT POWER OFF THE COMPUTER DURING STEP 9. Once you initiate it, don't touch the computer until it's done. Yes, I listed this twice. It's _important_.
5. NEVER shrink or grow NTFS from outside Windows, just to be sure. Windows knows how to shrink NTFS far better than other platforms.

### The steps
Step 1. Create a GParted Live USB/CD

Step 2. Boot into Windows

Step 3. Remove all files that you can (cache, downloads, old files and programs you won't be using).

Step 3.5. Defragment the drive - yes, that applies even to SSD using this technique. Auslogics Disk Defrag <= v.4.5.00 works pretty well for this, but other third party utils that move all data to the beginning of the partition work equally well. I advise don't use the built-in Windows defragger for this technique - I don't know what it does, so I don't know it works for what I want to do in this step.

Step 4. Go to the Disk Managment console (like the one in [this screenshot](https://web.archive.org/web/20210704213407im_/https://docs.microsoft.com/en-us/windows-server/storage/disk-management/media/disk-management.png)). Pick the C: drive, and use the "shrink volume" option to reduce it to as small a size as you can. Leave about 10 GB free if you can.

Step 5. Once shrinking is complete, boot into GParted Live. Create a Linux ext4/zfs/btrfs/whatever partition to fill all the unallocated space.

Step 6. Mount both the Linux partition and the NTFS partition (C: drive). Move as many files as you can from C: to the Linux partition, until you run out of space on the Linux partition.

Step 7. Reboot into Windows. You should now see that the Windows partition has a lot more space available.

Step 8. Repeat steps 3.5 and 4 - defrag the Windows partition, then shrink it to minimum size + 10 GB.

Step 9. Boot into GParted Live again, and this time use the "move partition" feature to move the Linux partition to the left, to the beginning of the unallocated space. This will move all the contents of the Linux partition a few gigabytes to the left, byte by byte.

Step 10. Use the "grow partition" feature to expand your Linux partition to the max possible size.

Step 11. Repeat steps 6-10 until you moved all the data you want to the Linux partition

This works for every combination of filesystems (or, _almost_ every combination of filesystems). Whether you're migrating NTFS-> ext4, or ext4->BTRFS or whatever, it will work just fine as long as you can shrink the source FS and grow the destination FS. 
