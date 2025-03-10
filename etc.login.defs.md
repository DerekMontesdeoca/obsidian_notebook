`/etc/login.defs` is a configuration file in Linux that handles various settings related to account management, user authentication, passwords, and login. It is used by utilities like [[command passwd]], [[command login]], groupadd, usermod, etc.

Changes to this file affect only new users, as this files handles defaults for new users only.

Some settings defined in this file are overridden by [[Pluggable Authentication Modules for Linux|PAM]]. 

# Important Parameters

## Password Policies

- PASS_MAX_DAYS
- PASS_MIN_DAYS
- PASS_WARN_AGE
- ENCRYPT_METHOD

## User Account Defaults

- UID_MIN / UID_MAX: Range of UIDs for regular user accounts.
- GID_MIN / GID_MAX: Range of GIDs for regular groups.
- USERGROUPS_ENAB: yes or no, whether to create groups for users.
- CREATE_HOME: Whether useradd should create a home ddirectory for a user by default.

## Security Settings

- UMASK: Default file permissions mask for newly created files.
- FAILLOG_ENAB: Whether to enable logging of failed login attempts.
- LOG_UNKFAIL_ENAB: Logs unkown users failed login attempts. 