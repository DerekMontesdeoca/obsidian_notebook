Both are used in [[bash]] to change options. The main difference between both is that shopt controls options for interactive use, while set modifies options scripting and error handling (mostly).
# shopt

```bash
# List all available option and their states
shopt

# Show only enable options
shopt -s

# Enable an option
shopt -s autocd

# Disable an option
shopt -u histappend
```

# set

```bash
# 
```