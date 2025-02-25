ISO's can be modified to include different things. For example, you can modify an ISO image for debian to include scripts or programs required to perform the installation.
1. The ISO image needs to be mounted to the FS on a loopback device /dev/loopX. You can check loopback devices using `losetup`. `mount` should be able to automatically recognize that -o loop is required, but if it doesn't, you may have to specify `mount -o loop`. 
2. Copy the contents to a writable dir, as ISO images are read-only.
3. Modify the contents.
4. Repackage the ISO using `xorriso`. However, specific options required for the command need to be researched further.
A possible workaround for mounting is using `xorriso` on "ossirox" mode, which allows for removing and adding files.<br>
Be aware that some ISO's contain checksums that need to be updated if you modify the ISO.