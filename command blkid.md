Prints [[block device|block devices]] with id's and attributes.

```bash
# Select
blkid /dev/sda1
# Output options
blkid --output|-o value|key /dev/sdb2
# Filter what to output
blkid --match-tag|-s UUID /dev/sdb2
```
