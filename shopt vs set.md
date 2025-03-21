Both are used in [[bash]] to change options. The main difference between both is that shopt controls options for bash specific shell options, while set modifies options scripting and error handling (mostly) on "[[POSIX]]" shells.
# shopt

```bash
# List all available option and their states
shopt

# Show only enabled options
shopt -s

# Enable an option
shopt -s autocd

# Disable an option
shopt -u histappend
```

# set

```bash
# Debug script
set -x 
# Make pipe commands fail.
set -o pipefail
```