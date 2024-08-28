Fingerprinting Organizations with Collected Archives)
## Overview
**FOCA** (Fingerprinting Organizations with Collected Archives) is a powerful information gathering and reconnaissance tool used primarily for metadata extraction from publicly available documents. It is widely utilized by penetration testers, ethical hackers, and security researchers to uncover sensitive information such as usernames, email addresses, software versions, server names, and even internal IP addresses. FOCA can analyze files like PDFs, Microsoft Office documents, Open Office files, and others that are accessible on the internet, extracting metadata that can be valuable for understanding an organization's infrastructure and identifying potential security weaknesses.

FOCA can perform various types of information gathering, such as domain and subdomain enumeration, file retrieval from search engines, and analysis of metadata for potentially exploitable data.

## Features
- **Metadata Extraction:** Extracts metadata from documents to uncover hidden information about an organization.
- **File Analysis:** Analyzes various file formats including PDFs, DOCX, PPTX, XLSX, and more.
- **Domain and Subdomain Enumeration:** Enumerates domains and subdomains associated with the target organization.
- **Network Mapping:** Maps internal networks and identifies IP addresses, servers, and software versions.
- **Automated Search Engine Queries:** Uses search engines to find documents and information related to the target.
- **Cross-Platform Support:** Primarily a Windows application, but can be run on Unix-based systems using virtualization or emulation tools.

## Website
- [FOCA GitHub Repository](https://github.com/ElevenPaths/FOCA)
- [FOCA Official Website](https://www.elevenpaths.com/labstools/foca/index.html)

## Installation

### On Windows:

1. **Download FOCA:**

   - Download the FOCA installer from the [official FOCA page](https://www.elevenpaths.com/labstools/foca/index.html).

2. **Install FOCA:**

   - Run the downloaded installer and follow the on-screen instructions to complete the installation.

3. **Run FOCA:**

   - Once installed, launch FOCA from the Start Menu or desktop shortcut.

### On Unix-based systems (Linux/macOS):

1. **Using Virtualization or Emulation:**

   - Since FOCA is primarily a Windows application, you can run it on Unix-based systems using virtualization tools like VMware or VirtualBox, or using Wine.

2. **Install Wine (if using Wine):**

   - Install Wine using your package manager:

   - **On Debian-based systems:**

```sh
sudo apt-get install wine
```

   - **On macOS using Homebrew:**

```sh
brew install --cask wine-stable
```

3. **Run FOCA Using Wine:**

   - Download the FOCA installer and run it using Wine:

```sh
wine FOCA_setup.exe
```

## Basic Usage
FOCA can perform various information-gathering and reconnaissance tasks. Here are some common commands and usage examples:

### Metadata Extraction from Documents
To extract metadata from documents found online:

1. **Launch FOCA and Create a New Project:**

   - Open FOCA and click on **"New Project"** to create a new project for the target organization.

2. **Set the Target Domain:**

   - Enter the target domain you want to analyze in the "Domain" field.

3. **Search and Download Documents:**

   - Click on **"Search All"** to search for documents related to the target domain across multiple search engines.
   - FOCA will automatically download and store the documents it finds.

4. **Extract Metadata:**

   - After downloading the documents, click on **"Analyze"** to extract metadata from the documents.
   - FOCA will display the extracted metadata, including usernames, software versions, file paths, and other sensitive information.

### Domain and Subdomain Enumeration
To enumerate domains and subdomains associated with the target:

1. **Run a DNS Search:**

   - In the project, navigate to **"Domains"** and click on **"DNS Search"**.
   - FOCA will perform DNS enumeration to identify subdomains and related information.

2. **Analyze DNS Results:**

   - Review the results to identify potential subdomains and IP addresses.

### Network Mapping
To map internal networks and identify IP addresses:

1. **Identify IP Addresses:**

   - After metadata extraction, FOCA will list internal IP addresses that it discovers in the documents.
   
2. **Map the Network:**

   - Use the IP addresses to map the internal network and identify servers, software versions, and other infrastructure details.

### Automated Search Engine Queries
To use FOCA's automated search engine capabilities:

1. **Configure Search Engines:**

   - In FOCA, configure the search engines you want to use under **"Options"**.
   
2. **Run Search Queries:**

   - Click **"Search All"** to run queries across all configured search engines for the target domain.

### Analyzing Results
To analyze the results and extract valuable information:

1. **Review Metadata:**

   - Go through the metadata extracted from documents to identify usernames, emails, software versions, and other sensitive information.

2. **Identify Security Weaknesses:**

   - Look for outdated software, internal server names, and IP addresses that could indicate potential security weaknesses.

## Key Features and Commands

### Metadata Extraction
- **Description:** Extracts metadata from documents to uncover hidden information such as usernames, email addresses, software versions, and more.
- **Usage:**
  - Search for documents using **"Search All"** and extract metadata using **"Analyze"**.

### Domain and Subdomain Enumeration
- **Description:** Identifies domains and subdomains associated with a target organization through DNS enumeration.
- **Usage:**
  - Use the **"DNS Search"** feature in the **"Domains"** tab to enumerate domains and subdomains.

### Network Mapping
- **Description:** Maps internal networks and identifies IP addresses, servers, and software versions based on extracted metadata.
- **Usage:**
  - Analyze extracted metadata for IP addresses and map the internal network.

### Automated Search Engine Queries
- **Description:** Uses search engines to find documents and information related to the target organization.
- **Usage:**
  - Run queries using the **"Search All"** feature after configuring search engines in **"Options"**.

### Analyzing Security Posture
- **Description:** Helps analyze the security posture of an organization by uncovering potentially sensitive information that could be used in attacks.
- **Usage:**
  - Review extracted metadata and DNS results for security weaknesses.

## Tools for Information Gathering and Offensive Security Using FOCA

- **Information Gathering:** Use FOCA to gather valuable information about a target organization, including domains, subdomains, internal IP addresses, and more.
- **Metadata Analysis:** Extract and analyze metadata from publicly accessible documents to uncover sensitive information about a target.
- **Network Reconnaissance:** Map the target’s network infrastructure by analyzing IP addresses, server names, and software versions found in documents.
- **Security Assessment:** Identify potential security weaknesses by discovering outdated software, misconfigured servers, and exposed sensitive data.
- **Compliance Auditing:** Ensure that organizations are adhering to data protection policies by auditing metadata in publicly accessible documents.

## Best Practices
- **Use FOCA Responsibly:** Always ensure that you have proper authorization before using FOCA for reconnaissance and information gathering tasks.
- **Stay Within Legal Boundaries:** Be aware of the legal implications of using FOCA and ensure compliance with local laws and regulations.
- **Combine with Other Tools:** Use FOCA alongside other information gathering tools like [[Maltego]], [[theHarvester]], and [[Recon-ng]] for comprehensive assessments.
- **Regularly Update FOCA:** Keep FOCA up-to-date to benefit from the latest features, security enhancements, and bug fixes.
- **Analyze Results Carefully:** Review the output of FOCA carefully to identify potential vulnerabilities, misconfigurations, and opportunities for further exploitation.

## References
- [FOCA GitHub Repository](https://github.com/ElevenPaths/FOCA)
- [FOCA Official Website](https://www.elevenpaths.com/labstools/foca/index.html)
- [Using FOCA for Metadata Extraction](https://null-byte.wonderhowto.com/how-to/use-foca-extract-metadata-from-public-documents-0176668/)
- [FOCA Tutorial for Information Gathering](https://www.hackingarticles.in/foca-tutorial-information-gathering/)
- [FOCA Cheat Sheet](https://highon.coffee/blog/foca-cheat-sheet/)

