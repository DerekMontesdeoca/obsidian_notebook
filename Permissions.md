The permission model in Linux is very straightforward in Linux.  There are 3 groups of permissions: 

1. User
2. Group
3. Others (Everyone)

For each of these groups the following permissions exist:

1. Read
2. Write
3. Execute

These permissions work as you would expect on files, but on directories they have a slightly different meaning.

# Directory Permissions

## Read

Gives you permission to list the file and read the files in a directory (if you also have read permission on said files).

## Write

Gives you permission to modify the contents of a directory, meaning you can add, remove, and edit files (if you have write permission on said file) within it.

## Execute

Execute provides "access" to the directory. It authorizes you to look at extended information on files in the directory (using `ls -l`) and doing `cd` to the directory.  

## Practical Approach

You only need the follwing permission combinations for directories: 

1. rwx - 7: You allow everything.
2. r-x - 5: You can enter the dir and list the contents, but cannot modify it.
3. --- - 0: You have no permissions.

# Special Permissions

There is an additional octal for permissions that controls the SUID, the GSID, and the STICKY bit. 

## SUID

The SUID is a permission that makes whoever executes the file, to have the permissions of the owner of the file. This is useful when you want to give elevated privileges to a user for executing a command, but not allow that user to modify anything themselves. For example, the [[command passwd]] uses the SUID to allow users to change their passwords by giving them execution of the command as root. That allows the modification of the `/etc/passwd` and `/etc/shadow` files that are owned by root, without allowing them to modify those files themselves. The modification is done in a controlled manner by the passwd command (which they cannot modify either). 

## SGID

The SGID has 2 functions. The first one is that it works on files as SUID for groups, i.e., the user that executes the file will get the group permissions of the owner. The second one is that if set on a directory, any files created in the directory will have their group ownership set to that of the directory owner. **This means that any new created file or directory will inherit the group of that dir.**

## Sticky 

Only useful at the directory level, where it makes the contents impossible to be deleted by non-owners or root. 