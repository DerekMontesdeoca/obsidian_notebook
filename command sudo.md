Sudo allows a user to execute a command as another user or superuser. Sudo means superuser do. Many systems utilize sudo to allow regular users to execute some commands with elevated privileges. 

Using sudo instead of becoming root, has many advantages. Elevated privileges can be given to users with more fine grain than just allowing them to do anything. Also, sudo logs successful and failed attempts to gain elevated privileges. Some systems even deactivate root completely, in favor of allowing users to only use sudo. In these systems, superuser can still be accessed via sudo su. Using sudo as the only way to gain elevated privileges does require additional considerations for system administrators. 

Sudo will change behavior according to the policies configured by the sysadmin. These policies are usually configured in the [[/etc/sudoers]] file.  They will determine what privileges are given to the user when sudo is invoked. According to the documentation, additional plugins can be configured to extend the functionality of sudo. 

Sudo allows caching of the user password and this caching can be refreshed without the need to execute any command by using sudo -v. 