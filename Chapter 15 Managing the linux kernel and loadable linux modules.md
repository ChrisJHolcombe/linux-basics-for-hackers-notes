# [[Linux Basics for Hackers Getting Started with Networking, Scripting, and Security in Kali]]

### The Kernel: The Central Nervous System of Linux

The kernel is essentially the core component of the operating system, managing system resources and communication between hardware and software.

---

### Checking the Kernel Version

You can check your system's kernel version with:
```bash
uname -a
```

### Viewing and Tuning Kernel Parameters

To view all the system kernel parameters, use:
```bash
sysctl -a | less
```
- Press `q` to exit. Note: A keyboard interrupt (Ctrl + C) will not work here.

### Enabling IP Forwarding

IP forwarding can be enabled to allow your system to forward packets. This is useful for routing and man-in-the-middle attacks.

1. **Edit `sysctl.conf` File**:
   - By default, IP forwarding is disabled: `net.ipv4.ip_forward=0`
   - Change it to `1` to enable:
     ```bash
     net.ipv4.ip_forward=1
     ```

2. **Apply the Change**:
   ```bash
   sysctl -w net.ipv4.ip_forward=1
   ```

### System Hardening

To make your system more difficult to discover, you can ignore all ICMP echo requests (ping requests) by adding this line to your `sysctl.conf` file:
```bash
net.ipv4.icmp_echo_ignore_all = 1
```
- After making the change, update the system settings:
  ```bash
  sudo sysctl -p
  ```

### Listing Kernel Modules

To list all kernel modules currently loaded in your system, use:
```bash
lsmod
```

### Adding and Removing Kernel Modules with `modprobe`

1. **Add a Kernel Module**:
   ```bash
   modprobe -a <module_name>
   ```
   - Replace `<module_name>` with the specific module you want to load.

2. **Remove a Kernel Module**:
   ```bash
   modprobe -r <module_name>
   ```

By understanding and managing kernel parameters and modules, you can fine-tune your system's performance and security, making it better suited for both everyday use and penetration testing.
