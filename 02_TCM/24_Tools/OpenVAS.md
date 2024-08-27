Open Vulnerability Assessment System
## Overview
OpenVAS (Open Vulnerability Assessment System) is a comprehensive open-source vulnerability scanner and vulnerability management solution. It is part of the Greenbone Vulnerability Management (GVM) suite and provides capabilities for detecting security issues in systems, networks, and applications. OpenVAS is widely used by security professionals, network administrators, and penetration testers to identify vulnerabilities, misconfigurations, and security weaknesses within an IT environment.

OpenVAS supports both unauthenticated and authenticated scanning, allowing it to perform detailed assessments of systems from an external perspective and from within, giving a more thorough understanding of security posture.

## Features
- **Comprehensive Vulnerability Scanning:** Identifies security vulnerabilities, misconfigurations, and missing patches in systems and applications.
- **Regularly Updated Feeds:** Uses up-to-date Network Vulnerability Tests (NVTs) from the Greenbone Community Feed or Greenbone Security Feed.
- **Customizable Scans:** Allows users to configure scan settings, choose specific NVTs, and schedule regular scans.
- **Authenticated and Unauthenticated Scanning:** Performs scans with or without valid credentials to assess both internal and external security postures.
- **Detailed Reporting:** Generates comprehensive reports in various formats (PDF, HTML, XML) for documentation and remediation purposes.
- **Cross-Platform:** Available for Linux, and can be run in a virtualized environment on other operating systems.

