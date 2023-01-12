# Tandberg LTO-4 HH (Half-Height) tape drive

## Summary

Tandberg LTO-4 HH drive is a SAS-attached LTO-4 drive. My best guess is that it's an OEM rebranded version of the HP StorageWorks LTO-4 Ultrium 1760 (aka HPE StoreEver LTO-4 Ultrium 1760), based on the fact that they both respond to the HP LT&T diagnostic tool, and the fact that they have nearly identical faceplates.

## Feature support

### Emergency eject

Hold down Eject for a few seconds and tape should eject just fine

### OBDR

Apparently supported. According to the HP manual, firmware will support OBDR if the output of a SCSI INQUIRY command has the string `$DR-10` at byte offset 43. My particular device identifies itself as having firmware revision `U529/OEM` in HP LT&T.

