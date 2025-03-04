List open files and shows which processes are using them. This command is particularly useful because everything on Linux is a file. This includes:

1. Regular files
2. Directories
3. Block special files
4. character special files
5. Executing text reference 
6. Libraries
7. Stream or network files
	1. Internet socket
	2. NFS
	3. UNIX domain socket

# Common Use Cases

## Finding which process is using a file

When you get a error saying that a file is being used, and thus you cannot modify it or remove it.

```sh
lsof /path/to/file
```

This shows which process has the file open. With that information you can terminate or kill the process and release the file.

## Identifying processes using a specific port

Because [[Linux Sockets]] (network connections) are files that contain the address and port, lsof can filter by address or port to find the sockets that are being used. By using the -i option, you can select the listing of files that match the address. The address will be in the form: 

```txt
[46][protocol][@hostname|hostaddr][:service|port]
```

46 is the ip version and means 4|6.

## Finding files open by a user

```sh
lsof -u username
```

