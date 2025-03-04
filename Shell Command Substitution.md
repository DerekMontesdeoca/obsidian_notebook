Allows the output of a command to replace the command itself. Command substitution occurs when a command is enclose ad follows:

```sh
$(command)
```

Bash perfoms the expainsion by executing the command in a subshell and replacing the command substitution with the output of stdout of the command executed.