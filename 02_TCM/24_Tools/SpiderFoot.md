# SpiderFoot

## Overview
**SpiderFoot** is an open-source, automated intelligence-gathering tool used for reconnaissance and OSINT (Open Source Intelligence) investigations. It is designed to collect and analyze information about a target from various public sources, providing a comprehensive view of its digital footprint. SpiderFoot can perform a wide range of tasks, such as discovering domain names, IP addresses, email addresses, social media profiles, and other critical data that may be publicly accessible. It is widely used by penetration testers, security researchers, and threat intelligence analysts to identify vulnerabilities, gather threat intelligence, and assess the exposure of a target.

SpiderFoot integrates with numerous APIs and data sources, including search engines, WHOIS databases, social media, dark web services, and more, making it a versatile tool for OSINT investigations and cybersecurity assessments.

## Features
- **Automated OSINT Collection:** Automates the process of gathering information from various public data sources and APIs.
- **Modular Architecture:** Offers over 200 modules to perform different types of reconnaissance tasks, such as domain discovery, IP address geolocation, social media analysis, and more.
- **Web-Based GUI and CLI:** Provides both a web-based graphical user interface and a command-line interface for flexibility in use.
- **Customizable Scans:** Allows users to configure scans with specific modules, target parameters, and data sources for tailored investigations.
- **Integration with APIs and Data Sources:** Supports integration with a wide range of APIs and data sources, such as Shodan, Have I Been Pwned, VirusTotal, and more.
- **Cross-Platform Compatibility:** Available for Unix-based systems (Linux, macOS) and Windows environments.

