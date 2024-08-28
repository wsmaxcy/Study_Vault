## Overview
Aquatone is a tool for visual inspection of websites across a large number of hosts. It is used by penetration testers, bug bounty hunters, and security researchers to quickly identify web services running on different subdomains and IP addresses. Aquatone allows users to take screenshots of websites, providing a visual overview of the web services within a target domain or IP range. It supports multiple discovery tools and can process Nmap XML output to gather a list of hosts to scan.

Aquatone is particularly useful for reconnaissance and enumeration during penetration testing and red teaming exercises, helping identify and document web-based attack surfaces.

## Features
- **Automated Website Screenshotting:** Takes screenshots of multiple websites across different subdomains and IP addresses.
- **HTTP Request and Response Inspection:** Captures HTTP headers and responses for further analysis.
- **Subdomain and Host Enumeration:** Integrates with other discovery tools (such as Nmap) to enumerate subdomains and hosts.
- **Customizable Scan Profiles:** Allows users to customize scan profiles to control the scanning behavior and output format.
- **Multiple Output Formats:** Supports various output formats, including HTML and JSON, for easy documentation and reporting.
- **Cross-Platform Support:** Available on Unix-based systems (Linux, macOS) and Windows.

## Website
- [Aquatone GitHub Repository](https://github.com/michenriksen/aquatone)

## Installation

### On Unix-based systems (Linux/macOS):

1. **Install Aquatone via GitHub:**

   - Install `Go` (Golang), as Aquatone is written in Go:

```sh
sudo apt-get install golang  # Debian-based systems
brew install go  # macOS using Homebrew
```

   - Clone the Aquatone repository from GitHub:

```sh
git clone https://github.com/michenriksen/aquatone.git
cd aquatone
```

   - Build Aquatone using Go:

```sh
go build .
```

   - Move the Aquatone executable to a directory in your PATH, such as `/usr/local/bin`:

```sh
sudo mv aquatone /usr/local/bin/
```

2. **Install via pre-built binary:**

   - Download the latest release from the [Aquatone Releases Page](https://github.com/michenriksen/aquatone/releases).

   - Extract the downloaded archive and move the binary to a directory in your PATH.

### On Windows:

1. **Install via pre-built binary:**

   - Download the latest Windows binary from the [Aquatone Releases Page](https://github.com/michenriksen/aquatone/releases).

   - Extract the downloaded archive and add the binary to your PATH environment variable.

2. **Run Aquatone:**

   - Use the command prompt or PowerShell to run Aquatone:

```sh
aquatone
```

## Basic Usage
Aquatone can process domain and subdomain lists, Nmap XML output, and more. Here are some common commands and usage examples:

### Basic Domain Scan
To perform a basic scan against a list of domains:

1. **Create a file containing domains:**

   - Save the list of domains to a file named `domains.txt`.

2. **Run Aquatone against the domain list:**

```sh
cat domains.txt | aquatone
```

### Processing Nmap XML Output
To process Nmap XML output for a list of hosts to scan:

1. **Run Nmap and save the output in XML format:**

```sh
nmap -oX nmap_output.xml -p80,443 example.com
```

2. **Run Aquatone using the Nmap XML output:**

```sh
cat nmap_output.xml | aquatone -nmap
```

### Customizing HTTP Headers
To customize HTTP headers for the scan:

```sh
cat domains.txt | aquatone -H "User-Agent: CustomAgent" -H "Cookie: sessionid=xyz"
```

- **`-H "Header: Value"`**: Adds custom HTTP headers to the request.

### Specifying an Output Directory
To specify a custom output directory:

```sh
cat domains.txt | aquatone -out /path/to/output
```

- **`-out /path/to/output`**: Specifies the output directory for scan results.

### Specifying Ports to Scan
To specify which ports to scan for web services:

```sh
cat domains.txt | aquatone -ports 80,443,8080
```

- **`-ports 80,443,8080`**: Scans the specified ports.

## Key Features and Options

### Website Screenshotting
- **Description:** Automatically takes screenshots of websites across multiple subdomains and IP addresses for visual inspection.
- **Usage:**
```sh
cat domains.txt | aquatone
```

### HTTP Request and Response Inspection
- **Description:** Captures and displays HTTP headers and responses, allowing for detailed analysis of web services.
- **Usage:**
```sh
cat domains.txt | aquatone -http
```

### Subdomain and Host Enumeration
- **Description:** Processes input from various discovery tools (e.g., Nmap) to enumerate hosts and subdomains for scanning.
- **Usage:**
```sh
cat nmap_output.xml | aquatone -nmap
```

### Custom Scan Profiles
- **Description:** Allows users to customize scan profiles, including HTTP headers, request methods, and ports.
- **Usage:**
```sh
cat domains.txt | aquatone -H "User-Agent: CustomAgent" -ports 80,443
```

### Output Formats and Reporting
- **Description:** Generates reports in multiple formats (HTML, JSON) for easy documentation and analysis.
- **Usage:**
```sh
cat domains.txt | aquatone -out /path/to/output -format json
```

## Tools for Web Application Reconnaissance and Security Testing Using Aquatone

- **Web Service Discovery:** Use Aquatone to identify and document all web services running on a target domain or IP range by taking screenshots and capturing HTTP responses.
- **Visual Inspection:** Quickly identify interesting or suspicious web pages that require further investigation or manual testing.
- **Automated Reconnaissance:** Automate the process of enumerating subdomains and hosts to speed up the reconnaissance phase of a penetration test.
- **Web Application Assessment:** Analyze HTTP headers and responses to identify potential misconfigurations, security issues, and vulnerable endpoints.
- **Comprehensive Documentation:** Generate detailed reports and visual documentation of the web application landscape for reporting and analysis.

## Best Practices
- **Use Aquatone Responsibly:** Always ensure that you have proper authorization before using Aquatone to perform reconnaissance and scanning activities.
- **Combine with Other Tools:** Use Aquatone alongside other web application security tools like [[Nmap]], [[Sublist3r]], and [[Burp Suite]] for comprehensive reconnaissance and testing.
- **Customize Scans:** Tailor scan profiles and HTTP headers to target specific web services and avoid detection by web application firewalls (WAFs).
- **Keep Aquatone Updated:** Regularly update Aquatone to benefit from the latest features, security enhancements, and bug fixes.
- **Analyze Results:** Review screenshots and HTTP responses carefully to identify potential vulnerabilities, exposed services, and misconfigurations.

## References
- [Aquatone GitHub Repository](https://github.com/michenriksen/aquatone)
- [Aquatone Documentation](https://github.com/michenriksen/aquatone#readme)
- [Visual Reconnaissance with Aquatone](https://null-byte.wonderhowto.com/how-to/use-aquatone-quickly-get-visual-representation-web-target-0182574/)
- [Aquatone Tutorial for Bug Bounty Hunters](https://www.hackingarticles.in/aquatone-tool-for-bugbounty-hunters/)
- [Aquatone Cheatsheet](https://highon.coffee/blog/aquatone-cheat-sheet/)

