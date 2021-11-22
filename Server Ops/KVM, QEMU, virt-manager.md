# Shared directories

virt-manager supports VirtualBox-like shared directories using the [9p file sharing protocol](https://en.wikipedia.org/wiki/9P_(protocol)).

The documentation online doesn't list all the moving parts that have to be aligned just right in one article, so these notes attempt to synthesise all of this info in one place.

## Set up a shared dir in virt-manager

Open the VM configuration, click `Add Hardware`, select `Filesystem`, and fill in the config as below:

- **Driver:** Path

- **Mode:** Squash

- **Write policy:** Immediate

- **Source path:** any existing directory on your host machine that you want to share between the host and the guest. You shouldn't choose a directory that's already in use (such as the home directory or `/tmp`), because file permissions and ownership could be clobbered.

- **Target path:** anything that looks like a full Unix path. **This is just a HANDLE, not a PATH. Think of it as the share name in VirtualBox.** It won't be the actual mount path inside the guest VM, it's only for the guest to tell the hypervisor which share it's mounting.

If you wish, tick the option to expose this directory as read-only.

*Do not select anything different for the first three options!* It will not work, or you will get mysterious permissions-related failures.

Finally: change owner and group of the directory you chose as the `Source path` to `libvirt-qemu` (or equivalent - whichever group you had to add yourself to so that you could create and launch VMs).
**THIS IS IMPORTANT.** You **WILL** get mysterious permission-related errors unless you make sure to do so. 
