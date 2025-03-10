[VBoxManage Manual](https://www.virtualbox.org/manual/ch08.html)<br>
Hypervisor for virtual machines.
#### Commands
- createvm - Create a vm with os type and name
- modifyvm - Assign boot, memory, cpus, resources
- storagectl - Add and remove physical storage controllers.
- storageattach - Attach media to controllers.
- startvm - start vm
- createmedium - Create storage mediums like virtual disks.
- unregistervm - Unregister and delete vm.

### VBox Networking
Networks in Virtual Box machines come as virtual networks that connect the host with the guest. The following configurations are offered:
- Not attached: Represents a network card that is present but has no connection, as if no Ethernet cables was plugged into the card.
- Bridged networking: Creates a bridged connection, making the guest its own member of the network.
- Nat: Network address translation by the host, making the guest unaccessible from the outside but allowing it to communicate from within. The host is also unaccesible by default since it doesn't belong to the local network created by NAT. VirtualBox creates a virtual interface that acts as a router that becomes the middleman between the guest machine and the outside world.
- Nat networking: Same as nat but allows multiple guests to communicate amongst each other and the host.
- Host-only networking: Provides a network only for host and guests.
- Internal networking: Provides a network only for guests.