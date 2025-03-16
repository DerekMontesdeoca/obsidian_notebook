Tar is an archiving utility capable of creating and extracting [[Archive Files]]. The name comes from Tape Archiver from the era of tape storage units.

The main commands used with tar are creating and extracting archives.

# Extraction

Not only can you extract a dir structure. You can extract a dir structure into your own dir structure and tar will add files to the corresponding dirs and create the ones that don't exist.

```bash
# The flag for extraction is -x.
# The flag to specify the archive on which to perform extraction is -f <path>.
# Optionally, gunzip compression may be specified with the -z flag.
# The -C option can be specified to select a dir to extract the files to.
tar xzf my_archive.tar.xz 
```

# Creation

```bash
# The flag for creation is -c.
# The flag to specify the archive is -f <path>.
# Optionally, gunzip compression may be specified with the -z flag.
tar czf my_archive.tar.gz file1 file2 file3
```

# Some Compression Options

```bash
# -j for bzip2
# -J or --xz
# -I (insert here compression program with options)
```