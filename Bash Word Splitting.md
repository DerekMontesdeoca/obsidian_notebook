Word splitting in [[bash]] is what controls and determines how bash processes and expands variables and [[Shell Command Substitution]] into separate words. Understanding this is crucial for writing robust scripts and avoiding unexpected behavior. Word splitting is infamous for cause many types of bugs within bash. 

Word splitting occurs when Bash expands a variable or a command substitution and then splits the result into multiple words based on the IFS (Internal Field Separator).

# Internal Field Separator (IFS)

The IFS variable defines which characters  Bash uses for word splitting. By default, IFS contains the following characters:

1. Space `' '` 
2. Tab `'\t'`
3. Newline `'\n'`

The IFS can be set:

```bash
IFS=","
# or
local IFS=","
```

## Reset the IFS

```bash
IFS=$'\t\n '
unset IFS
```

# Supress Word Splitting

Word splitting can be supressed by using double quotes `""` around an element. 

```bash
var="Hello World"

# Splits $var into 2 words.
echo $var

# Preserves $var as a single word.
echo "$var"
```


# Best Practice

Always double quote output of command substitution and variables to avoid word splitting. If splitting is needed, use arrays instead. You can avoid quoting when necessary but make it the exception.

