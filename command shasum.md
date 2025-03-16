shasum implements all algoriths of sha for [[Checksum]].

# Print

```bash
shasum -a 1 myfile
# Output:
# 6923a6e1353f4b6e11d111c2671806d41615a8d9  myfile
```

The output gives you the checksum, followed by the name of the file. This output with this format can be used to check files on [[#Check]]

# Check

```bash
echo "239487293749234729384729347 myfile" | shasum -1 --check
# Output:
# myfile: OK
```
