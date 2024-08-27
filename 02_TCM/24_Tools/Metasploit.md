## Overview
Metasploit is a powerful and versatile penetration testing framework used for developing and executing exploit code against a remote target machine. It is widely used by security professionals to identify, validate, and exploit security vulnerabilities in systems and applications.

## Features
- **Exploitation Framework:** Extensive library of exploits for various platforms.
- **Payloads:** Customizable payloads for delivering exploit code.
- **Auxiliary Modules:** Modules for scanning, fuzzing, and other network tasks.
- **Post-Exploitation:** Tools for post-exploitation, including pivoting and privilege escalation.
- **Metasploit Console:** Interactive shell for running and managing exploits and payloads.
- **Metasploit Community and Pro:** Enhanced versions with additional features and GUI.

## Website
- [Metasploit](https://www.metasploit.com/)

## Installation

### On Unix-based systems:
1. **Install Metasploit:**
```sh
curl https://raw.githubusercontent.com/rapid7/metasploit-framework/master/msfupdate | bash
```

2. **Run Metasploit:**
```sh
msfconsole
```

### On Windows:
1. **Download Installer:**
   - Download the Metasploit installer from the [Metasploit Download Page](https://www.metasploit.com/download).

2. **Run Installer:**
   - Follow the installation instructions to install Metasploit.

3. **Run Metasploit:**
   - Launch Metasploit from the Start menu.

## Basic Usage
Metasploit is typically run from the command line using `msfconsole`. Here are some common commands and workflows:

### Starting Metasploit
1. **Open Metasploit Console:**
```sh
msfconsole
```

### Searching for Exploits
1. **Search Exploits:**
```sh
search name:exploit_name
```

### Using an Exploit
1. **Select Exploit:**
```sh
use exploit/path/to/exploit
```

2. **Set Options:**
```sh
set RHOST target_ip
set RPORT target_port
```

3. **Set Payload:**
```sh
set PAYLOAD payload_name
```

4. **Run Exploit:**
```sh
exploit
```

### Auxiliary Modules
1. **Search Auxiliary Modules:**
```sh
search auxiliary
```

2. **Use Auxiliary Module:**
```sh
use auxiliary/path/to/module
```

3. **Set Options:**
```sh
set RHOST target_ip
```

4. **Run Module:**
```sh
run
```

### Post-Exploitation
1. **Meterpreter Sessions:**
   - After successfully exploiting a target, use Meterpreter for post-exploitation tasks.

2. **Interact with Session:**
```sh
sessions -i session_id
```

3. **List Sessions:**
```sh
sessions -l
```

4. **Post-Exploitation Commands:**
   - Use commands like `sysinfo`, `hashdump`, and `shell` within a Meterpreter session.

## Best Practices
- **Regular Updates:** Keep Metasploit and its modules updated to benefit from the latest exploits and features.
- **Use Appropriate Payloads:** Choose payloads that are suitable for the target environment.
- **Manage Sessions Carefully:** Ensure proper session management to avoid detection and maintain control over exploited systems.
- **Combine with Other Tools:** Use Metasploit in conjunction with other tools like [[Nmap.md|Nmap]], [[Burp Suite]], and [[WhatWeb.md|WhatWeb]] for comprehensive assessments.

## References
- [Metasploit Official Documentation](https://docs.metasploit.com/)
- [Metasploit Unleashed](https://www.offensive-security.com/metasploit-unleashed/)
- [Rapid7 Metasploit Documentation](https://docs.rapid7.com/metasploit/)