## Website
- [SpiderFoot Official Website](https://www.spiderfoot.net/)

## Installation

### On Unix-based systems (Linux/macOS):

1. **Install SpiderFoot via GitHub:**

   - Clone the SpiderFoot repository from GitHub:

```sh
git clone https://github.com/smicallef/spiderfoot.git
cd spiderfoot
```

   - Install the required dependencies:

```sh
pip3 install -r requirements.txt
```

2. **Run SpiderFoot:**

   - Start SpiderFoot with the following command:

```sh
python3 sf.py
```

### On Windows:

1. **Install Python and Git:**

   - Ensure Python and Git are installed on your system.

2. **Install SpiderFoot via GitHub:**

   - Clone the SpiderFoot repository from GitHub using Git Bash:

```bash
git clone https://github.com/smicallef/spiderfoot.git
cd spiderfoot
```

   - Install the required dependencies using pip:

```bash
pip install -r requirements.txt
```

3. **Run SpiderFoot:**

   - Open Command Prompt, navigate to the SpiderFoot directory, and run:

```cmd
python sf.py
```

## Basic Usage
SpiderFoot provides both a web-based GUI and a command-line interface (CLI) for conducting reconnaissance and OSINT investigations. Here are some common commands and usage examples:

### Running SpiderFoot with the Web GUI
To run SpiderFoot with the web-based graphical user interface:

1. **Start SpiderFoot:**

```sh
python3 sf.py
```

2. **Access the Web GUI:**

   - Open a web browser and navigate to `http://127.0.0.1:5001` to access the SpiderFoot GUI.

3. **Create a New Scan:**

   - Click on **"New Scan"** and enter the target information (e.g., domain, IP address, email address).
   - Configure the scan settings by selecting the modules and data sources you want to use.

4. **Run the Scan:**

   - Click **"Start Scan"** to begin the OSINT investigation.
   - Monitor the progress and view results in real-time from the GUI dashboard.

### Running SpiderFoot from the Command Line
To run SpiderFoot using the command-line interface:

1. **Run a Simple Scan:**

```sh
python3 sf.py -s example.com -o output.html
```

   - **`-s example.com`**: Specifies the target (e.g., domain name, IP address).
   - **`-o output.html`**: Specifies the output file format and filename (HTML in this example).

2. **Running a Scan with Specific Modules:**

```sh
python3 sf.py -s example.com -m sfp_dnsresolve,sfp_shodan -o output.csv
```

   - **`-m sfp_dnsresolve,sfp_shodan`**: Specifies specific modules to use for the scan.
   - **`-o output.csv`**: Specifies the output file format and filename (CSV in this example).

### Configuring API Keys
To use API keys for enhanced data gathering, add them in the SpiderFoot GUI or CLI:

1. **Add API Keys via Web GUI:**

   - Navigate to **"Settings"** > **"API Keys"** and enter your API keys for services like Shodan, Have I Been Pwned, and VirusTotal.

2. **Add API Keys via Command Line:**

```sh
python3 sf.py --setkey SHODAN_API <YOUR_SHODAN_API_KEY>
 ```

   - **`--setkey SHODAN_API <YOUR_SHODAN_API_KEY>`**: Adds the Shodan API key for use with Shodan-related modules.

### Viewing and Exporting Scan Results
To view and export scan results:

1. **View Results in Web GUI:**

   - Go to the **"Results"** tab in the SpiderFoot GUI to view scan results, including discovered domains, emails, IP addresses, and more.

2. **Export Results:**

   - Click **"Export"** to save the results in various formats (HTML, CSV, JSON).

## Key Features and Commands

### Automated OSINT Collection
- **Description:** Automates the process of gathering information from various public data sources and APIs, providing a comprehensive view of a target's digital footprint.
- **Usage:**
```sh
python3 sf.py -s example.com -o output.html
```

### Modular Architecture
- **Description:** Offers over 200 modules for different types of reconnaissance tasks, such as domain discovery, IP address geolocation, social media analysis, and more.
- **Usage:**
```sh
python3 sf.py -s example.com -m sfp_dnsresolve,sfp_shodan -o output.csv
```

### Web-Based GUI and CLI
- **Description:** Provides both a web-based GUI and a command-line interface for flexibility in use, allowing users to choose their preferred method of operation.
- **Usage:**
  - **Web GUI:** Start SpiderFoot with `python3 sf.py` and access via `http://127.0.0.1:5001`.
  - **CLI:** Use command-line options for targeted scans and automated tasks.

### Customizable Scans
- **Description:** Allows users to configure scans with specific modules, target parameters, and data sources for tailored investigations.
- **Usage:**
```sh
python3 sf.py -s example.com -m sfp_dnsresolve,sfp_shodan -o output.csv
```

### Integration with APIs and Data Sources
- **Description:** Supports integration with a wide range of APIs and data sources, enhancing the depth and breadth of OSINT collection.
- **Usage:**
```sh
python3 sf.py --setkey SHODAN_API <YOUR_SHODAN_API_KEY>
```

### Exporting Results
- **Description:** Exports gathered data to various formats (HTML, CSV, JSON) for reporting and further analysis.
- **Usage:**
```sh
python3 sf.py -s example.com -o output.json
```

## Tools for Information Gathering and OSINT Using SpiderFoot

- **OSINT Investigations:** Use SpiderFoot to gather open-source intelligence on domains, IP addresses, email addresses, and more, uncovering valuable data for further analysis.
- **Cyber Threat Intelligence:** Build comprehensive maps of threat actors, campaigns, and associated infrastructure to understand attack patterns and develop mitigation strategies.
- **Network Reconnaissance:** Identify and map network assets, including domains, subdomains, IP addresses, and servers, to identify potential entry points and vulnerabilities.
- **Incident Response:** Analyze data from compromised systems to identify the spread and impact of an incident by mapping related entities and domains.
- **Social Engineering:** Research organizations and individuals to gather information that can be used in social engineering attacks or phishing campaigns.

## Best Practices
- **Use SpiderFoot Responsibly:** Always ensure that you have proper authorization before using SpiderFoot for reconnaissance and information gathering tasks.
- **Stay Within Legal Boundaries:** Be aware of the legal implications of using SpiderFoot and ensure compliance with local laws and regulations.
- **Combine with Other Tools:** Use SpiderFoot alongside other information gathering tools like [[Maltego]], [[theHarvester]], and [[Shodan]] for comprehensive assessments.
- **Regularly Update SpiderFoot:** Keep SpiderFoot up-to-date to benefit from the latest features, security enhancements, and bug fixes.
- **Analyze Results Carefully:** Review the output of SpiderFoot carefully to identify potential vulnerabilities, misconfigurations, and opportunities for further investigation.

## References
- [SpiderFoot Official Website](https://www.spiderfoot.net/)
- [SpiderFoot GitHub Repository](https://github.com/smicallef/spiderfoot)
- [SpiderFoot Documentation](https://www.spiderfoot.net/documentation/)
- [SpiderFoot Tutorial for OSINT Gathering](https://www.hackingarticles.in/spiderfoot-tutorial-for-osint-gathering/)
- [SpiderFoot Cheat Sheet](https://highon.coffee/blog/spiderfoot-cheat-sheet/)

