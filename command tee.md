Use it to redirect or append to multiple fds at the same time and stdout.

```bash
echo "something" | tee /dev/fd/3 /dev/fd/4 file1.txt > /dev/null
```