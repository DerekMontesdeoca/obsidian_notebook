
**cryptsetup** is what you use to interface with [[dm-crypt]] as it runs on user-space.
The main use for these commands is encrypting disks and partitions. Basic commands for using cryptsetup with [[LUKS]] for encrypting a partition are the following:

```sh
# Format a new partition with LUKS. You can provide a passphrase or a key.
cryptsetup luksFormat /dev/sda5

# Decrypt a partition with LUKS. The partition will be mapped to 
# /dev/mapper/sda5_crypt
cryptsetup open --type LUKS /dev/sda5 sda5_crypt

cryptsetup close /dev/mapper/sda5_crypt

# Ask if a partition has a LUKS header.
cryptsetup isLuks /dev/sda5
```

** If you want to close a luks partition that has [[LVM]] on it, make sure to deactivate the volume groups from the partition to avoid it telling you the partition is busy.

If you are using LVM you can have LVM on LUKS or LUKS on LVM. They both have their trade-offs and caveats.
