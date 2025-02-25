A system configuration file on Debian systems. It defines how disk partitions and various other block devices, or remote file systems should be mounted into the file system. 

A simple `/etc/fstab`, using file system UUIDs:

```
# ============ /etc/fstab ============= #

# <device>                               <dir> <type> <options>    <dump> <fsck>
UUID=0a3407de-014b-458b-b5c1-848e92a327a3 /     ext4 defaults                0 1
UUID=CBB6-24F2 /boot vfat defaults,nodev,nosuid,noexec,fmask=0177,dmask=0077 0 2
UUID=f9fe0b69-a280-415d-a03a-a32752370dee none  swap defaults                0 0
UUID=b411dc99-f0a0-4c87-9e05-184977be8539 /home ext4 defaults                0 2
```

Options come from the command [[mount]].