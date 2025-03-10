Users and gruops are used to control access to the system's files, directories, and peripherals.

# Users

Anyone who uses the system may be a user as long as they set a unique name. Some names are reserved for the system, e.g.  root. 

Users can be retrieved from the [[/etc/passwd]] file, they can be queried individually with the [[command id]] and listed with [[command getent]].
# Groups

Groups make it easy to give [[Permissions|permissions]] to multiple users at the same time. 

## Shared Access

For example, when multiple users need to work in a common project, a group can be created, the users can then be added to such group, and the project can be assigned to the group with permissions that allow access to it. 

## Giving Permissions to Multiple Users

Groups can also be used to give special permissions to certain users. A group can specify the special permissions of the users and then users can be added to the group. That way is a lot more effective than manually specifying access to each user. 

## Group Manipulation in Linux

Groups can be listed by reading the `/etc/group` file. Groups for a user can be retrieved by using the [[command groups]] and the [[command id]], and individual groups can be queried using the [[comand getent]].

# UPG

In most Linux distros, when a new user is created, a group with the same name as the user is also created by default. This is known as the **User Private Group** (UPG) scheme. This makes it easier to actually use groups for [[#Shared Access]]. With UPG default permissions for groups can be a lot more lax because files belong the the private group by default. If no private group existed (as it used to be), default group permissions would have to be very strict to avoid security issues. With the UPG, shared directories with the [[Permissions#SGID|SGID]] set can be used to make sure that new files and directories within it inherit the Group setting of the parent. 