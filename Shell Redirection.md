Shell redirection is directly related to file descriptors. When you do a shell redirection with `> <`, you are essentially using copying a file descriptor into a file descriptor slot. 

# \> Redirection

Copies the FD to the stdout of the current process.

# < Redirection

Copies the FD to the stdin of the current process.

# &> or &< Redirection

Copies the FD to whatever is in the slot of the number on the right.