## Overview
Responder is a powerful network tool used for attacking network protocols and poisoning name resolution requests within a local network. It is commonly used during penetration tests and red team operations to capture and manipulate NetBIOS Name Service (NBT-NS), LLMNR (Link-Local Multicast Name Resolution), and MDNS (Multicast DNS) requests. By poisoning these name resolution protocols, Responder can trick clients into sending credentials to a rogue SMB or HTTP server set up by the attacker, allowing for the capture of user credentials and session hashes.

Responder is an essential tool for attackers looking to exploit weaknesses in network authentication and for security professionals who want to assess the vulnerability of their network to these types of attacks.

## Features
- **NBT-NS, LLMNR, and MDNS Poisoning:** Actively listens for broadcast requests and responds to them to redirect traffic to the attacker's machine.
- **Credential Capture:** Captures NTLMv1/NTLMv2 hashes, plaintext passwords, and NetNTLMv1/NetNTLMv2 hashes.
- **SMB Relay Attacks:** Enables relay of SMB authentication to other services on the network.
- **HTTP/HTTPS Server:** Hosts rogue HTTP/HTTPS servers to capture HTTP-based authentication credentials.
- **Proxy Authentication Capture:** Captures proxy authentication credentials from network traffic.
- **Cross-Platform:** Runs on Unix-based systems (Linux, macOS) and is included in popular security distributions like Kali Linux.

## Website
- [Responder GitHub Repository](https://github.com/lgandx/Responder)

## Installation

### On Unix-based systems (Linux/macOS):
1. **Install Responder via Package Manager (Kali Linux):**
   - Responder is pre-installed in Kali Linux. For other distributions:
   - On Debian-based systems:
```sh
sudo apt-get install responder
```
   - On Red Hat-based systems:
```sh
sudo yum install responder
```

2. **Clone from GitHub:**
   - To get the latest version:
```sh
git clone https://github.com/lgandx/Responder.git
cd Responder
```

### On Windows:
1. **Install Windows Subsystem for Linux (WSL):**
   - Responder is not natively available on Windows but can run in a WSL environment.

2. **Follow the Linux Installation Steps:**
   - Follow the Unix-based installation steps within the WSL environment.

## Basic Usage
Responder is run from the command line interface (CLI). Here are some common commands and usage examples:

### Start Responder
To start Responder on a specific network interface:
```sh
sudo responder -I eth0
```
- **`-I eth0`**: Specifies the network interface to listen on (e.g., `eth0`).

### Enable SMB and HTTP Authentication Capture
To enable SMB and HTTP server functionalities to capture credentials:
```sh
sudo responder -I eth0 -wrf
```
- **`-w`**: Enables WPAD (Web Proxy Auto-Discovery) rogue server.
- **`-r`**: Enables rogue DNS server.
- **`-f`**: Forces Wredir (Microsoft WebDAV Mini-Redirector) authentication downgrade.

### Custom Configuration
To use a custom configuration file:
```sh
sudo responder -I eth0 -c /path/to/custom.conf
```
- **`-c`**: Specifies the path to a custom configuration file.

### Running in Analyze Mode
To run Responder in analyze mode without poisoning requests (passive mode):
```sh
sudo responder -I eth0 -A
```
- **`-A`**: Analyze mode only; do not respond to requests.

### Log Output to a File
To save the output of Responder to a file for later analysis:
```sh
sudo responder -I eth0 -wrf -l /path/to/output.txt
```
- **`-l`**: Specifies the log file path.

## Key Features and Options

### LLMNR and NBT-NS Poisoning
- **Description:** Responder actively listens for LLMNR and NBT-NS queries and responds with fake answers to redirect traffic to the attacker's machine.
- **Usage:**
  - Run Responder with the `-I` option to start poisoning:
```sh
sudo responder -I eth0
```

### Credential Capture and Relay
- **Description:** Captures NTLM hashes and plaintext credentials from poisoned requests. Supports relay attacks where captured credentials are used to authenticate against other services.
- **Usage:**
  - Capture credentials with:
```sh
sudo responder -I eth0 -wrf
```
  - Relay captured credentials with:
```sh
sudo python3 /usr/share/responder/tools/RunFinger.py
```

### SMB Authentication Relay
- **Description:** Relays captured SMB authentication credentials to other systems on the network, potentially leading to unauthorized access.
- **Usage:**
  - Relay captured credentials using `NTLMRelayx` or other tools in conjunction with Responder.

### HTTP/HTTPS Rogue Server
- **Description:** Hosts rogue HTTP/HTTPS servers to capture credentials from HTTP-based authentication mechanisms like Basic, NTLM, and Digest.
- **Usage:**
  - Start the HTTP/HTTPS server with:
```sh
sudo responder -I eth0 -w
```

### WPAD Rogue Server
- **Description:** Creates a rogue WPAD server to capture proxy authentication credentials.
- **Usage:**
  - Start the WPAD server with:
```sh
sudo responder -I eth0 -w
```

## Tools for Network Security and Penetration Testing Using Responder

- **Credential Harvesting:** Use Responder to capture network credentials from protocols like SMB, HTTP, and HTTPS during internal penetration tests.
- **Network Exploitation:** Exploit weaknesses in network authentication protocols like LLMNR, NBT-NS, and WPAD to gain unauthorized access to systems and sensitive data.
- **Internal Network Reconnaissance:** Identify hosts and services on the network that respond to broadcast name resolution requests.
- **Relay Attacks:** Use captured credentials to perform relay attacks and move laterally within a network.
- **Phishing and Social Engineering:** Set up rogue servers to capture credentials during phishing or social engineering campaigns.

## Best Practices
- **Use Responder in Controlled Environments:** Always ensure that you have permission before using Responder to perform network poisoning and credential capture, as it can disrupt legitimate network traffic.
- **Limit Exposure:** Use Responder's options to limit the scope of poisoning to avoid unnecessary network disruptions and detection.
- **Monitor Network Traffic:** Regularly monitor network traffic for signs of unauthorized use of Responder or similar tools to detect potential intrusions.
- **Combine with Other Tools:** Use Responder alongside other network tools like [[Bettercap]], [[Ettercap]], and [[Wireshark]] for comprehensive network assessments.
- **Keep Responder Updated:** Regularly update Responder to benefit from the latest features, security enhancements, and bug fixes.

## References
- [Responder GitHub Repository](https://github.com/lgandx/Responder)
- [Responder Documentation and Usage](https://github.com/lgandx/Responder/wiki)
- [LLMNR/NBT-NS Poisoning with Responder](https://www.sans.org/white-papers/llmnr-nbt-ns-poisoning-responder-37930/)
- [MITRE ATT&CK Techniques](https://attack.mitre.org/techniques/T1171/)

