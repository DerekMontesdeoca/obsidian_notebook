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

# Move Mount

Move a **mounted tree** to another place (atomically). The call is:

```sh
mount --move olddir newdir
```


# Shared Subtree

Since Linux 2.6.15 it is possible to mark a mount and its submounts as shared, private, slave or unbindable. A shared mount provides the ability to create mirrors of that mount such that mounts and unmounts within any of the mirrors propagate to the other mirror. A slave mount receives propagation from its master, but not vice versa. A private mount carries no propagation abilities. An unbindable mount is a private mount which cannot be cloned through a bind operation. 

Supported operations are:
```sh
mount --make-shared mountpoint
mount --make-slave mountpoint
mount --make-private mountpoint
mount --make-unbindable mountpoint
```

The following commands allow one to recursively change the type of all the mounts under a given mountpoint.

```sh
mount --make-rshared mountpoint
mount --make-rslave mountpoint
mount --make-rprivate mountpoint
mount --make-runbindable mountpoint
```

**mount** **does not read** [fstab(5)](https://man.archlinux.org/man/fstab.5.en) when a **--make-*** operation is requested. All necessary information has to be specified on the command line.


# Useful Options

\--bind

\--label
	Mount the partition with the specific label.

-o, --options
	**Last option takes precedence**. See [[#Filesystem-Independent Mount Options]]

 --rbind
	 Like bind but recursive.

-t, --types 

# Filesystem-Independent Mount Options

Some of these options are only useful when they appear in the _/etc/fstab_ file.

async, sync
	All I/O should be done asynchronously or synchronously.

atime
	Update inode access times on the filesystem.

noatime
	This optimizes access time by removing the write required to update access times of inodes in the filesystem.

noauto, auto
	Can o can't be mounted with --all or by fstab.

defaults
	rw,suid,dev,exec,auto,nouser,async

dev, nodev
	Controls whether [[Device Special Files]] will be treated like actual devices.

diratime, nodiratime
	Update or not directory access times.

dirsync
	Does all updates to a directory synchronously.

exec, noexec
	Permit or not execution of binaries and other executable files.

group
	Allow ordinary user to mount the filesystem if one of that user's groups matches the group of the device.

nofail
	Do not report errors for this device if it doesn't exist.

relatime, norelatime
	Access time is only updated (or not) if the previous access time was earlier than or equal to the ccurrent modify or change time.

lazytime, nolazytime
	Only update (or not) times (atime, mtime, ctime) on the in-memory version of the file inode. This significantly reduces writes to the inode table for workloads that perform frequent random writes to preallocated files. 

suid, nosuid
	Honors (or not) suid on files in the filesystem.

silent, loud

owner
	Allow a user to mount a filesystem if it owns it. (implies nosuid and ndev)

remount

ro

rw

user
	Allows a user to mount. (implies nosuid, no exec and nodev)

X-mount.mkdir\[=mode]
	Creates target dir if it doesn't exist.

umask, fmask and dmask 
	sets a mask for permissions that are not present on FAT only. 