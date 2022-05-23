## Sorting by

* Normal sort order: `sort`
* "Human" file sizes: `sort -h` - this can sort file sizes like `4K`, `9G` and so on
* Natural numbers: `sort -n` - so that `9` comes before `12`, rather than the other way round (because normally it's sorted digit-by-digit, not as a whole number
* **Version numbers**: `sort -V` - normally sort breaks on dots, it seems. This can correctly sort a line of text that e. g. contains a kernel version or a package version
* Reverse sort: `sort -r` - reverse the sort order of whichever 

## Other - sort unique
`sort -u`

Replaces `sort | uniq`.

## Other (extremely useful technique) - sort by field

Given the following input (an example `/etc/fstab`):

```
/dev/sda1 / ext4 defaults 0 0
/dev/sda3 /data2 ext4 defaults 0 0
/dev/sda2 /data1 ext4 defaults 0 0
```

You may sort by the second field (the mount point) using the `sort -k 2,2` option. For the third field, that's `sort -k 3,3`, and so on. Any whitespace is treated as a field separator.
