# Shodan

## Overview
**Shodan** is a search engine for Internet-connected devices, known as the "Google for hackers." Unlike traditional search engines that index web content, Shodan indexes information about devices connected to the Internet, such as servers, routers, webcams, IoT devices, and more. It gathers data on devices' operating systems, software versions, open ports, and even security vulnerabilities by continuously scanning the Internet for publicly accessible devices and services. 

Shodan is widely used by penetration testers, security researchers, and network administrators to perform reconnaissance, assess exposure to the Internet, identify vulnerable devices, and gather threat intelligence. It provides powerful search capabilities, filters, and an API that can be integrated into custom tools and workflows for automated scanning and monitoring.

## Features
- **Device Search Engine:** Searches for Internet-connected devices, revealing detailed information about their configurations and vulnerabilities.
- **Geolocation Data:** Provides geographic information about the devices, including country, city, and coordinates.
- **Vulnerability Detection:** Identifies devices with known vulnerabilities by cross-referencing with the Common Vulnerabilities and Exposures (CVE) database.
- **Filters and Search Operators:** Offers advanced search filters and operators to refine queries and target specific device types or configurations.
- **API Integration:** Provides a powerful API for integrating Shodan data into custom tools, applications, and workflows.
- **Monitoring and Alerts:** Allows users to set up monitoring and alerts to notify them of changes in the status of devices or networks.

## Website
- [Shodan Official Website](https://www.shodan.io/)

## Installation

### Shodan CLI Installation:

1. **Install Python and Pip:**

   - Ensure Python and pip (Python's package installer) are installed on your system.

2. **Install the Shodan Command-Line Interface (CLI):**

   - Install the Shodan CLI using pip:

```sh
pip install shodan
```

3. **Initialize Shodan CLI with Your API Key:**

   - Sign up for a Shodan account at [Shodan](https://www.shodan.io/) and retrieve your API key from your account settings.
   - Initialize Shodan with your API key:

```sh
shodan init <YOUR_SHODAN_API_KEY>
```

## Basic Usage
Shodan provides a variety of search capabilities and commands to help users find and analyze Internet-connected devices. Here are some common commands and usage examples:

### Searching for Devices
To search for devices with specific characteristics:

```sh
shodan search "apache"
```

- **`"apache"`**: Searches for devices running Apache HTTP server.

### Filtering Search Results
To refine search results using filters:

```sh
shodan search "nginx country:US"
```

- **`"nginx country:US"`**: Searches for devices running Nginx located in the United States.

### Checking Device Information
To get detailed information about a specific IP address:

```sh
shodan host <IP_ADDRESS>
```

- **`<IP_ADDRESS>`**: Specifies the IP address of the device to analyze.

### Identifying Vulnerable Devices
To search for devices with specific vulnerabilities:

```sh
shodan search "vuln:CVE-2017-0144"
```

- **`"vuln:CVE-2017-0144"`**: Searches for devices vulnerable to the EternalBlue exploit (CVE-2017-0144).

### Downloading Search Results
To download search results to a file:

```sh
shodan download results.json.gz "apache country:DE"
```

- **`results.json.gz`**: Specifies the filename to save the results.
- **`"apache country:DE"`**: Specifies the search query for Apache servers in Germany.

### Using Shodan API
To interact with Shodan using its API for automated tasks:

1. **Install Shodan Python Library:**

   - The Shodan CLI installation also includes the Python library. Import it in your Python scripts:

```python
import shodan
```

2. **Initialize the Shodan Client with API Key:**

```python
api = shodan.Shodan('<YOUR_SHODAN_API_KEY>')
```

3. **Perform Searches Using the API:**

```python
results = api.search('apache')
for result in results['matches']:
    print(result['ip_str'], result['data'])
```

### Setting Up Alerts
To set up an alert for a specific IP range or CIDR:

```sh
shodan alert create "My Alert" 192.168.1.0/24
```

- **`"My Alert"`**: Specifies the name of the alert.
- **`192.168.1.0/24`**: Specifies the IP range or CIDR to monitor.

## Key Features and Commands

### Device Search Engine
- **Description:** Searches for Internet-connected devices and provides detailed information about their configurations and potential vulnerabilities.
- **Usage:**
```sh
shodan search "apache"
```

### Geolocation Data
- **Description:** Provides geographic information about devices, including country, city, and coordinates.
- **Usage:**
```sh
shodan search "nginx country:US"
```

### Vulnerability Detection
- **Description:** Identifies devices with known vulnerabilities by cross-referencing with the CVE database.
- **Usage:**
```sh
shodan search "vuln:CVE-2017-0144"
```

### API Integration
- **Description:** Offers a powerful API for integrating Shodan data into custom tools, applications, and workflows.
- **Usage:**
```python
import shodan
api = shodan.Shodan('<YOUR_SHODAN_API_KEY>')
results = api.search('apache')
```

### Monitoring and Alerts
- **Description:** Allows users to set up monitoring and alerts to notify them of changes in the status of devices or networks.
- **Usage:**
```sh
shodan alert create "My Alert" 192.168.1.0/24
```

### Downloading and Saving Results
- **Description:** Enables users to download search results to a file for offline analysis and reporting.
- **Usage:**
```sh
shodan download results.json.gz "apache country:DE"
```

## Tools for Information Gathering and Security Assessment Using Shodan

- **Network Reconnaissance:** Use Shodan to identify exposed devices on the Internet, including routers, servers, webcams, and IoT devices, to assess their security posture.
- **Vulnerability Management:** Search for devices with known vulnerabilities and outdated software to identify potential security risks within an organization or network.
- **Threat Intelligence:** Monitor networks for changes in device status, new vulnerabilities, and emerging threats to proactively respond to security incidents.
- **Cybersecurity Audits:** Conduct audits of Internet-facing assets to ensure compliance with security policies and best practices, reducing the risk of exposure to cyber attacks.
- **Red Teaming and Penetration Testing:** Gather information on target networks and devices to plan and execute effective penetration tests and red team exercises.

## Best Practices
- **Use Shodan Responsibly:** Always ensure that you have proper authorization before using Shodan for reconnaissance and information gathering tasks.
- **Stay Within Legal Boundaries:** Be aware of the legal implications of using Shodan and ensure compliance with local laws and regulations.
- **Combine with Other Tools:** Use Shodan alongside other information gathering tools like [[theHarvester]], [[Recon-ng]], and [[Maltego]] for comprehensive assessments.
- **Regularly Update Shodan CLI and API Usage:** Keep up-to-date with Shodan’s features and changes to maximize its effectiveness.
- **Analyze Results Carefully:** Review the output of Shodan searches carefully to identify potential vulnerabilities, misconfigurations, and opportunities for further investigation.

## References
- [Shodan Official Website](https://www.shodan.io/)
- [Shodan Documentation](https://developer.shodan.io/api)
- [Shodan Tutorial for Device Search and Vulnerability Detection](https://www.hackingarticles.in/shodan-tutorial-device-search-and-vulnerability-detection/)
- [Shodan Cheat Sheet](https://highon.coffee/blog/shodan-cheat-sheet/)
- [Using Shodan for Cyber Reconnaissance](https://null-byte.wonderhowto.com/how-to/use-shodan-for-cyber-reconnaissance-0197791/)

