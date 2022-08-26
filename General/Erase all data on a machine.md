# Standard procedure for wiping a machine in Linux

Requirements: 
- an Ubuntu live USB medium
- the nwipe package from [here](https://packages.ubuntu.com/jammy/nwipe). Make sure you download the package for the same Ubuntu version as your live USB. Copy the package onto the USB alongside the Ubuntu system files so that it's easy to find.

## Part 1 - get the machine into the right state & confirm drive details
0. Remove any drives you *do not* intend to wipe from the computer.
1. Boot the computer.
    - You may wish to load the entire system into RAM with the `toram` boot parameter (for Debian/Ubuntu derivatives) and remove the live medium to ensure it's not accidentally wiped.
3. Put the machine into sleep mode (`systemctl suspend`), and then wake it up again.
    - This step is needed to unfreeze the security on the drive, so we can set the security password.
    - If this doesn't work, or the machine wakes up with garbled graphics on the screen, then start over with the guide while skipping Part 2.
2. Enumerate the drives to confirm which drive letter(s) the disk(s) to be wiped received from the Linux kernel. Run `lsblk`.
4. For each drive you intend to erase, run `hdparm -I /dev/sdX | less` to confirm:
    - the capacity, make, model (and optionally serial number) of the drive (these should be listed at the start of the output)
    - the security status. This should be listed as `not enabled`, `not locked` and `not frozen`
      - If you are seeing `frozen` instead of `not frozen`, try suspending the machine and waking it again.
    - whether the drive supports ATA Enhanced Erase. We'll use this in the next part.
5. Find out what your `/dev/sdX` path maps to under `/dev/disk/by-id`:
   ```sh
   ls -la /dev/disk/by-id/!(*-part*)
   ```
   You will be able to find the right drive based on the filename (starts with the bus it's attached to - `usb` for USB, `ata` for SATA, etc, followed by make and model, and so on) and/or the `/dev/sdX` destination it's referencing. Remember the path, it will be used throughout the rest of the guide.

   This step is optional as the standard `/dev/sdX` identifier can be used throughout this procedure, but it's an additional safety measure to make sure that the wrong wipe is not being wiped by accident.

## Part 2 - ATA Secure Erase
1. Enable security on the drive by configuring the password to `Eins`. For example, given the drive path `/dev/disk/by-id/ata-X`:
   ```sh
   hdparm --user-master u --security-set-pass Eins /dev/disk/by-id/ata-X
   ```
2. Check that security on the drive has been enabled
   ```sh
   hdparm -I /dev/disk/by-id/ata-X | tail
   ```
   The drive should now show as `enabled` instead of `not enabled`.
3. Run the disk erase command:
   ```sh
   time hdparm --user-master u --security-erase Eins /dev/disk/by-id/ata-X
   ```
   Alternatively, if the drive supports ATA Enhanced Erase, run this instead:
   ```sh
   time hdparm --user-master u --security-erase-enhanced Eins /dev/disk/by-id/ata-X
   ```
   The command should exit when the wipe is finished, and print out how long it took.
4. Repeat step 2, but this time check that the security status shows as `not enabled`.

(Source for this section: https://ata.wiki.kernel.org/index.php/ATA_Secure_Erase)

## Part 3 - random + zero erase with nwipe
1. Install nwipe from the USB. You can normally do this by typing `sudo apt install ` into the terminal (note the space at the end), then drag-and-dropping the DEB file onto the terminal window and pressing Enter.
2. Launch `nwipe`, and set it up as below before kicking off the erasure process:

|Setting|Value to use for wiping|
|-------|-----------------------|
|Method|PRNG Stream|
|Rounds|1 with a blanking pass|
|Blanking|Perform a blanking pass|
|PRNG| ISAAC-64 (if available - if it isn't, or if you're wiping on a 32-bit machine, then you may use `ISAAC` instead)|
