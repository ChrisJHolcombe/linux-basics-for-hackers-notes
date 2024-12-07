# [[Linux Basics for Hackers Getting Started with Networking, Scripting, and Security in Kali]]

### Staying Anonymous on the Internet

While everything on the internet is tracked, there are ways to maintain anonymity. Here are the main topics for achieving this:

1. **The Onion Network (Tor)**
2. **Proxy Servers**
3. **VPNs (Virtual Private Networks)**
4. **Private Encrypted Email**

---

### The Onion Network (Tor)

The Onion Router (Tor) sends your information through three different routers located across the world, making it extremely difficult to track. Originally developed in the 1990s for espionage, Tor remains one of the most effective anonymity tools available.

### Proxy Servers

Using a proxy server reroutes your internet traffic through a different IP address. Here’s how it works:
- Your information passes through your ISP and then to the proxy server, which masks your original IP before reaching the destination.

**Command for Using Proxychains:**
```bash
proxychains <nmap_scan_parameters>
```

### Configuring Proxychains

- The configuration file for Proxychains is typically located at:
  ```bash
  /etc/proxychains.conf
  ```
- If it is not in this location, use `locate` to find it:
  ```bash
  locate proxychains.conf
  ```

**Adding Proxies:**
- Scroll down in the config file and add your IP addresses and port numbers.
- Here’s an example from my configuration:
  ```plaintext
  [ProxyList]

  # add proxy here ...
  socks5 67.201.58.190 4145
  socks5 68.1.210.189 4145
  socks5 208.102.51.6 58208
  # defaults set to "tor"
  socks4 127.0.0.1 9050
  ```

**Using Proxychains with a Web Browser:**
```bash
proxychains firefox <web_address>
```
- This command will open the specified web address in Firefox, either in a new tab or in a new browser window if Firefox isn’t open.

### Configuring Proxy Chains

1. **Dynamic Chains**:
   - Uncomment `#dynamic_chain` in the config file by removing the `#` symbol.
   - Comment out `strict_chain`.
   - This setup allows Proxychains to skip non-working proxies and continue with the next available one.

2. **Random Chains**:
   - Comment out both `dynamic_chain` and `strict_chain`.
   - Uncomment `random_chain`.
   - Uncomment `chain_len` and set it to the number of proxies you have:
     ```plaintext
     chain_len = 3
     ```
   - This setup randomly selects a proxy from your list and tries to process the request. If it fails, it picks another proxy at random.

**Caution**: Free proxy chains can be risky. They increase anonymity but also latency, and the proxy servers themselves could potentially steal your information. For optimal security, use paid proxies.

---

### Recommended Paid Proxy Services

1. **PrivateProxy**: Speeds from 250Mbps to 10Gbps, starting at $29/month.
2. **SocksProxy**: Socks proxies starting at $15/month for 100Mbps.
3. **Proxify**: Offers socks and HTTP proxies, starting at $25/month for 500Mbps.
4. **Proxy.sh**: Fast and anonymous proxies, starting at $20/month.
5. **HideMyAss**: Known for VPNs but also offers proxy services starting at $24.99/month.

---

### VPNs (Virtual Private Networks)

VPNs are widely known and used to hide your internet activity from your ISP. They encrypt your data and reroute it through secure servers, masking your IP address.

---

### Private Encrypted Email

**ProtonMail** is the most secure encrypted email service available. Even administrators at ProtonMail cannot read your emails. It provides end-to-end encryption, making it a top choice for privacy-conscious users.

- **Website**: [ProtonMail](https://proton.me/)

These tools and techniques can greatly improve your online privacy, but remember that true anonymity requires a combination of practices and tools. Always be cautious and informed about the methods you choose.
