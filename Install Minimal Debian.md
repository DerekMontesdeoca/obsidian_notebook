Start by installing a minimal debian using [[debootstrap]] from a live ISO.
1. Configure [[Debian locale]].
2. Adjust time.
3. Install lvm2 cryptsetup parted.
4. Make partitions.
5. LuksFormat main partition.
6. Open main partition.
7. Make PVs and create VGs and LVs.
8. Make filesystems.
9. Create a chroot directory.
10. Mount new partitions to chroot dir.
11. Debootstrap into chroot dir.
12. Copy apt keyrings into chroot dir.
13. Mount system dirs into chroot dir with make-rslave.
14. chroot into chroot dir.
15. apt update and upgrade.
16. Set up hostname.
17. Install, uncomment and generate locale.
18. Generate loopback network interface and default dhcp interface.
19. Create fstab.
20. Create crypttab.
21. Install lvm2, cryptsetup, cryptsetup-initramfs and grub.
22. Install kernel.
23. Update initramfs.
24. Install grub.
25. Update grub.
26. Exit chroot.
27. umount partitions.
28. Reboot.