A hostname is the name assigned to a device in a network. It is used to identify the machine within that network. It is important to note that this doesn't happen automatically. In order for the hostname to be available to the network, it needs to be broadcasted via dns or mdns or maybe with by sending it when requesting an IP with dhcp. Even if the computer is not broadcasting its hostname to the network, the hostname is still useful because it identifies the computer internally for things such as system messages, logs, and troubleshooting.

# Changing the Hostname

## Configuration File

The most common way to change the hostname of a machine is by changing the configuration file `/etc/hostname`. 

The hostname is stored in memory in the kernel. The information stored in `/etc/hostname` is only read when booting. For that reason you cannot change the hostname instantaneously when editing the configuration file. 

## [[command hostname]]

In order to change the hostname instantaneously, use the command hostname. This only changes the information temporarily until next reboot.

## [[command hostnamectl]]

On systemd services this command can be used to change the hostname permanently and istantaneously.