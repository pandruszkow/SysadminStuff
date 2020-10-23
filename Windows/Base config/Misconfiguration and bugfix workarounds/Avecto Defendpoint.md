VirtualBox does not start
==========
Avecto will try to overwrite pieces of the VirtualBox binary, in-memory, after you start it. The problem is, VirtualBox is hardened since version 4 or 5, and it's having none of it. Launching a VM will fail with a VBox hardening error.

To solve this, ensure your VirtualBox binary is whitelisted for non-modification from Avecto config keys in the registry. If that doesn't work, try pressing the Start VM button several times in a row until the machine actually starts up without showing the error message (think starting an old lawnmower or an old car). If that still doesn't work, try to start VirtualBox using the fake "admin prompt".

Total time spent troubleshooting: up to 10 hours, maybe more.
