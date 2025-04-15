Advanced file copying. Usually used for syncing directories on same host or over a network. 

# Useful Options

- -z Compress copied data.
- -v Verbose: Shows everything that is being copied. Helps notice errors.
- -a Archive mode: Preserves symbolic links, devices, attributes, permissions, ownerships.
- -u Update: skips files that are newer on the receiver.
- --delete-after: Deletes files on dest that don't exist on src. After means that if the xfer fails, files are not deleted.
- --checksum -c: Checksums: Use checksums instead of modtime.
- --relative -R: Allows for copying with relative paths. Example:

```bash
# Creates /baz/bar
rsync /foo/bar /baz
# Creates /baz/foo/bar
rsync -R /foo/bar /baz 
# Creates /bar/baz/bar/baz
rsync -R /foo/./bar/baz /bar/baz
```