## Overview
Nikto2 is an open-source web server scanner designed to identify potential vulnerabilities and security issues in web servers. It performs comprehensive tests against web servers for multiple items, including over 6,700 potentially dangerous files and programs, outdated server software, and various server configuration issues. Nikto2 is widely used by penetration testers, security researchers, and system administrators to assess the security posture of web servers and web applications.

Nikto2 is a robust and versatile tool that provides quick and detailed information about the security state of a web server, making it an essential tool for web application security assessments.

## Features
- **Comprehensive Web Server Scanning:** Detects outdated server software, potential security issues, and common vulnerabilities.
- **SSL/TLS Testing:** Performs checks for SSL/TLS configurations and vulnerabilities.
- **Customizable Scans:** Allows users to configure scans with custom plugins, databases, and tuning options.
- **Support for Multiple Protocols:** Scans HTTP, HTTPS, and other web protocols to identify vulnerabilities across various services.
- **Output Reporting:** Generates detailed reports in multiple formats, including HTML, XML, CSV, and plain text.
- **Plugin Support:** Extends functionality through a modular plugin architecture to perform advanced checks.
- **Cross-Platform:** Available on Unix-based systems (Linux, macOS) and Windows.

## Website
- [Nikto Project Website](https://cirt.net/Nikto2)

## Installation

### On Unix-based systems (Linux/macOS):

1. **Install Nikto2 via Package Manager:**

   - **On Debian-based systems:**

```sh
sudo apt-get install nikto
```

   - **On Red Hat-based systems:**

```sh
sudo yum install nikto
```

2. **Install via GitHub:**

   - Clone the Nikto2 repository from GitHub:

```sh
git clone https://github.com/sullo/nikto.git
cd nikto/program
```

   - Run Nikto2 directly using Perl:

```sh
perl nikto.pl
```

### On Windows:

1. **Install Nikto2:**

   - Download the Nikto2 files from the [Nikto GitHub Repository](https://github.com/sullo/nikto).
   - Ensure Perl is installed (ActivePerl or Strawberry Perl is recommended).
   
2. **Run Nikto2:**

   - Use the Perl interpreter to run Nikto2:

```sh
perl nikto.pl
```

## Basic Usage
Nikto2 is a command-line tool with various options for web server scanning. Here are some common commands and usage examples:

### Basic Web Server Scan
To perform a basic scan against a web server:

```sh
perl nikto.pl -h http://target.com
```

- **`-h http://target.com`**: Specifies the target URL or IP address to scan.

### Scanning a Specific Port
To scan a web server on a specific port:

```sh
perl nikto.pl -h http://target.com -p 8080
```

- **`-p 8080`**: Specifies the port to scan.

### Scanning HTTPS Web Servers
To perform a scan on an HTTPS web server:

```sh
perl nikto.pl -h https://target.com
```

### Output Results to a File
To save scan results to a file for later analysis:

```sh
perl nikto.pl -h http://target.com -o output.html -Format html
```

- **`-o output.html`**: Specifies the output file.
- **`-Format html`**: Sets the output format to HTML.

### Using Plugins for Extended Scanning
To use specific plugins for scanning:

```sh
perl nikto.pl -h http://target.com -Plugins 'apache'
```

- **`-Plugins 'apache'`**: Specifies the plugin to use during the scan.

### Tuning Scans for Specific Tests
To tune scans for specific types of tests:

```sh
perl nikto.pl -h http://target.com -Tuning 1 2 3
```

- **`-Tuning 1 2 3`**: Specifies the scan types (1 for interesting files, 2 for outdated servers, 3 for security checks).

## Key Features and Options

### Comprehensive Vulnerability Scanning
- **Description:** Performs detailed scans of web servers to detect outdated software, insecure configurations, and potential vulnerabilities.
- **Usage:**
```sh
perl nikto.pl -h http://target.com
```

### SSL/TLS Security Checks
- **Description:** Performs checks for SSL/TLS vulnerabilities, including weak ciphers and expired certificates.
- **Usage:**
```sh
perl nikto.pl -h https://target.com -ssl
```

### Custom Plugins and Scanning Modules
- **Description:** Supports custom plugins and modules to extend functionality and perform advanced checks.
- **Usage:**
```sh
perl nikto.pl -h http://target.com -Plugins 'apache,php'
```

### Advanced Output Reporting
- **Description:** Generates detailed reports in various formats for easy documentation and analysis.
- **Usage:**
```sh
perl nikto.pl -h http://target.com -o report.xml -Format xml
```

### Tuning and Customization
- **Description:** Allows users to customize scans by selecting specific types of tests and excluding unnecessary ones.
- **Usage:**
```sh
perl nikto.pl -h http://target.com -Tuning 9
```

## Tools for Web Server Security Testing Using Nikto2

- **Vulnerability Identification:** Use Nikto2 to identify common vulnerabilities, outdated software, and insecure configurations on web servers.
- **Security Audits:** Perform regular security audits of web servers to ensure compliance with security best practices.
- **SSL/TLS Assessment:** Test SSL/TLS configurations for weak ciphers, expired certificates, and other security weaknesses.
- **Web Application Hardening:** Identify and remediate exposed files, directories, and server misconfigurations that could be exploited by attackers.
- **Automated Scanning:** Automate the process of web server scanning and vulnerability assessment as part of a continuous security monitoring strategy.

## Best Practices
- **Use Nikto2 Responsibly:** Always ensure that you have proper authorization before using Nikto2 to scan web servers for vulnerabilities.
- **Regularly Update Databases:** Keep Nikto2 databases up-to-date to benefit from the latest vulnerability checks and plugin enhancements.
- **Customize Scans:** Use tuning options and custom plugins to focus scans on relevant tests and reduce noise from irrelevant checks.
- **Combine with Other Tools:** Use Nikto2 alongside other web application security tools like [[Nmap]], [[Burp Suite]], and [[OWASP ZAP]] for comprehensive assessments.
- **Document Findings:** Generate detailed reports for documentation and follow up with appropriate remediation actions based on the scan results.

## References
- [Nikto Project Website](https://cirt.net/Nikto2)
- [Nikto GitHub Repository](https://github.com/sullo/nikto)
- [Nikto User Guide](https://cirt.net/nikto2-docs/)
- [How to Use Nikto for Web Vulnerability Scanning](https://null-byte.wonderhowto.com/how-to/use-nikto-scan-for-web-vulnerabilities-0186463/)
- [Nikto Cheatsheet](https://highon.coffee/blog/nikto-cheat-sheet/)

