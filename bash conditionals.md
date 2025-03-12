conditionals in [[bash]] follow the form:

```bash
if [[ condition ]]; then
	command
fi
```

Different tests can be performed inside the brackets:

- -e: file exists
- -d dir exists
- -f file is regular file and exists
- -x file exists and is executable
- -r file readable
- -w file writable
- -v variable is set
- -z string is zero len
- -n string is not empty
- -b is block special file
-  str == str2
- str != str2
- <> string comparison
- -lt -gt -ge -le -eq for arithmetic comparison
- str ~= regex (ERE)