## Overview
Aircrack-ng is a comprehensive suite of tools designed for assessing the security of wireless networks. It is widely used by penetration testers, security researchers, and network administrators to monitor, attack, test, and crack Wi-Fi networks. Aircrack-ng includes various tools for tasks such as capturing packets, attacking access points, cracking WEP and WPA/WPA2-PSK keys, and replaying attacks.

As a robust and versatile toolkit, Aircrack-ng is an essential tool for anyone looking to evaluate the security of wireless networks or learn more about wireless security.

## Features
- **Packet Capture:** Captures packets from 802.11 wireless networks to analyze network traffic and find vulnerabilities.
- **Network Attacks:** Performs various attacks, including deauthentication, fake access points, and replay attacks, to test network defenses.
- **WEP and WPA/WPA2-PSK Cracking:** Cracks WEP and WPA/WPA2-PSK keys using captured packets and wordlists.
- **Replay Attacks:** Reinjects captured packets to generate more traffic, increasing the likelihood of cracking a network key.
- **Wireless Card Support:** Supports a wide range of wireless network adapters, including those capable of injection and monitor mode.
- **Cross-Platform:** Available on Linux, Windows, macOS, and other Unix-based systems.

## Website
- [Aircrack-ng Official Website](https://www.aircrack-ng.org/)

## Installation

### On Unix-based systems (Linux/macOS):
1. **Install Aircrack-ng via Package Manager:**
   - On Debian-based systems:
```sh
sudo apt-get install aircrack-ng
```
   - On Red Hat-based systems:
```sh
sudo yum install aircrack-ng
```
   - On macOS using Homebrew:
```sh
brew install aircrack-ng
```

2. **Build from Source:**
   - Download the source code from the [Aircrack-ng Download Page](https://www.aircrack-ng.org/downloads.html).
   - Extract and compile:
```sh
tar -zxvf aircrack-ng-<version>.tar.gz
cd aircrack-ng-<version>
make
sudo make install
```

### On Windows:
1. **Download the Installer:**
   - Download the latest Windows binaries from the [Aircrack-ng Download Page](https://www.aircrack-ng.org/downloads.html).

2. **Extract and Run:**
   - Extract the downloaded files and run the Aircrack-ng executables from the command prompt.

## Basic Usage
Aircrack-ng is a suite of tools, each with its own specific purpose. Here are some common commands and usage examples for the main tools:

### Putting a Wireless Card in Monitor Mode
To put a wireless card into monitor mode:
```sh
sudo airmon-ng start wlan0
```
- **`wlan0`**: The name of the wireless interface to be put into monitor mode.

### Capturing Packets
To capture packets from a specific wireless network:
```sh
sudo airodump-ng wlan0mon
```
- **`wlan0mon`**: The wireless interface in monitor mode.

### Targeting a Specific Access Point
To capture packets from a specific access point and channel:
```sh
sudo airodump-ng -c 6 --bssid AA:BB:CC:DD:EE:FF -w capture wlan0mon
```
- **`-c 6`**: Specifies the channel (e.g., `6`).
- **`--bssid AA:BB:CC:DD:EE:FF`**: The BSSID of the target access point.
- **`-w capture`**: Writes the captured packets to a file named `capture`.

### Cracking WEP Encryption
To crack a WEP key using captured packets:
```sh
sudo aircrack-ng -b AA:BB:CC:DD:EE:FF capture-01.cap
```
- **`-b AA:BB:CC:DD:EE:FF`**: The BSSID of the target network.
- **`capture-01.cap`**: The file containing the captured packets.

### Cracking WPA/WPA2-PSK Encryption
To crack a WPA/WPA2-PSK key using a wordlist:
```sh
sudo aircrack-ng -w /path/to/wordlist.txt -b AA:BB:CC:DD:EE:FF capture-01.cap
```
- **`-w /path/to/wordlist.txt`**: Specifies the path to the wordlist file.
- **`-b AA:BB:CC:DD:EE:FF`**: The BSSID of the target network.
- **`capture-01.cap`**: The file containing the captured handshake packets.

### Deauthentication Attack
To perform a deauthentication attack to disconnect clients from a target access point:
```sh
sudo aireplay-ng -0 10 -a AA:BB:CC:DD:EE:FF wlan0mon
```
- **`-0 10`**: Sends 10 deauthentication packets.
- **`-a AA:BB:CC:DD:EE:FF`**: The BSSID of the target access point.

## Key Features and Tools

### Airmon-ng
- **Description:** A tool to enable and disable monitor mode on wireless interfaces.
- **Usage:**
```sh
sudo airmon-ng start wlan0
```

### Airodump-ng
- **Description:** A tool to capture packets from wireless networks and collect information such as BSSIDs, ESSIDs, and signal strength.
- **Usage:**
```sh
sudo airodump-ng wlan0mon
```

### Aireplay-ng
- **Description:** A tool to perform packet injection attacks, such as deauthentication attacks, to generate more traffic or disconnect clients.
- **Usage:**
```sh
sudo aireplay-ng -0 10 -a AA:BB:CC:DD:EE:FF wlan0mon
```

### Aircrack-ng
- **Description:** The main tool for cracking WEP and WPA/WPA2-PSK keys using captured packets.
- **Usage:**
```sh
sudo aircrack-ng -w /path/to/wordlist.txt -b AA:BB:CC:DD:EE:FF capture-01.cap
```

### Airdecap-ng
- **Description:** A tool to decrypt WEP/WPA/WPA2-PSK encrypted packets with known keys.
- **Usage:**
```sh
airdecap-ng -p passphrase -e SSID capture-01.cap
```

### Packet Replay and Injection
- **Description:** Replay captured packets to generate traffic or perform man-in-the-middle (MitM) attacks.
- **Usage:**
```sh
sudo aireplay-ng --interactive wlan0mon
```

## Tools for Wireless Network Security and Penetration Testing Using Aircrack-ng

- **Wireless Network Auditing:** Use Aircrack-ng to capture packets and analyze wireless network traffic for security assessments.
- **Password Cracking:** Perform brute-force attacks on WEP and WPA/WPA2-PSK keys using captured handshake packets and wordlists.
- **Network Reconnaissance:** Gather information about nearby wireless networks, including their BSSIDs, channels, encryption types, and connected clients.
- **Deauthentication Attacks:** Execute deauthentication attacks to disconnect clients and capture handshake packets for cracking.
- **Replay and Injection Attacks:** Replay captured packets to generate traffic or manipulate data streams in wireless networks.

## Best Practices
- **Use Aircrack-ng Responsibly:** Always ensure that you have proper authorization before using Aircrack-ng to capture packets or perform attacks on wireless networks.
- **Stay Within Legal Boundaries:** Be aware of the legal implications of using wireless security tools and ensure compliance with local laws and regulations.
- **Limit the Scope of Attacks:** Use specific BSSIDs and channels to limit the scope of attacks and avoid unnecessary interference with other networks.
- **Use Strong Encryption:** Encourage the use of strong encryption (WPA2/WPA3) on wireless networks to protect against brute-force and dictionary attacks.
- **Combine with Other Tools:** Use Aircrack-ng alongside other wireless security tools like [[Wireshark]], [[Bettercap]], and [[Kismet]] for comprehensive assessments.
- **Keep Aircrack-ng Updated:** Regularly update Aircrack-ng to benefit from the latest features, security enhancements, and bug fixes.

## References
- [Aircrack-ng Official Website](https://www.aircrack-ng.org/)
- [Aircrack-ng Documentation](https://aircrack-ng.org/documentation.html)
- [Aircrack-ng GitHub Repository](https://github.com/aircrack-ng/aircrack-ng)
- [Wireless Network Cracking with Aircrack-ng](https://null-byte.wonderhowto.com/how-to/hack-wi-fi-cracking-wpa2-psk-passwords-using-aircrack-ng-0148323/)
- [Aircrack-ng Tutorial and Cheat Sheet](https://www.aircrack-ng.org/doku.php?id=newbie_guide)

