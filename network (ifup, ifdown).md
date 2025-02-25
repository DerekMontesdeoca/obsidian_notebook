Manages basic networking and comes default with most linux configurations, although most distros prefer using networkd (systemd) or network manager (nmcli).
#### Loopback
```
auto lo
iface lo inet loopback
```
- auto - The device should be mounted on boot.
- inet - IPv4 protocol.
- loopback - Specifies loopback device. Loopback devices allow a machine to communicate with itself in a safe way without having to go through the physical hardware interface. Typically set to 127.0.0.1 or localhost.

#### dhcp
```
auto $interface_name
iface $interface_name inet dhcp
```
- dhcp - Queries the dhcp server for an ip.