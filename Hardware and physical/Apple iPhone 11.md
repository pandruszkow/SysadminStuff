# Apple iPhone 11

## Hardware features

### Back-of-device tap gestures

Do not work reliably in my experience. Pull-down menu shortcut buttons work more reliably, though more cumbersome.

## Quality of life

### Remote file access
There are free WebDAV/SFTP servers which can be downloaded from the App Store and run in foreground to shuttle files across wirelessly without using iCloud.

### Content-based Camera Roll search
This can work with keywords that are entity types ("cat", "lake") or OCR'ed text fragments. The latter is more reliable - I am unsure of which entity-based keywords are actually available, and the feature is quite basic. OCR is quite good.

### Shortcuts

Make sure to install the app and explore the features. Location-based triggers are particularly powerful if the phone needs to act in a location-specific way.

There is no way to run a shortcut periodically. The only, cumbersome, way is to set up automations at fixed times throughout the day at 5 minute intervals, or something similar. This results in 24 * (60 / 5) = 288 time-based automation entries total. This is challenging to manage for obvious reasons.

Notably, Shortcuts can parse JSON data and make HTTP(S) requests. This opens the door to some direct interaction with servers, which does not involve PWAs or web-based clients.

Community/third-party shortcuts are available. Some of them, quite complex and elaborate. There is also `/r/shortcuts`, which is quite useful.

### Shortcuts - "Convert to PNG"

Certain iOS apps struggle to deal with `.webm` input. To accommodate them, a simple shortcut can be built to convert the file passed in as input into a PNG. The resulting PNG can then be read by the target app.

The shortcut (like any other shortcut that acts on a file) can be added to the file actions menu, and triggered from the gallery or file browser.

### Content filters in browser (tracking etc.)
Adguard is quite useful and free in its basic form. Some other filtering solutions exist, but I haven't investigated them.

## Local AI

No first-party Apple AI as of last update to this section.

Works using third-party inference apps. LLM Farm and [Cactus](https://github.com/cactus-compute/cactus) work quite well. The latter has no obvious bugs, but has a limited model selection and inference configuration.

Only smaller models will work quickly. Expect to fit nothing larger than 3B in memory, with quantisation.

## Backing up

Backups can be performed in one of two ways:

* using iTunes
* using libimobiledevice

### Using iTunes
**[Warn: Instructions incomplete, unchecked. Requires validation on live software.]**

If running on Linux, a Windows VM or dual boot will be required. Currently, I've seen issues getting the trust relationship (pairing) the iPhone with virtualised Windows 10 despite setting up USB pass-through. Cause unknown. TODO: Troubleshoot this at some point.

1. Pair iPhone to computer.
  - Install iTunes
  - Plug in via Lightning to USB port
  - Choose "Trust" on the modal dialog that shows on the iPhone
2. Run device backup from iTunes (click the rectangular smartphone icon in the upper-right hand corner on one of the top toolbars.
3. When asked whether to enable encryption, enable. **RECORD THE PASSPHRASE IMMEDIATELY.**
  - Encryption enabled means that secrets (passwords, etc.) get backed up too. Disabling encryption means re-enrolling every app again manually.
  - **FORGOTTEN PASSPHRASE RESULTS IN DATA LOSS.** This is strong encryption, not obfuscation. There is no way to open without the password entered at backup time.
4. Wait for backup to complete. Validate using iTunes-Backup-Explorer (see `Validating backups` section).

### Using libimobiledevice (Linux-native)

1. Navigate to official project website at https://libimobiledevice.org/.
2. Download and install the latest version.
3. Verify that command `idevicebackup2` is now available on the system.
4. Create backup directory if not present (alter path according to preference):
   ```
   mkdir -p "~/Documents/iPhone backup from $(date -I)"
   ```
5. ```
   idevicebackup2 -i --full --debug backup "~/Documents/iPhone backup from $(date -I)"
   ```
6. When asked whether to enable encryption, enable. **RECORD THE PASSPHRASE IMMEDIATELY.**
  - Encryption enabled means that secrets (passwords, etc.) get backed up too. Disabling encryption means re-enrolling every app again manually.
  - **FORGOTTEN PASSPHRASE RESULTS IN DATA LOSS.** This is strong encryption, not obfuscation. There is no way to open without the password entered at backup time.
7. Wait for backup to complete. Validate using iTunes-Backup-Explorer (see `Validating backups` section).

*[Note: `idevicebackup2 info` and `idevicebackup2 list` do not work (see https://github.com/libimobiledevice/libimobiledevice/issues/607). This means the use of an external iTunes backup reader utility is required to validate the data.]*

### Validating backups

1. Download and install iTunes-Backup-Explorer from https://github.com/MaxiHuHe04/iTunes-Backup-Explorer.
2. Using menu option `File` -> `Open backup...`, point to the `Manifest.db` file in the root directory of the backup.
3. If the backup is encrypted (which it should be, according to these instructions), enter passphrase.
4. Once decrypted and loaded, navigate to check that the important parts of the backup are present (browser bookmarks, Camera Roll, etc.)
