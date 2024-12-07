# [[Linux Basics for Hackers Getting Started with Networking, Scripting, and Security in Kali]]

### Network Configuration: The `ifconfig` Replacement

The book mentions the use of the `ifconfig` command for network configuration, but it has been deprecated. The updated command to use is `ip`, which provides all of the network information for your computer.

### Using the `ip` Command

- **ip addr show**: Displays detailed information about your network interfaces, including adapter names, MAC addresses, and whether the interface is up or down. It is more comprehensive than the old `ifconfig` command.
- **Example**: 
  ```bash
  $ ip addr show
  ```
  This command will give you all the necessary details about your network devices.

### MAC Address Changes

The book describes changing your MAC address manually. However, I prefer using `macchanger`, as it simplifies the process and achieves the same result efficiently.

### Using `macchanger`

**macchanger** is a tool that allows you to easily change your MAC address. Here is the help output for `macchanger`:

```bash
$ macchanger --help
GNU MAC Changer
Usage: macchanger [options] device

  -h,  --help                   Print this help
  -V,  --version                Print version and exit
  -s,  --show                   Print the MAC address and exit
  -e,  --ending                 Don't change the vendor bytes
  -a,  --another                Set random vendor MAC of the same kind
  -A                            Set random vendor MAC of any kind
  -p,  --permanent              Reset to original, permanent hardware MAC
  -r,  --random                 Set fully random MAC
  -l,  --list[=keyword]         Print known vendors
  -b,  --bia                    Pretend to be a burned-in address
  -m,  --mac=XX:XX:XX:XX:XX:XX
       --mac XX:XX:XX:XX:XX:XX  Set the MAC XX:XX:XX:XX:XX:XX
```

**Example**:
To change your MAC address to a random one, you can use:
```bash
$ sudo macchanger -r <network_interface>
```

For more information or to report issues, visit: [macchanger GitHub page](https://github.com/alobbs/macchanger/issues)

### The `dig` Command

The `dig` command is used for querying DNS servers. You can use it to gather information about a domain.

- **Basic Syntax**: 
  ```bash
  $ dig <domain>
  ```
  This will output useful information about the domain, including IP addresses and other DNS records.

### Specifying DNS Services

You can specify different types of DNS records by adding options after the domain:
- **Mail Exchange (MX)**: 
  ```bash
  $ dig <domain> mx
  ```
- **Name Server (NS)**:
  ```bash
  $ dig <domain> ns
  ```

These options allow you to focus your queries and retrieve specific information relevant to your target