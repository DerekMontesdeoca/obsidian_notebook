mknod creates special bock or character special files on linux. The basic structure of the command is the following:

```sh
mknod name type [major minor] 
```

Here, [[Major|major]] and [[Minor|minor]] are device numbers for the [[Linux Kernel]], and type is one of b for  [[block device|block devices]], c for [[Character Special File|character special files]], and p for [[FIFO|FIFOS]].

Mknod is also a function in C and it allows for more options than the ones specified above.