[Arch Wiki](https://man.archlinux.org/man/mount.8)

All files accessible in a Unix system are arranged in one big tree, the file hierarchy, rooted at _/_. These files can be spread out over several devices. The **mount** command serves to attach the filesystem found on some device to the big file tree. Only the user that mounted a filesystem can unmount it again.

The standard form of the **mount** command is:

```sh
mount -t type device dir
```

The option **-t** _type_ is optional. Root permissions are necessary to mount a filesystem by default. The previous contents (if any) and owner and mode of _dir_ become invisible, and as long as this filesystem remains mounted, the pathname _dir_ refers to the root of the filesystem on _device_.

If only the directory or the device is given, for example:

```sh
mount /dir
```

then **mount** looks for a mountpoint (and if not found then for a device) in the _/etc/[[fstab]] file.

The same filesystem may be mounted more than once, and in some cases (e.g., network filesystems) the same filesystem may be mounted on the same mountpoint multiple times. The **mount** command does not implement any policy to control this behavior. All behavior is controlled by the kernel and it is usually specific to the filesystem driver. The exception is **--all**, in this case already mounted filesystems are ignored.

# List Mounts

For listing mounts use [[findmnt]].

# Non-superuser Mount

Normally, only the superuser can mount filesystems. However, when _fstab_ contains the **user** option on a line, anybody can mount the corresponding filesystem.

```sh
/dev/cdrom /cd iso9660 ro,user,noauto,unhide
```

If any user should be able to unmount a blk device, then use **users** instead of **user** in the _fstab_ line.

# Bind Mount

Remount part of the file hierarchy somewhere else. The call is:

```sh
mount --bind olddir newdir
```

or by using the fstab entry.
After this call the same contents are accessible in two places.
It is important to understand that "bind" does not create any second-class or special node in the kernel VFS. The "bind" is just another operation to attach a filesystem. There is nowhere stored information that the filesystem has been attached by a "bind" operation. The _olddir_ and _newdir_ are independent and the _olddir_ may be unmounted.

The entire file hierarchy including submounts can be attached a second place by using:

```sh
mount --rbind olddir newdir
```



