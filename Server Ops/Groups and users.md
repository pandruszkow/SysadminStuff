## Access to hardware

Add the user to the groups according to the table below:

| Group name(s) | Description |
|------------|-------------|
|`kvm`<br> `libvirt`|Virtualisation (KVM, Virt-Manager)|

## Add a user to a group

`gpasswd -a <username> <group name>`

## Initialise a user on Linux

Use `adduser`.

## Force password change on next login for a user

Force user to change password on next login:

```sh
passwd --expire <username>
```

Print information about when the password expires:
```sh
chage -l <username>
```
