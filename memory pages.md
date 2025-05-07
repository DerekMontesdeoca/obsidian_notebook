Memory pages are blocks of memory that act as units for various features implemented by the OS. Among these features, the most notable is [[virtual memory]]. Additional to that, swapping and memory protection also make use of pages.

Pages can be shared by many processes with virtual memory. 

# Huge pages

Pages usually have a default size that should work for everyday use, usually 4kiB. In the case that you need bigger pages and they are supported, huge pages can be used, which are anything from 2MiB to 1GiB.
# Get PageSize

PageSize can be obtained via getconf or by directly reading kernel filesystem.

```bash
getconf PAGESIZE
```

# Page Types

## Anonymous Pages

- Not backed by a file.
- Created by stack usage, malloc or mmap with `MAP_ANONYMOUS`.
- Swappable

## File-Backed Pages

- Created by mmap() on a file.
- Backed by the file itself.
- Create a mapping between a file and memory.

## Shared Pages

- Created by mmap() with `MAP_SHARED`
- Shared between processes (IPC)
- Can be backed by a file.

## COW Pages

- Created by fork() or mmap() with `MAP_PRIVATE`
- Shared initially and duplicated when written.
- Allow memory sharing until modification.
- Like a lazy copy.

## Zero Pages

- Page filled with zeros, shared until written to.
- Used for freshly allocated memory.
- Backed by a special "zero page" in the kernel.

### Page Cache Pages

- Act as caches for disk access.

## Kernel Pages

- Only accesible to the kernel.
- 