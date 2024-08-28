# SIPVicious

## Overview
SIPVicious is a popular open-source toolset for auditing and attacking SIP (Session Initiation Protocol) and VoIP (Voice over IP) networks. It is widely used by penetration testers, VoIP security researchers, and network administrators to assess the security of SIP-based services and networks. SIPVicious includes several tools that can be used to scan for SIP devices, enumerate extensions, and perform brute-force attacks to crack SIP passwords.

SIPVicious is often employed to identify vulnerabilities in SIP deployments, such as weak credentials, misconfigurations, and insecure endpoints, making it an essential tool for testing the robustness and security of VoIP systems.

## Features
- **SIP Device Scanning:** Identifies SIP devices on a network using the `svmap` tool.
- **SIP Extension Enumeration:** Enumerates SIP extensions using the `svwar` tool.
- **SIP Password Cracking:** Performs brute-force attacks on SIP accounts using the `svcrack` tool.
- **SIP INVITE Flooding:** Tests the ability of a SIP server to handle INVITE requests using the `svflood` tool.
- **Cross-Platform Compatibility:** Available on Unix-based systems (Linux, macOS) and Windows environments.
- **Command-Line Interface:** Provides a powerful and flexible command-line interface for scripting and automation.

## Website
- [SIPVicious GitHub Repository](https://github.com/sipcapture/sipvicious)

## Installation

### On Unix-based systems (Linux/macOS):

1. **Install SIPVicious via pip:**

   - Ensure you have Python 3 and pip installed, then install SIPVicious using pip:

```sh
pip3 install sipvicious
```

2. **Install via GitHub:**

   - Clone the SIPVicious repository from GitHub:

```sh
git clone https://github.com/sipcapture/sipvicious.git
cd sipvicious
```

   - Install the required dependencies and set up SIPVicious:

```sh
pip3 install -r requirements.txt
python3 setup.py install
```

### On Windows:

1. **Install SIPVicious via pip:**

   - Open Command Prompt and run:

```cmd
pip install sipvicious
```

2. **Install via GitHub:**

   - Clone the SIPVicious repository from GitHub and follow the same steps as for Unix-based systems.

## Basic Usage
SIPVicious includes several tools for different types of attacks and scans on SIP networks. Here are some common commands and usage examples:

### Scanning for SIP Devices
To scan for SIP devices on a network:

1. **Run svmap to Identify SIP Devices:**

```sh
svmap <target-ip-range>
```

   - **`<target-ip-range>`**: Specifies the IP range to scan (e.g., `192.168.1.0/24`).

### Enumerating SIP Extensions
To enumerate SIP extensions:

1. **Run svwar to Enumerate Extensions:**

```sh
svwar -m INVITE -e100-200 <target-ip>
```

   - **`-m INVITE`**: Specifies the method to use (INVITE in this example).
   - **`-e100-200`**: Specifies the range of extensions to enumerate (100-200 in this example).
   - **`<target-ip>`**: Specifies the target IP address of the SIP server.

### Cracking SIP Passwords
To perform a brute-force attack on SIP passwords:

1. **Run svcrack with a Wordlist:**

```sh
svcrack -u userlist.txt -p passlist.txt <target-ip>
```

   - **`-u userlist.txt`**: Specifies the path to the user list file.
   - **`-p passlist.txt`**: Specifies the path to the password list file.
   - **`<target-ip>`**: Specifies the target IP address of the SIP server.

### SIP INVITE Flooding
To test the SIP server's ability to handle INVITE requests:

1. **Run svflood to Flood SIP INVITE Requests:**

```sh
svflood <target-ip>
```

   - **`<target-ip>`**: Specifies the target IP address of the SIP server.

### Customizing Scans
To customize the scan process, such as specifying a custom user agent:

1. **Run svmap with a Custom User Agent:**

```sh
svmap -A "CustomUserAgent" <target-ip-range>
```

   - **`-A "CustomUserAgent"`**: Specifies the custom user agent string to use.

## Key Features and Commands

### SIP Device Scanning
- **Description:** Identifies SIP devices on a network by sending SIP requests to discover devices and services.
- **Usage:**
```sh
svmap <target-ip-range>
```

### SIP Extension Enumeration
- **Description:** Enumerates SIP extensions on a SIP server to identify valid extensions that can be targeted in attacks.
- **Usage:**
```sh
svwar -m INVITE -e100-200 <target-ip>
```

### SIP Password Cracking
- **Description:** Performs brute-force attacks on SIP accounts to crack weak passwords and gain unauthorized access.
- **Usage:**
```sh
svcrack -u userlist.txt -p passlist.txt <target-ip>
```

### SIP INVITE Flooding
- **Description:** Floods a SIP server with INVITE requests to test its ability to handle high traffic loads and potential denial-of-service conditions.
- **Usage:**
```sh
svflood <target-ip>
```

### Custom Scan Options
- **Description:** Allows users to customize SIP scans with various options, such as user agents, headers, and methods.
- **Usage:**
```sh
svmap -A "CustomUserAgent" <target-ip-range>
```

## Tools for VoIP Security and Offensive Security Using SIPVicious

- **VoIP Security Assessment:** Use SIPVicious to identify vulnerabilities in SIP and VoIP deployments, such as weak passwords and insecure configurations.
- **Network Reconnaissance:** Perform reconnaissance on SIP networks to gather information about SIP devices, extensions, and services.
- **Password Auditing:** Test the strength of SIP passwords using brute-force attacks to identify weak or default credentials.
- **Denial-of-Service Testing:** Simulate denial-of-service attacks on SIP servers using SIP INVITE flooding to evaluate server robustness.
- **Post-Exploitation:** Utilize information gathered from SIPVicious scans to further exploit SIP networks and gain unauthorized access.

## Best Practices
- **Use SIPVicious Responsibly:** Always ensure that you have proper authorization before using SIPVicious for offensive security tasks and network assessments.
- **Stay Within Legal Boundaries:** Be aware of the legal implications of using SIPVicious and ensure compliance with local laws and regulations.
- **Combine with Other Tools:** Use SIPVicious alongside other VoIP security tools like [[Wireshark]], [[SIPcrack]], and [[Nmap]] for comprehensive assessments.
- **Regularly Update SIPVicious:** Keep SIPVicious up-to-date to benefit from the latest features, security enhancements, and bug fixes.
- **Analyze Results Carefully:** Review the output of SIPVicious commands carefully to identify potential vulnerabilities, misconfigurations, and opportunities for further exploitation.

## References
- [SIPVicious GitHub Repository](https://github.com/sipcapture/sipvicious)
- [SIPVicious Documentation](https://github.com/sipcapture/sipvicious/blob/master/README.md)
- [SIPVicious Tutorial for VoIP Security Testing](https://www.hackingarticles.in/sipvicious-voip-security-testing/)
- [SIPVicious Cheat Sheet](https://highon.coffee/blog/sipvicious-cheat-sheet/)
- [Using SIPVicious for SIP Network Reconnaissance](https://null-byte.wonderhowto.com/how-to/use-sipvicious-for-sip-network-reconnaissance-0197654/)

