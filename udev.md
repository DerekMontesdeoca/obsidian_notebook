[ArchWiki](https://wiki.archlinux.org/title/Udev)<br>
udev is the Linux device manager responsible for dynamic device detection and management. It runs in user space and interacts with the kernel's device events, processing them asynchronously.
- Belongs to the systemd family and only works with systemd.
- Creates device nodes dynamically in /dev.
- Uses and applies naming rules for devices.
- Triggers scripts or actions when devices are pluggeed in or removed.
- Provides persistent naming for devices based on UUID.

#### Device Connection Flow
1. Kernel detects a device and triggers a new event.
2. udev daemon (udevd) receives the event and matches it to rules in /etc/udev/rules.d/
3. udev applies rules like:
    - Create device in /dev
    - Set permissions.
    - Create symlinks.
    - Execute scripts.
4. Device is available for use.