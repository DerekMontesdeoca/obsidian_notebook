[ArchWiki](https://wiki.archlinux.org/title/Dm-crypt/System_configuration)

**dm-crypt** is the linux kernel's device mapper crypto target. Device mapper is infrastructure in the Linux kernel that provide a generic way to create virtual layers of block devices. Writes to this device will be encrypted  and read decrypted. dm-crypt works at the kernel level, translating on the fly.