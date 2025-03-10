Extended globbing in [[bash]] is a [[shopt vs set|shopt]] option that enables the extended syntax for globbing in the shell. 

```bash
!(pattern) # Match anything but the pattern
*(pattern) # Match the pattern 0 or more times
+(pattern) # Match the pattern 1 or more times
?(pattern) # Match the pattern 0 or 1 times.
@(pattern) # Matches one of the given patterns
```
