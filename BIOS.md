The basic input and output system (BIOS), is the first program executed when [[Linux Boot Process|booting a computer]]. It has the following responsiblities: 

1. Loading basic I/O, usually just keyboard and a terminal screen.
2. Performing the Power On Self Test (POST) that checks hardware integrity. 
3. Detects and enumerates devices such as storage devices, RAM, and peripherals.
4. Select the device from which to boot.
5. Finds the [[Boot Loader]] from the [[MBR]].
6. Hands over control to the boot loader.

The BIOS is a 16-bit [[Real-mode Program|real-mode program]].