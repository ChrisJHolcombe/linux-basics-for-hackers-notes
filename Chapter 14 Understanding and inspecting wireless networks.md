# [[Linux Basics for Hackers Getting Started with Networking, Scripting, and Security in Kali]]

### Understanding Wireless Networks

Wireless networks are crucial for every pentester to understand. If a wireless network becomes compromised, it can have devastating consequences. It's important to note that you should only perform penetration testing on networks you own or have explicit permission to test.

---

### Wireless Network Terminology

- **AP (Access Point)**: The device that broadcasts the Wi-Fi signal.
- **ESSID**: The name of the wireless router.
- **BSSID**: A unique identifier for each AP.
- **SSID**: The service set identifier, or the router name.
- **Channels**: Wi-Fi routers operate on channels from 1 to 11.
- **Power**: Signal strength is measured in negative values. A higher negative number indicates a stronger signal.
- **Security**: The type of security protocol the router is using (e.g., WPA, WPA2).
- **Mode**: The operational mode of the device, which could be managed, master, or monitor.
- **Wireless Range**: In the US, the AP signal limit is 0.5 watts, roughly translating to 300 feet. A high-gain antenna can extend this range significantly.
- **Frequency**: Routers operate on 2.4GHz and 5GHz frequency bands.

---

### Basic Wireless Commands

1. **View Wireless Network Information**:
   ```bash
   ip addr show
   ```
   - This command shows all details about your wireless network cards.

2. **List Available Wi-Fi Networks**:
   ```bash
   nmcli dev wifi
   ```
   - To connect to an AP:
     ```bash
     nmcli dev wifi connect <SSID> password <password>
     ```

---

### Using Aircrack-ng for Wireless Penetration Testing

For wireless recon and cracking, you'll need an antenna that supports monitor mode. Research online for antennas that are suitable, as options frequently change.

1. **Start the Adapter in Monitor Mode**:
   ```bash
   airmon-ng start <interface_name>
   ```
   - Run `airmon-ng check kill` to kill any interfering wireless processes.

2. **Capture Wireless Data**:
   ```bash
   airodump-ng <interface_name>
   ```
   - Note: The interface name might change to include "mon" at the end. Verify using:
     ```bash
     ip addr show
     ```

3. **Target Specific Access Point**:
   ```bash
   airodump-ng -c <channel_of_target_AP> --bssid <BSSID> -w <cap_file_name> <interface_name>
   ```

4. **Deauthenticate Clients**:
   - To deauthenticate everyone:
     ```bash
     aireplay-ng --deauth 100 -a <BSSID> -c ff:ff:ff:ff:ff:ff <interface_name>
     ```

5. **Crack the Captured File**:
   ```bash
   aircrack-ng -w <path_to_wordlist> -b <BSSID> <cap_file_name>
   ```

---

### Bluetooth Scanning and Recon

You can use the `bluez` toolset to scan and sniff Bluetooth devices.

1. **Install Bluez**:
   ```bash
   apt install bluez
   ```

2. **Bluez Tools Overview**:
   - **hciconfig**: Similar to `ifconfig` but for Bluetooth devices.
   - **hcitool**: An inquiry tool that provides device names, IDs, class, and clock information.
   - **hcidump**: Used to sniff Bluetooth traffic.

3. **Scan for Bluetooth Devices**:
   ```bash
   hcitool scan
   ```
   - This will display Bluetooth device MAC addresses, which you can use with `l2ping`.

4. **Inquiry Scan**:
   ```bash
   hcitool inq
   ```

---

### Scanning for Bluetooth Services with `sdptool`

`sdptool` is used to browse and find available Bluetooth services.

**Syntax**:
```bash
sdptool browse <target_mac_address>
```

### Checking Device Reachability with `l2ping`

To check if a Bluetooth device is reachable:
```bash
l2ping <mac_address>
```

---

By mastering these commands and tools, you can effectively analyze and secure your own wireless networks, as well as understand how attackers might attempt to compromise them.
