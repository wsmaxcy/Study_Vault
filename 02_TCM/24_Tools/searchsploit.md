## Overview
SearchSploit is a command-line search tool for Exploit-DB, which allows you to quickly search through the Exploit Database archive. It is part of the Exploit-DB repository and is included in the Kali Linux distribution. SearchSploit makes it easy to find exploits and shellcode that can be used during penetration tests and security assessments.

## Features
- **Offline Searching:** Allows searching of the Exploit-DB archive offline.
- **Extensive Database:** Access to a vast collection of exploits, shellcode, and proof-of-concepts.
- **Easy to Use:** Simple command-line interface for quick searches.
- **Detailed Output:** Provides detailed information and links to exploit code.

## Website
- [Exploit-DB](https://www.exploit-db.com/)
- [SearchSploit GitHub Repository](https://github.com/offensive-security/exploitdb)

## Installation

### On Unix-based systems (Linux/macOS):
1. **Included in Kali Linux:**
   - SearchSploit is pre-installed in Kali Linux.

2. **Manual Installation:**
   ```sh
   git clone https://github.com/offensive-security/exploitdb.git /opt/exploitdb
   ln -sf /opt/exploitdb/searchsploit /usr/local/bin/searchsploit
   ```

### On Windows:
1. **Using Windows Subsystem for Linux (WSL):**
   - Install a Linux distribution from the Microsoft Store (e.g., Ubuntu).
   - Follow the Unix-based system installation steps within the WSL terminal.

## Basic Usage
SearchSploit is run from the command line. Here are some common commands and usage examples:

### Search for Exploits
To search for exploits related to a keyword:
```sh
searchsploit keyword
```

### View Exploit Details
To view detailed information about a specific exploit:
```sh
searchsploit -x exploit/path
```

### Update Exploit Database
To update the local exploit database:
```sh
searchsploit -u
```

### Search by CVE
To search for exploits by CVE number:
```sh
searchsploit CVE-YYYY-XXXX
```

### Practical Examples

#### Searching for Apache Exploits
To search for all exploits related to Apache:
```sh
searchsploit apache
```

#### Viewing an Exploit
To view the details of a specific exploit:
```sh
searchsploit -x exploits/webapps/12345.txt
```

#### Updating the Exploit Database
To ensure you have the latest exploits:
```sh
searchsploit -u
```

## Advanced Options
SearchSploit offers several advanced options for more specific use cases:

### Save Output to a File
To save the search results to a file:
```sh
searchsploit keyword -w > output.txt
```

### Exclude Results
To exclude certain terms from the search results:
```sh
searchsploit keyword -e excluded_term
```

### Case-Insensitive Search
To perform a case-insensitive search:
```sh
searchsploit -i keyword
```

## Best Practices
- **Regular Updates:** Regularly update the exploit database to access the latest exploits.
- **Verify Exploits:** Always verify the exploit code and its impact in a controlled environment before using it on live systems.
- **Use Ethically:** Ensure that exploits are used ethically and legally, with appropriate permissions.
- **Combine with Other Tools:** Use SearchSploit in combination with other tools like [[Nmap.md|Nmap]], [[Metasploit]], and [[Burp Suite]] for comprehensive assessments.

## References
- [Exploit-DB Website](https://www.exploit-db.com/)
- [SearchSploit GitHub Repository](https://github.com/offensive-security/exploitdb)
- [SearchSploit Usage](https://www.exploit-db.com/searchsploit)

