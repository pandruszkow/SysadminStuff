## Access to hardware

Add the user to the groups according to the table below:

| Group name(s) | Description |
|------------|-------------|
|`kvm`<br> `libvirt`|Virtualisation (KVM, Virt-Manager)|



## Initialise a user on Linux

Use `adduser`.

## Force password change on next login for a user

For username `user123`, run the following commands as root or as the target user to:

* Force the password change: `passwd --expire user123`
* Print information about when the password expires: `chage -l user123`
