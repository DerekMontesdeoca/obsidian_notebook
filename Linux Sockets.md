A Linux socket is an abstract representation (handle) for the local endpoint of a [[network]] communication path. Sockets allow for communication between 2 processes. These processes can be on the network or on the same machine.  Sockets on Linux are represented as File Descriptors. Sockets allow for bidirectional communication, unlike pipes that only allow for unidirectional communication. The data is buffered internally by the [[Linux Kernel]] on a send buffer and a receive buffer. Sockets in Linux follow the read/write model. 

# Socket Representation

Full sockets are represented by:
1. Transport layer protocol. I.e., tcp/udp.
2. Source IP
3. Source Port
4. Destination IP
5. Destination Port

A listening socket only has 3 of the 5. When a connection is established, a new socket is created to allow for the current socket to continue listening. 

# Using Sockets

To create a socket, linux uses the C socket syscall. After that, depending on whether you need the functionality of the server or the client, you use the functions in the socket API. 

On the server side the functions are the following:
1. socket: Allocates system resources and creates a new socket, identified by an integer number.
2. bind: Assigns an ip address to a port to enable listening for new connections.
3. listen: The sockets listens for a new connection. 
4. accept: Creates a new full socket with all the information.
5. read
6. write

On the client side, the functions are the following:
1. connect
2. read
3. write