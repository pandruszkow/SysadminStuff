## Enabling the serial console on Ubuntu 20.04 LTS

```sh
sudo systemctl enable serial-getty@ttyS0.service
sudo systemctl start serial-getty@ttyS0.service
```

These two lines will get a serial console going that you can then connect to using `virsh` (if using virt-manager), or some other way if you're using a different hypervisor/VM thingy.

## Colours on the serial console

Search .bashrc for the substring `set a fancy prompt`, and add the following line just before those lines:

```sh
export TERM=xterm-256color
```

Note that this will force a particular type of a terminal everywhere, which may have side effects.
