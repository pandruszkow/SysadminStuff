# chmod

## Symbolic file permissions

This is what you see in the beginning of each line when viewing a directory through `ls -l`:
```
-rwxr-xr-x 1 ubuntu ubuntu 807 Feb 25  2020 /home/ubuntu/.profile
```

The anatomy of the permission field is as follows (there are three spaces added between each character for ease of markup in ASCII art):
```
-   r   w   x   r   -   x   r   -   x
^   \_______/   \_______/   \_______/
|       ^           ^           ^
|       |           |           |
|       |       +---+           |
|       |       |               |
|       |       |      +--------+
|       |       |      |
|       |       |      +---- the 'other' triad - read, write, execute bits that apply to everyone else
|       |       |
|       |       +---- the group triad - read, write, execute bits that apply to the group that owns the file
|       |
|       +---- the user triad - read bit, write bit, execute bit that apply to the file owner
|
+------- directory bit - set to `d` if the listed item is a directory

```

Each bit is referred to using letters `r`, `w` and `x`.

To change each triad's value, specify the letter for the triad, then whether you want to add/subtract flags from the existing value, or set the whole triad in one go. `u`=user(owner), `g`=group, `o`=other (**NOT** owner), `a`=every triad at once.

### Examples

#### Simple examples

- Give owner execute permission: `chmod u+x file`
- Set permissions to read and write only, at group level: `chmod g=rw file`. If the group had execute permission before, it's now removed because this combo makes the new permissions exactly equal to `rw` - meaning if either `r` or `w` bit is disabled, it becomes enabled; and if any bit outside of `r` and `w` is enabled, it becomes disabled.
- Take away write permission for other users (not owner and not group): `chmod o-w file`
- Take away everyones execute permission: `chmod a-x file`

#### Combo examples

You can set permissions for multiple triads at once. Simply write out what you wish to do for each triad as above, separating each item with a `,`. Triads can be grouped into one item too: to operate on `u`ser and `g`group at once, write it out as `ug..`.

- Give owner execute permission, set group and other to read-write: `chmod u+x,g=rw,o=rw`
  - With the group and other triads combined (but with the same result): `chmod u+x,go=rw`

#### Special permissions:

- Sticky/SUID (setuid)/setgid bit: todo (see blog post at https://dougvitale.wordpress.com/2013/02/16/linux-file-permissions-and-chmod/)
- e`X`ecute but only for directories: `chmod a+X -R directory`
  - this comes in handy when rescuing directories that were clobbered with a bad `chmod` command. Upper-case `X` will set the execute bit only on directories but leave it as-is on files, unlike lower-case `x` that will give an execute bit to everything (which is rarely the desirable outcome).
