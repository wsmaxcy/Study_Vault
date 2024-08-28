## Overview
**Recon-ng** is a full-featured web reconnaissance framework written in Python, designed for open-source intelligence (OSINT) gathering and reconnaissance. It provides a modular architecture that allows users to easily add, remove, and configure modules to perform various tasks, such as domain and IP address reconnaissance, vulnerability identification, and social engineering research. Recon-ng is widely used by penetration testers, security researchers, and ethical hackers to automate the process of collecting and analyzing publicly available information about targets.

Recon-ng comes with a variety of built-in modules and can be extended with custom scripts, making it a versatile tool for conducting thorough reconnaissance during the initial stages of a penetration test or security assessment.

## Features
- **Modular Architecture:** Supports a wide range of modules for domain reconnaissance, IP address analysis, social media harvesting, and more.
- **API Integration:** Integrates with various APIs to gather information from sources like WHOIS, Shodan, Have I Been Pwned, and more.
- **Database Support:** Stores collected data in a SQLite database for easy access, reporting, and analysis.
- **Command-Line Interface:** Offers a robust command-line interface that mimics the look and feel of a Metasploit-like framework.
- **Extensible with Custom Modules:** Allows users to develop and add custom modules for specialized tasks.
- **Cross-Platform Compatibility:** Available for Unix-based systems (Linux, macOS) and Windows environments.

