## Overview
CrackMapExec (CME) is a popular post-exploitation tool designed to automate the assessment and penetration of large Active Directory (AD) networks. Originally created to simplify the process of network enumeration and credential validation, CME has evolved into a powerful tool that supports a variety of attack techniques, such as credential dumping, command execution, lateral movement, and more. CrackMapExec is widely used by penetration testers, red teamers, and security researchers to perform both offensive and defensive operations in Windows environments.

CrackMapExec leverages the SMB protocol to perform its operations, making it particularly effective for Windows network assessments and exploiting common misconfigurations.

## Features
- **Credential Validation:** Validates credentials across multiple hosts to identify reusable passwords and weak configurations.
- **Command Execution:** Executes commands and scripts remotely on multiple systems using valid credentials.
- **Lateral Movement:** Moves laterally across the network by leveraging valid credentials and executing payloads on target systems.
- **Credential Dumping:** Dumps credentials from memory using techniques such as Mimikatz, DCSync, and more.
- **Service and User Enumeration:** Enumerates services, users, groups, and shares on target systems.
- **Cross-Platform Support:** Runs on Unix-based systems (Linux, macOS) and Windows environments.
- **Modular Architecture:** Supports various modules for extending functionality and integrating with other tools.

## Website
- [CrackMapExec GitHub Repository](https://github.com/Porchetta-Industries/CrackMapExec)

## Installation

### On Unix-based systems (Linux/macOS):

1. **Install CrackMapExec via pip:**

   - First, ensure Python 3.x and pip are installed on your system. Then, install CME using pip:

```sh
python3 -m pip install pipx
pipx ensurepath
pipx install crackmapexec
```

2. **Install via GitHub:**

   - Clone the CrackMapExec repository from GitHub:

```sh
git clone https://github.com/Porchetta-Industries/CrackMapExec.git
cd CrackMapExec
```

   - Install the required dependencies:

```sh
python3 setup.py install
```

### On Windows:

1. **Install via pip:**

   - Ensure Python 3.x and pip are installed. Then, run:

```powershell
python -m pip install pipx
pipx ensurepath
pipx install crackmapexec
```

2. **Install via GitHub:**

   - Clone the CrackMapExec repository from GitHub:

```powershell
git clone https://github.com/Porchetta-Industries/CrackMapExec.git
cd CrackMapExec
```

   - Install the required dependencies:

```powershell
python setup.py install
```

## Basic Usage
CrackMapExec can be used for a wide range of post-exploitation tasks in Active Directory environments. Here are some basic commands and usage examples:

### Credential Validation
To validate a set of credentials across multiple hosts in a domain:

```sh
crackmapexec smb 192.168.1.0/24 -u username -p password
```

- **`smb 192.168.1.0/24`**: Specifies the SMB protocol and the target IP range.
- **`-u username -p password`**: Specifies the username and password for credential validation.

### Command Execution
To execute a command remotely on target systems:

```sh
crackmapexec smb 192.168.1.0/24 -u username -p password -x 'whoami'
```

- **`-x 'whoami'`**: Executes the `whoami` command on the target systems.

### Credential Dumping
To dump credentials from the memory of target systems:

```sh
crackmapexec smb 192.168.1.0/24 -u username -p password --mimikatz
```

- **`--mimikatz`**: Uses Mimikatz to dump credentials from memory.

### Lateral Movement
To move laterally across the network using valid credentials:

```sh
crackmapexec smb 192.168.1.0/24 -u username -p password -d domain --exec-method smbexec
```

- **`--exec-method smbexec`**: Specifies the execution method for lateral movement (in this case, SMBExec).

### Service Enumeration
To enumerate services running on the target systems:

```sh
crackmapexec smb 192.168.1.0/24 -u username -p password --shares
```

- **`--shares`**: Lists shared resources available on the target systems.

### User Enumeration
To enumerate domain users:

```sh
crackmapexec ldap 192.168.1.0/24 -u username -p password --users
```

- **`ldap`**: Specifies LDAP enumeration for domain users.

## Key Features and Options

### Credential Validation
- **Description:** Validates a set of credentials across multiple hosts to identify weak passwords, password reuse, and account configurations.
- **Usage:**
```sh
crackmapexec smb 192.168.1.0/24 -u username -p password
```

### Command Execution
- **Description:** Executes commands and scripts on remote systems using valid credentials for remote code execution.
- **Usage:**
```sh
crackmapexec smb 192.168.1.0/24 -u username -p password -x 'whoami'
```

### Credential Dumping
- **Description:** Dumps credentials from memory and the file system using various techniques, including Mimikatz.
- **Usage:**
```sh
crackmapexec smb 192.168.1.0/24 -u username -p password --mimikatz
```

### Lateral Movement
- **Description:** Facilitates lateral movement across a network using techniques like SMBExec, WMI, and DCOM.
- **Usage:**
```sh
crackmapexec smb 192.168.1.0/24 -u username -p password --exec-method smbexec
```

### Service and Share Enumeration
- **Description:** Enumerates services, users, groups, and shares on target systems to gather valuable information for further exploitation.
- **Usage:**
```sh
crackmapexec smb 192.168.1.0/24 -u username -p password --shares
```

### User and Group Enumeration
- **Description:** Enumerates domain users and groups to identify targets and assess network exposure.
- **Usage:**
```sh
crackmapexec ldap 192.168.1.0/24 -u username -p password --users
```

## Tools for Post-Exploitation and Offensive Security Using CrackMapExec

- **Active Directory Assessments:** Use CrackMapExec to validate credentials, enumerate users and groups, and identify potential attack vectors within Active Directory environments.
- **Command Execution and Lateral Movement:** Perform remote command execution and lateral movement to expand access across a compromised network.
- **Credential Harvesting and Dumping:** Extract credentials from memory and files to gain further access and exploit additional systems.
- **Service and Share Enumeration:** Discover network shares, services, and resources that can be exploited or used to pivot further into the network.
- **Automated Network Assessments:** Automate the process of assessing network security by leveraging CrackMapExec's modular architecture and powerful scripting capabilities.

## Best Practices
- **Use CrackMapExec Responsibly:** Always ensure that you have proper authorization before using CrackMapExec for offensive security tasks and post-exploitation activities.
- **Stay Within Legal Boundaries:** Be aware of the legal implications of using offensive security tools and ensure compliance with local laws and regulations.
- **Combine with Other Tools:** Use CrackMapExec alongside other post-exploitation tools like [[Mimikatz]], [[Empire]], and [[Metasploit]] for comprehensive assessments.
- **Regularly Update CrackMapExec:** Keep CrackMapExec up-to-date to benefit from the latest features, security enhancements, and bug fixes.
- **Analyze Results Carefully:** Review the output of CrackMapExec commands carefully to identify potential vulnerabilities, misconfigurations, and opportunities for further exploitation.

## References
- [CrackMapExec GitHub Repository](https://github.com/Porchetta-Industries/CrackMapExec)
- [CrackMapExec Documentation](https://github.com/Porchetta-Industries/CrackMapExec/wiki)
- [CrackMapExec Tutorial for Active Directory Penetration Testing](https://www.hackingarticles.in/comprehensive-guide-on-crackmapexec-for-active-directory-penetration-testing/)
- [CrackMapExec Cheat Sheet](https://highon.coffee/blog/crackmapexec-cheat-sheet/)
- [CrackMapExec: Automating Post-Exploitation](https://null-byte.wonderhowto.com/how-to/use-crackmapexec-automate-post-exploitation-0198254/)

