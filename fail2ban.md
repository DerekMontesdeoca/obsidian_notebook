Fail2ban is an intrusion prevention software framework. Works by monitoring logfiles for selected entries and running scripts based on them. Usually, it works by banning ip addresses that belong to hosts trying to breach the system's security. 

Among the actions that fail2ban can execute when an abusive IP address is detected are:
- Update [[Firewall]] rules.
- Send email notifications.
- Any user-defined action that can be programmed into a Python script.

# Filters

Filters are responsible for determining which records should count as offending.

The configuration ships with premade filters, including:
- Apache
- [[Lighttpd]]
- [[sshd]]

Filters are defined by Python regexes and go in `/etc/fail2ban/filter.d/*.conf`.

# Actions

Actions define what happens when an agressor is found, e.g. ufw deny. Actions are defined in `/etc/fail2ban/action.d/*.conf`

Variables are defined in `[Definition]` and they are mandatory, unlessed given a default in the `[Init]` section.

# Jails

A jail is the combination of a filter and an action.  You can pass a parameter to a filter or an action from a Jail by invoking it like so:

```jail.local
[sshd]
action = ufw[ip="192.168.1.1"]
```