## Website
- [Recon-ng GitHub Repository](https://github.com/lanmaster53/recon-ng)

## Installation

### On Unix-based systems (Linux/macOS):

1. **Install Recon-ng via Package Manager:**

   - **On Debian-based systems:**

```sh
sudo apt-get install recon-ng
```

   - **On macOS using Homebrew:**

```sh
brew install recon-ng
```

2. **Install via GitHub:**

   - Clone the Recon-ng repository from GitHub:

```sh
git clone https://github.com/lanmaster53/recon-ng.git
cd recon-ng
```

   - Install the required dependencies:

```sh
pip3 install -r REQUIREMENTS
```

3. **Run Recon-ng:**

   - Launch Recon-ng by running:

```sh
python3 recon-ng
```

### On Windows:

1. **Install Python and Git:**

   - Ensure Python and Git are installed on your system.

2. **Install Recon-ng via GitHub:**

   - Clone the Recon-ng repository from GitHub using Git Bash:

```bash
git clone https://github.com/lanmaster53/recon-ng.git
cd recon-ng
```

   - Install the required dependencies using pip:

```bash
pip install -r REQUIREMENTS
```

3. **Run Recon-ng:**

   - Open Command Prompt, navigate to the Recon-ng directory, and run:

```cmd
python recon-ng
```

## Basic Usage
Recon-ng provides a variety of modules and commands for gathering information and performing reconnaissance. Here are some common commands and usage examples:

### Starting Recon-ng
To start Recon-ng and initialize a new workspace:

```sh
recon-ng
```

- This command launches the Recon-ng framework.

### Creating and Using a Workspace
To create a new workspace and switch to it:

```sh
workspaces create example_workspace
workspaces select example_workspace
```

- **`workspaces create example_workspace`**: Creates a new workspace named `example_workspace`.
- **`workspaces select example_workspace`**: Switches to the newly created workspace.

### Adding a Target Domain
To add a target domain to your current workspace:

```sh
add domains example.com
```

- **`add domains example.com`**: Adds `example.com` as a target domain to the workspace.

### Running a Module
To run a module, such as `recon/domains-hosts/google_site_web`, to find hosts related to a domain:

```sh
modules load recon/domains-hosts/google_site_web
run
```

- **`modules load recon/domains-hosts/google_site_web`**: Loads the module for finding hosts via Google Site.
- **`run`**: Executes the loaded module.

### Using API Keys
To use API keys for enhanced data gathering, add them to Recon-ng:

```sh
keys add shodan_api <YOUR_SHODAN_API_KEY>
```

- **`keys add shodan_api <YOUR_SHODAN_API_KEY>`**: Adds the Shodan API key for use with Shodan-related modules.

### Viewing and Exporting Collected Data
To view collected data and export it for reporting:

```sh
show hosts
export json /path/to/export.json
```

- **`show hosts`**: Displays all hosts collected in the workspace.
- **`export json /path/to/export.json`**: Exports the collected data to a JSON file.

### Installing Additional Modules
To install additional modules directly from the Recon-ng interface:

```sh
marketplace install recon/hosts-hosts/shodan_ip
```

- **`marketplace install recon/hosts-hosts/shodan_ip`**: Installs the Shodan IP module from the marketplace.

## Key Features and Commands

### Modular Architecture
- **Description:** Supports a wide range of modules for tasks such as domain reconnaissance, IP address analysis, and social media harvesting.
- **Usage:**
```sh
modules load recon/domains-hosts/google_site_web
run
```

### API Integration
- **Description:** Integrates with various APIs (Shodan, WHOIS, Have I Been Pwned, etc.) to enhance data gathering capabilities.
- **Usage:**
```sh
keys add shodan_api <YOUR_SHODAN_API_KEY>
modules load recon/hosts-hosts/shodan_ip
run
```

### Database Support
- **Description:** Stores collected data in a SQLite database for easy access, reporting, and analysis.
- **Usage:**
```sh
show hosts
export json /path/to/export.json
```

### Command-Line Interface
- **Description:** Offers a robust command-line interface that mimics the look and feel of a Metasploit-like framework, making it familiar for many users.
- **Usage:**
```sh
recon-ng
workspaces create example_workspace
add domains example.com
```

### Extensible with Custom Modules
- **Description:** Allows users to develop and add custom modules for specialized tasks, enhancing Recon-ng’s versatility.
- **Usage:**
```sh
marketplace search custom_module_name
marketplace install custom_module_name
```

### Installing and Using Modules from the Marketplace
- **Description:** Provides access to a marketplace of modules that can be installed and used directly within the framework.
- **Usage:**
```sh
marketplace search shodan
marketplace install recon/hosts-hosts/shodan_ip
```

## Tools for Information Gathering and Reconnaissance Using Recon-ng

- **OSINT Investigations:** Use Recon-ng to gather open-source intelligence on domains, IP addresses, email addresses, and more, uncovering valuable data for further analysis.
- **Cyber Threat Intelligence:** Build comprehensive maps of threat actors, campaigns, and associated infrastructure to understand attack patterns and develop mitigation strategies.
- **Network Reconnaissance:** Identify and map network assets, including domains, subdomains, IP addresses, and servers, to identify potential entry points and vulnerabilities.
- **Social Engineering:** Research organizations and individuals to gather information that can be used in social engineering attacks or phishing campaigns.
- **Incident Response:** Analyze data from compromised systems to identify the spread and impact of an incident by mapping related entities and domains.

## Best Practices
- **Use Recon-ng Responsibly:** Always ensure that you have proper authorization before using Recon-ng for reconnaissance and information gathering tasks.
- **Stay Within Legal Boundaries:** Be aware of the legal implications of using Recon-ng and ensure compliance with local laws and regulations.
- **Combine with Other Tools:** Use Recon-ng alongside other information gathering tools like [[Maltego]], [[theHarvester]], and [[Shodan]] for comprehensive assessments.
- **Regularly Update Recon-ng:** Keep Recon-ng up-to-date to benefit from the latest features, security enhancements, and bug fixes.
- **Analyze Results Carefully:** Review the output of Recon-ng carefully to identify potential vulnerabilities, misconfigurations, and opportunities for further investigation.

## References
- [Recon-ng GitHub Repository](https://github.com/lanmaster53/recon-ng)
- [Recon-ng Documentation](https://github.com/lanmaster53/recon-ng/blob/master/README.md)
- [Recon-ng Tutorial for OSINT Gathering](https://www.hackingarticles.in/recon-ng-tutorial-for-osint-gathering/)
- [Recon-ng Cheat Sheet](https://highon.coffee/blog/recon-ng-cheat-sheet/)
- [Using Recon-ng for Cyber Reconnaissance](https://null-byte.wonderhowto.com/how-to/use-recon-ng-for-cyber-reconnaissance-0197764/)