## Website
- [OpenVAS Official Website](https://www.openvas.org/)
- [Greenbone Security Manager (GSM)](https://www.greenbone.net/en/)

## Installation

### On Unix-based systems (Linux):
1. **Install OpenVAS via Package Manager:**
   - On Debian-based systems (e.g., Ubuntu):
```sh
sudo apt-get install openvas
```
   - On Red Hat-based systems (e.g., CentOS):
```sh
sudo yum install openvas
```

2. **Install OpenVAS using Greenbone Vulnerability Management (GVM):**
   - Follow detailed installation instructions on the [Greenbone Community Edition Setup](https://greenbone.github.io/docs/latest/22.4/installation/gvmd_installation.html) page.

3. **Build from Source:**
   - Download the source code from the [Greenbone GitHub Repository](https://github.com/greenbone).
   - Follow the build and installation instructions provided in the repository README files.

### Post-Installation Setup
1. **Initialize OpenVAS:**
   - Initialize the OpenVAS setup and update feeds:
```sh
sudo gvm-setup
```

2. **Start OpenVAS Services:**
   - Start the OpenVAS manager, scanner, and other necessary services:
```sh
sudo gvm-start
```

3. **Access the Web Interface:**
   - Open a web browser and navigate to `https://<server-ip>:9392` to access the Greenbone Security Assistant (GSA) web interface.

## Basic Usage
OpenVAS can be accessed via the Greenbone Security Assistant (GSA) web interface or via command-line tools. Here are some basic usage steps:

### Logging into the Web Interface
1. **Open the Web Interface:**
   - Navigate to `https://<server-ip>:9392` in a web browser.
   
2. **Log in with Credentials:**
   - Use the default credentials or the ones set during installation (`admin` / `password`).

### Running a Vulnerability Scan
1. **Create a New Target:**
   - Navigate to **Configuration** > **Targets** > **New Target**.
   - Enter the target's name and IP address range.

2. **Create a New Task:**
   - Go to **Scans** > **Tasks** > **New Task**.
   - Fill in the task name, select the target created earlier, choose a scan configuration (e.g., Full and fast), and save.

3. **Start the Scan:**
   - Start the task by clicking the play button next to it.

### Analyzing Scan Results
1. **View Scan Reports:**
   - Navigate to **Scans** > **Reports** to view the completed scan reports.
   - Click on a report to see detailed information about detected vulnerabilities.

2. **Export Reports:**
   - Export reports in various formats (PDF, HTML, XML) for documentation or further analysis.

### Updating NVT Feeds
To update the NVT (Network Vulnerability Tests) feed:
```sh
sudo greenbone-nvt-sync
```

### Command-Line Interface (CLI)
To use the `omp` command-line tool to manage OpenVAS tasks:
1. **List Available Tasks:**
```sh
omp -u admin -w password -G
```

2. **Start a Task:**
```sh
omp -u admin -w password --start-task <task-id>
```

## Key Features and Configurations

### Custom Scan Configurations
- **Description:** Allows users to create custom scan configurations to tailor vulnerability scans to specific needs and reduce scan time.
- **Usage:**
  - Navigate to **Configuration** > **Scan Configs** > **New Scan Config** to create a custom configuration.

### Credentialed Scanning
- **Description:** Performs scans with valid credentials, allowing for deeper assessment of systems and identification of vulnerabilities that unauthenticated scans might miss.
- **Usage:**
  - Navigate to **Configuration** > **Credentials** > **New Credential** to create and assign credentials to scans.

### Scheduled Scans
- **Description:** Automates vulnerability scans by scheduling them to run at specific intervals, ensuring continuous monitoring and compliance.
- **Usage:**
  - Navigate to **Scans** > **Schedules** > **New Schedule** to configure scan intervals and timing.

### Detailed Reporting and Analysis
- **Description:** Generates detailed reports of vulnerabilities, including severity levels, CVSS scores, and remediation recommendations.
- **Usage:**
  - View and manage reports under **Scans** > **Reports**.

### Alerts and Notifications
- **Description:** Configures alerts and notifications to inform security teams of newly detected vulnerabilities or scan completions.
- **Usage:**
  - Set up alerts under **Configuration** > **Alerts** > **New Alert**.

## Tools for Vulnerability Management and Security Assessment Using OpenVAS

- **Comprehensive Vulnerability Scanning:** Use OpenVAS to perform detailed scans on networks, systems, and applications to identify potential vulnerabilities and security weaknesses.
- **Continuous Monitoring:** Schedule regular scans to ensure ongoing monitoring of the security posture and compliance with security policies.
- **Remediation Guidance:** Leverage OpenVAS reports to prioritize vulnerabilities based on severity and implement appropriate remediation strategies.
- **Security Audits:** Use OpenVAS as part of security audits to assess the overall security posture and validate the effectiveness of existing security controls.
- **Network Hardening:** Identify and remediate misconfigurations and vulnerabilities that could be exploited by attackers to strengthen network defenses.

## Best Practices
- **Run Regular Scans:** Perform regular vulnerability scans to identify and remediate new vulnerabilities and ensure compliance with security policies.
- **Use Credentialed Scanning:** Perform authenticated scans whenever possible to obtain a more comprehensive assessment of vulnerabilities.
- **Limit Scan Scope:** Define specific targets and use custom scan configurations to minimize network disruption and reduce false positives.
- **Monitor and Update Feeds:** Regularly update NVT feeds and monitor OpenVAS for new updates to ensure the scanner has the latest vulnerability information.
- **Combine with Other Tools:** Use OpenVAS alongside other security tools like [[Nmap]], [[Wireshark]], and [[Nessus]] for a comprehensive security assessment.
- **Keep OpenVAS Updated:** Regularly update OpenVAS and its components to benefit from the latest features, security enhancements, and bug fixes.

## References
- [OpenVAS Official Website](https://www.openvas.org/)
- [Greenbone Community Documentation](https://greenbone.github.io/docs/)
- [Greenbone GitHub Repository](https://github.com/greenbone)
- [Comprehensive Guide to OpenVAS](https://www.hackingarticles.in/comprehensive-guide-on-openvas/)
- [OpenVAS Vulnerability Scanning Tutorial](https://www.techrepublic.com/article/how-to-use-openvas-for-vulnerability-scanning/)

