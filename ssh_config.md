```ssh_config
Host myserver
    HostName myserver.example.com  # Actual hostname or IP
    User myuser                    # SSH username
    Port 2222                       # Non-standard SSH port
    IdentityFile ~/.ssh/my_key      # Specific private key
    ForwardX11 yes                  # Enable X11 forwarding
```
