Used to install, remove, and manage .deb packages locally. It doesn't resolve dependencies of packages automatically.

```sh
# Install a package.
dpkg -i package.deb
# Remove and installed package.
dpkg -r package
# List installed packages.
dpkg -l
```