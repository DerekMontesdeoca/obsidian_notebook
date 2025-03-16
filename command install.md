Install is a command for copying files and setting metadata in one step. It acts like a combination of  these commands:
- cp, mkdir -p
- chmod for [[Permissions]]
- chown
- strip. 

# Examples

```bash
# Basic copy
install mybinary /usr/local/bin

# Set permissions
install -m 755 binary /usr/local/bin

# Create intermediate dir structure
install -D myscript.sh /usr/local/bin/scripts
```