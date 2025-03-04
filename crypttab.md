crypttab (Crypto Table Mapping) is [[fstab]] for crypt. Practically works in the same way. Located at /etc/crypttab, this file specifies which crypt targets to mount automatically. This is meant to be used for fs's that should be decrypted after root has loaded, however, debian uses this files to configure your initramfs, making the process a lot easier and allowing you to specify on this file all the devices you want decrypted. You still need to update you [[initramfs]] and your [[Boot Loader]].

The format is the following:

```
# ============ /etc/crypttab ============ #

# Example crypttab file. Fields are: name, underlying device, passphrase, cryptsetup options.

# Mount /dev/lvm/swap re-encrypting it with a fresh key each reboot
swap	/dev/lvm/swap	/dev/urandom	swap,cipher=aes-xts-plain64,size=256,sector-size=4096

# Mount /dev/lvm/tmp as /dev/mapper/tmp using plain dm-crypt with a random passphrase, making its contents unrecoverable after it is dismounted.
tmp	/dev/lvm/tmp	/dev/urandom	tmp,cipher=aes-xts-plain64,size=256 

# Mount /dev/lvm/home as /dev/mapper/home using LUKS, and prompt for the passphrase at boot time.
home   /dev/lvm/home

# Mount /dev/sdb1 as /dev/mapper/backup using LUKS, with a passphrase stored in a file.
backup /dev/sdb1       /home/alice/backup.key

# Unlock /dev/sdX using the only available TPM, naming it myvolume
myvolume	/dev/sdX	none	tpm2-device=auto

```

I learned that discard option allows for special trim optimizations for SSD's. But discard only allows the optimizations to be allowed to bypass the encryption, if you actually want the optimizations, you need to enable them, e.g. continuous or scheduled TRIM.