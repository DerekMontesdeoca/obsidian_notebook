The `/etc/sudoers` file controls the privileges and access permissions for users using sudo. Because the correct functioning of the sudoers file is so important for the correct functioning of the system, a special command for editing sudoers was created. This command is called `visudo`.

# visudo

In order to correctly edit the sudoers file you need to invoke visudo, which in turn will use the $EDITOR env variable to determine which program to use to edit the file. The visudo command will create a copy of the file and edit that. When you save the file, visudo checks that the file is correct and saves it as the original.

# /etc/sudo.conf

`/etc/sudo.conf` is the file consulted by sudo in order to determine which pulgins to load. If no sudo.conf is found or if it is empty, the sudoers file will be used.

# File Format

The file format is composed of 2 basic types of entries. Aliases (variables) and user specs (rules that say who may run what). The sudoers file grammar is described in EBNF ([[Extended Backus-Naur form]]).

## Aliases (Variables)

Aliases are shortcuts that group multiple items together to simplify permissions.

There are four kinds of aliases

1. User_Alias: Groups users together
2. Runas_Alias: Groups users the command can be run as
3. Host_AliasGruops hosts (useful in network environments)
4. Cmnd_Alias or Cmd_Alias: Groups commands.

### User_Alias (Grouping Users)

Defines groups of users that can be referenced together later. E.g:

```sudoers
User_Alias ADMINS = derek, alice, bob
```

### Runas_Alias

Makes a group of which users a command can be run as (instead of just root). E.g:

```sudoers
Runas_Alias WEBADMINS = www-data, nginx
```

This means users can run commands as www-data or nginx.

### Host_Alias

Groups many hosts together. E.g:

```sudoers
Host_Alias WEBSERVERS = web01, web02, web03
```

### Cmd_Alias

```sudoers
Cmd_Alias RESTART = /bin/systemctl restart nginx, /bin/systemctl restart apache2
```

This allows applying a rule to all commands in RESTART.

## Default Lines

System-wide settings that control sudo's behavior. These setting may be overridden for specific cases. 

```sh
Defaults option=value
Defaults:user option=value
Defaults!command option=value
Defaults:gruop option=value
```

### Common Defaults Directives

- Secure Path: Defines the `PATH` environment variable for sudo commands, preventing users from running malicious executables from unintended locations.
- timestamp_timeout: Defines the cache time for the entered password.
- tty_tickets: Each session and terminal gets its own sudo access and password caching.
- !authenticate: Lets a user or group use sudo without password.
- env_keep: Allows environment variables to be preserved when using sudo.
- logfile: Logs sudo commands to the file.
- requiretty: disables sudo via scripts or remote exploits.
- !root_sudo: disables shell access via sudo (`sudo su` and `sudo -s`).
- reset_env: completely resets most enviroment variable to a safe state. Only a few are kept `HOME`, `TERM`, etc.

## Specs

determines which command a user may run and as what user on specified hosts. By default commands are ru nas root, but that can be changed on a per-command basis.

```sudoers
who where = (as_whom) what

# Additional commands with hosts can be specified to a rule
who where1 = (as_whom1) what1 : where2 = (as_whom2) what2 ...

# Before a command, options, tags and runas can be specified
# Options contian Selinux, date, timeout , chdir and chroot
```