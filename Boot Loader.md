A boot loader is a program that is found by the system BIOS (or UEFI) in the boot sector of your storage device, and which locates and starts your operating system for you. The most used boot loader for Linux is the [[GRUB]]. 

Most boot loaders work on 2 phases.

# Stage 1

The stage 1 boot loader launches when the BIOS executes it from the [[MBR]]. Its main job is to find and execute the [[#Stage 2]]. The main reason for this is that the MBR is only 512 bytes long, making it too small to hold the logic to boot.

# Stage 2

The stage 2 boot loader is in charge of loading the [[initrd]], loading the [[Linux Kernel]] as vmlinuz, which is just the kernel compressed, and executing it with kernel parameters. 

The /boot location is where the stage 2 boot loader is most often located but not always.