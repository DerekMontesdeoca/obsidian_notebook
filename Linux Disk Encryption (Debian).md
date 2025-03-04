The method I learned to encrypt disks in Linux was using a crypto device mapper, in my case, [[dm-crypt]]. In order to interface with dm-crypt that runs in kernel, you need to use a user-space program. That program is [[cryptsetup]]. Finally the encryption format I used was [[LUKS]].

# Booting with encrypted disks

The main issue with encrypting the system comes with booting. When you boot, the bootloader won't be able to find the root partition because it is encrypted. In order to decrypt it, the initial ram filesystem ([[initramfs]]) needs to load the required programs in order to decrypt the partitions and mount them. In debian this is done automatically when setting up your [[crypttab]], updating your initramfs and updating you [[Boot Loader]]. 

The process to be able to boot with encrypted disks is the following:

1. Have an encrypted partition.
2. Open the encrypted partition.
3. Add the partition to [[crypttab]] by UUID with a mapped name.
4. Add the mapped name to [[fstab]].
5. Update initramfs.
6. Update bootloader.
7. Reboot.