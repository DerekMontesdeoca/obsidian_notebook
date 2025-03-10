kernel/system statistics in the [[proc]] system dir.

Common entries define the amount of time, measured in units of USER_HZ 1/100ths of a second on most archs since boot. 

To calculate cpu load, the formula is the following:

```txt
(1 - (free / total_time)) * 100   
```

An awk script to calculate it: 

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
