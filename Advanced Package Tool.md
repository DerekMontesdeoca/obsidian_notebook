Apt is the tool used to manage packages in Debian and Debian-based Linux distros. There are 2 flavors of apt. There is the apt command, which is more intuitive and friendly but is not stable for scripting, since it doesn't always produce the same output. The other flavor are the apt-get apt-cache set of tools that are stable for scripting but are not as friendly. There is an additional package managing tool (aptitude) which uses ncurses and is useful for interactive package management.

Since apt-get and apt-cache are useful for every situation, I will focus on learning those first. 

# Upgrading

```sh
apt-get update
apt-get upgrade -y

```

# Installing

```sh
# Install the package
apt-get install --yes package-name
```

# Remove

```sh
apt-get remove package

# This will remove the package and its unused dependencies.
apt-get autoremove package
```

# Search and List

```sh
# Search a package.
apt-cache search package

# Show detailed package info.
apt-cache show package

# Show installed and available versions of packages.
apt-cache policy package

# List deps of package.
apt-cache depends package
```