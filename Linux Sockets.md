A Linux socket is an endpoint for communication between 2 processes. These processes can be on the network or on the same machine.  Sockets on Linux are represented as File Descriptors. Sockets allow for bidirectional communication, unlike pipes that only allow for unidirectional communication. The data is buffered internally by the [[Linux Kernel]] on a send buffer and a receive buffer. Sockets in Linux follow the read/write model. Sockets contain the address and port. 

# How Sockets Work in Linux

Sockets use a domain and type. The domain is the is the protocol that the socket will use, such as ipv4 or ipv6. The type determines the communication protocol like tcp or udp. To create a socket, linux uses the C socket syscall. After that, depending on whether you need the functionality of the server or the client, you use the functions in the socket API. 

On the server side the functions are the following:
1. bind
2. listen
3. accept
4. read
5. write

On the client side, the function are the following:
1. connect
2. send
3. recv
4. read
5. write