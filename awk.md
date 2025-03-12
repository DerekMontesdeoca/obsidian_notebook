AWK is general programming language based on text manipulation and processing. It is best used for manipulating text of a medium scale. If large scale manipulation is required, [[perl]] may be a better choice. For small scale text manipulationm, awk ran as a command from shell is usually the best choice. Even though most options can be specified via flags on the awk command, in a big program, using the syntax based options is better. 

# Syntax

This is an example program to calculate CPU load on 1s sample.

```awk
BEGIN {
    prev_total = 0
    prev_idle = 0
    for (i = 0; i < 2; i++) {
        if (i != 0) {
            system("sleep 1")
            prev_total = total
            prev_idle = idle
        }
        getline < "/proc/stat"
        close("/proc/stat")
        total = 0
        for (j = 2; j <= NF; j++)
            total += $j
        idle = $5
    }
    printf "%.1f %%\n", (1 - (idle - prev_idle) / (total - prev_total)) * 100
}
```

## Built-in Variables

- $0: prints all fields in a record.
- FS: Input field separator, -F in command line.
- OFS: Output field separator.
- NF: Number of fields.
- NR: Number of records.
- RS: Record separator variable (input).
- ORS: Output record separator.
- FILENAME: current filename variable.

## Initialization
In awk variables that are uninitialized, are treated as zero values, e.g. integers are treated as 0 and you can safely do `++myvar` without need to specify `myvar = 0` before.

## Arrays and Associative Arrays

```awk
arr[i]
name = "Peter"
++dict[name]
```

## File Output

You can do file output doing `>` to write and `>>` to append.

## Flow Control

You can exit from a script by using the `exit` command. You can also skip the current record by using the `next` statement.

## Functions

```awk
function error ( message ) {
    if (FILENAME != "-") {
        printf("%s: ", FILENAME) > "/dev/tty";
    }
    printf("line # %d, %s, line: %s\n", NR, message, $0) >> "/dev/tty";
}
```

system is usefule for side-effects.
getline is useful to get data from the outside world. getline will execute only once unless you close it. Even when using commands! Do close("my command").
## Patterns

Patterns are conditions that when met, execute blocks of code.

- BEGIN: Represent when NR == 0
- END: Represent when NR == last record
- comma separated condition specify when to start executing (turn on execution) and when to stop execution (turn off execution).
