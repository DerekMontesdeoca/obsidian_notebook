Initrd is born from the need of booting Linux. Traditionally it was done by the [[Linux Kernel]],  but certain requirements made this approach impractical. For example:

1. The requirement of userspace programs to complete the boot process, created a chicken and egg problem that is solved with 2 phase booting system, e.g. [[LUKS]] or [[LVM]].
2. The need for different possible configurations of the kernel due to different machines requiring different drivers and modules. Statically compiling these modules into the kernel creates many problems for different kinds of computers it could be used for. Initrd solves this by loading specific modules required to boot into the kernel.
3. The need for [[Hibernation|hibernation]]. Initrd gives the kernel access to the disks and  filesystems, allowing it to load memory back from hibernation status.

Initrd was then created to allow the [[Linux Boot Process]] to occur in 2 phases. The first phase, loading the initial ram disk, which in turn provides a user-space filesystem capable of executing the 2nd phase, which is the rest of the booting process. All required user-space modules and kernel modules are included here in order to execute the 2nd phase of the boot process.

A more modern version of the initrd is [[initramfs]]. 

