`pwquality.conf` is a file in /etc/security that is part of the libpwquality. It manages the quality of the passwords on Linux accounts. [[Pluggable Authentication Modules for Linux|PAM]] reads this file when changing or creating a new password. 

The file is the format key = value per line and most of the documentation can be found by reading the man page pwquality.conf.

Some of the values in the file refer to "credits". I'm not yet sure of what is the purpose of credits.