Used to set and display the [[hostname]] of the linux machine. 

Hostname, when invoked without any arguments, will display the current hostname as displayed by the gethostname c function.

To set the hostname, you invoke it with 1 argument or with --file option, the command sets the hostname with sethostname c function.

This command is only effective until next reboot. To change the hostname permanently, edit the `/etc/hostname`.