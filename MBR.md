The master boot record (MBR) is the very first sector of a bootable disk (512 bytes).
It contains the [[Boot Loader|boot loader]] code (446 bytes), the partition table(64 bytes), and the boot signature (boot flag) (2 bytes). 

The MBR support 4 primary partitions but extended partitions allow for more, by giving it a small partition table that allows for logical partitions inside. 

The MBR is limited to 2 TiB disks due to 32-bit [[Logical Block Addressing|LBA]] addressing. 
2^32 == 4294967296 addresses X 512 bytes per sector  == 2TiB .