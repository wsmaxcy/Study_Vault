## Overview
Cobalt Strike is a commercial, adversary simulation software designed for red team operations and advanced penetration testing. It provides a post-exploitation agent (known as "Beacon") and a framework for developing and executing payloads, simulating advanced threat actor techniques, and performing covert operations. Cobalt Strike is widely used by penetration testers and red teamers to test network defenses, assess organizational security posture, and simulate real-world attacks.

## Features
- **Beacon Payload:** A powerful and flexible post-exploitation agent that supports command execution, keylogging, file transfer, pivoting, and more.
- **Covert Communication:** Supports multiple communication channels (HTTP, HTTPS, DNS, SMB) for stealthy command and control (C2).
- **Post-Exploitation Modules:** Includes a variety of built-in modules for privilege escalation, credential dumping, lateral movement, and persistence.
- **Collaboration:** Allows multiple users to work together in a red team operation, sharing sessions and coordinating actions in real-time.
- **Threat Emulation:** Simulates advanced adversary tactics, techniques, and procedures (TTPs) to test detection and response capabilities.
- **Scripting and Extensibility:** Supports custom scripts in Cobalt Strike's Aggressor Script language to automate tasks and create custom attack workflows.

## Website
- [Cobalt Strike Official Website](https://www.cobaltstrike.com/)

## Installation

### System Requirements
- **Operating System:** Windows, Linux, or macOS.
- **Java Runtime Environment (JRE):** Cobalt Strike requires Java to run. Install JRE 8 or later.

### Installation Steps
1. **Download Cobalt Strike:**
   - Download the Cobalt Strike installer from the [Cobalt Strike Download Page](https://www.cobaltstrike.com/). This requires an active license.

2. **Extract the Installer:**
   - Extract the downloaded `.tgz` file to a directory of your choice.

3. **Run the Team Server:**
   - Start the Cobalt Strike team server on a machine accessible to red team operators:
   ```sh
   ./teamserver <IP address> <password>
   ```
   - **`<IP address>`**: The IP address of the server.
   - **`<password>`**: The password to authenticate clients to the team server.

4. **Connect the Client:**
   - Run the Cobalt Strike client and connect to the team server:
   ```sh
   ./cobaltstrike
   ```
   - Enter the IP address of the team server, the user name, and the password set during the server start.

## Basic Usage
Cobalt Strike is typically used through its graphical user interface (GUI), but many actions can be scripted. Here are some common tasks and usage examples:

### Establishing a Beacon
1. **Generate a Beacon Payload:**
   - Go to **Attacks** > **Packages** > **Windows Executable (S)** to generate a Stageless Beacon.
   - Choose the desired communication method (e.g., HTTP, HTTPS, DNS).

2. **Deliver the Payload:**
   - Use social engineering, phishing, or another method to deliver the generated payload to the target.

3. **Manage the Beacon:**
   - Once the Beacon is active, it will appear under **View** > **Beacons**.
   - Right-click the Beacon to interact and run post-exploitation commands.

### Post-Exploitation Activities
- **Privilege Escalation:**
  - Use built-in exploits to escalate privileges on the compromised host. Right-click on the Beacon and select **Explore** > **Elevate**.

- **Credential Dumping:**
  - Dump credentials from memory using built-in tools like Mimikatz. Right-click the Beacon and choose **Credentials** > **Mimikatz**.

- **Lateral Movement:**
  - Move laterally within the network using tools such as PsExec or WMI. Right-click the Beacon and select **Pivoting** > **PsExec** or **WMI**.

- **Persistence:**
  - Install persistent mechanisms to maintain access to the compromised system. Right-click the Beacon and choose **Access** > **Persistence**.

### C2 Communications and Evasion
- **Configure C2 Channels:**
  - Use different communication channels (HTTP, HTTPS, DNS, SMB) to evade detection and maintain a covert presence. Go to **Cobalt Strike** > **Listeners** and configure a new listener with the desired C2 method.

- **Use Sleep and Jitter:**
  - Adjust Beacon's sleep time and jitter to blend in with normal network traffic. Right-click on the Beacon and select **Sleep** to set these parameters.

### Collaboration and Teamwork
- **Collaborate with Team Members:**
  - Share sessions and actions with other team members for coordinated red team operations.

- **Use the Aggressor Script:**
  - Write custom scripts to automate repetitive tasks or create new attack workflows. Scripts can be loaded via **Cobalt Strike** > **Scripts**.

## Key Features and Modules

### Beacon
- **Description:** A post-exploitation agent that supports multiple C2 channels, evasion techniques, and a wide range of post-exploitation capabilities.
- **Usage:**
  - Deploy Beacons via phishing, web delivery, or file exploits, and use them for remote access, data exfiltration, and lateral movement.

### Malleable C2 Profiles
- **Description:** Allows red team operators to change C2 traffic patterns to mimic different types of malware or normal web traffic.
- **Usage:**
  - Load custom profiles under **Cobalt Strike** > **Listeners** > **Edit** to evade detection.

### Aggressor Script
- **Description:** A scripting language for Cobalt Strike that allows users to automate tasks and extend functionality.
- **Usage:**
  - Create `.cna` files and load them under **Cobalt Strike** > **Scripts** to enhance workflows.

### Collaboration Features
- **Description:** Support for multiple users to collaborate in real-time on a single engagement.
- **Usage:**
  - Multiple team members can connect to the same team server, share information, and coordinate attacks through the shared interface.

### Post-Exploitation Modules
- **Description:** Built-in modules for common post-exploitation tasks like privilege escalation, credential dumping, and lateral movement.
- **Usage:**
  - Right-click on an active Beacon and choose from the list of post-exploitation options to run commands on compromised hosts.

## Tools for Red Team Operations Using Cobalt Strike

- **Advanced Threat Simulation:** Simulate advanced threat actor tactics to test an organization's detection and response capabilities.
- **Post-Exploitation Framework:** Use Beacons and modules for in-depth post-exploitation activities, including data exfiltration and network pivoting.
- **Covert Command and Control:** Maintain covert communication channels to avoid detection by blue team defenses.
- **Team Collaboration:** Enable multiple red team members to collaborate on a single operation in real-time, enhancing the efficiency and coordination of attacks.

## Best Practices
- **Use in Authorized Environments:** Always ensure that you have proper authorization before using Cobalt Strike in an environment, as it is a powerful tool that can cause significant disruption.
- **Practice Good OpSec:** Utilize evasion techniques like sleep, jitter, and malleable C2 profiles to avoid detection and maintain operational security.
- **Keep Cobalt Strike Updated:** Regularly update Cobalt Strike to benefit from the latest features, security enhancements, and bug fixes.
- **Combine with Other Tools:** Use Cobalt Strike alongside other red team tools like [[Metasploit]], [[PowerShell Empire]], and [[Responder]] for comprehensive assessments.
- **Use Aggressor Scripts Wisely:** Develop and use Aggressor scripts to automate tasks and enhance functionality, but be mindful of operational security.

## References
- [Cobalt Strike Official Website](https://www.cobaltstrike.com/)
- [Cobalt Strike User Guide](https://www.cobaltstrike.com/userguide/)
- [Aggressor Script Documentation](https://www.cobaltstrike.com/aggressor-script/)
- [Red Teaming with Cobalt Strike](https://www.harmj0y.net/blog/redteaming/red-teaming-tips-techniques-part-1/)

