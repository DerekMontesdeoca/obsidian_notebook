Bourne Again Shell is the upgraded version of the (in)famous sh (Bourne Shell). It is the default shell in many Linux distributions and allows for a lot more syntax options than sh. Notably you can use arrays and better globbing in bash. 

# Configuration Files

The main configuration files:

- .bashrc
- .profile

The main thing to remember about these is that profile runs on login shells (basically when logging in), and bashrc runs everywhere else. 

On Bashrc you should place your aliases functions and interactive configs. On profile you should set your environment variables. 

## Why set env variables in .profile?

Env variables should be set on .profile for the following reasons:

1. It is executed once. 
2. All shells will inherit the env  set by the profile, ensuring consistency across all shells, interactive and non-interactive.