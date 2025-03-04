sshd is the daemon or service of the ssh server. It allows users to connect to it according to the settings specified in `/etc/ssh/sshd_config`.

# SSHD_CONFIG

The OpenSSH daemon configuration file. 

This is my basic sshd_config file. Note that password authentication must be disabled after using `ssh-copy-id`.

```sshd_config
AcceptEnv LANG LC_*
X11Forwarding no
Port 4242
PermitRootLogin no
PermitEmptyPasswords no
MaxSessions 3
MaxAuthTries 3
PasswordAuthentication yes
PublicKeyAuthentication yes
ClientAliveInterval 60
ClientAliveCountMax 3
UsePam yes
```

[[Pluggable Authentication Modules for Linux|PAM]] is recommended for enhanced security.