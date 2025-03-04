Uncomplicated firewall (UFW) is a stateful firewall frotend for iptables. It simplifies firewall rule management. ufw comes by default with debian and ubuntu flavors. It is important to know that ufw acts as a service (Daemon).

# Enable

1. Loads ufw rules from `/etc/ufw` into iptables (or nftables in newer systems).
2. Starts the UFW service on systemd.
3. Ensures that these rules are applied at boot time.

```sh
sudo ufw enable
```
# Status

Shows the status of ufw. You may use verbose or numbered for more output. If ufw is not active, it won't do anything, even if rules are defined.

```sh
sudo ufw status verbose
```

# Disable

Deactivates ufw and stops the ufw service on systemd. Also flushes all the rules from iptables or nftables.

```sh
sudo ufw disable
```

# Reload

Reloads all the rules without the need of disabling and enabling them.

# Default

the `ufw default` command sets the default policy for incoming, outgoing, and forwarded traffic. **This defines the default behavior of the firewall when no specific rule is applied to traffic.**

```sh
sudo ufw default <policy> <direction>
```

- policy: One of allow, deny, or reject.
	The difference between deny and reject is that deny silently drops the packet (no response to the sender, while reject sends a rejection message (useful for debugging).
- direction: One of incoming, outgoing, or routed.
	Routed represents forwarded packages. These packages are sent to a different network. This is not the type of forwarding that happens in NAT.

## Check Current Defaults

You can check current defaults with `sudo ufw status verbose` where you might see

```txt
Default: deny (incoming), allow (outgoing), disabled (routed)
```

That means the following:
- Deny incoming: All incoming packets are denied unless a specific rule allows it.
- Allow outgoing: All outgoing packets are allowed unless a specific rule denies it.
- Disable routed: Packet forwarding is disabled entirely.

## Change Default Policies

This is the most typical case:

```sh
sudo ufw default deny incoming
sudo ufw default allow outgoing
sudo ufw default deny routed
```

# Logging

```sh
sudo ufw logging on | off
sudo ufw logging low | medium | high | full 
```

- low: Logs denied packets only (default logging level).
- medium: low + limited allowed packets.
- high: Logs all allowed and denied packets.
- full: Logs everything in detail (including connection attempts).

## Where are UFW Logs Stored?

UFW logs are written syslog, typically found in main syslog file.

```txt
/var/log/syslog
```

If rsyslog is configured, it may be in a dedicated ufw log file

```sh
sudo tail -f /var/log/ufw.log
```

Kernel logs may store low-level events

```sh
sudo dmesg  grep UFW
```

# Reset

Disables UFW and returns all rules to installation default. You can use --force to  bypass confirmation.

# Rules

## Simple Syntax

```sh
# Basic
sudo ufw allow <port/service>
sudo ufw allow ssh
sudo ufw allow http
sudo ufw allow https
sudo ufw deny http

# Ip Address
sudo ufw allow from 192.168.1.100
sudo ufw deny from 192.168.1.200

# Address + Port 
sudo ufw allow from 192.168.1.100 to any port 22
sudo ufw deny from 192.168.1.200 to any port 80
sudo ufw allow from 192.168.1.0/24 to any port 22

# Ranges
sudo ufw allow 5000:5100/tcp
sudo ufw deny 1000:2000/udp

# Interfaces
sudo ufw allow in on eth0 to any port 22
```

## Full Syntax

```sh
sudo ufw [allow|deny|reject|limit] [in|out] on [interface] \
	proto <protocol> from <source> to <destination> port <port>

# Allow TCP traffic from addr to addr on port 22.
sudo ufw allow proto tcp from 192.168.1.100 to 192.168.1.200 port 22

# Block all UDP traffic from 10.0.0.50
sudo ufw deny proto udp from 10.0.0.50

# Reject http traffic from 192.168.1.0/24
sudo ufw reject proto tcp from 192.168.1.0/24 to any port 80

# Allow incoming traffic for already established and related connections on
# interface eth0, but block all new incoming connections.
sudo ufw allow in on eth0 from any to any state RELATED,ESTABLISHED

```

## Special Rules

Rate limiting.

```sh
sudo ufw limit ssh
```

Allows for 6 connections per 30 seconds per IP before blocking further attempts.