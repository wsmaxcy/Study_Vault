## File Transfer Protocol
## Overview
FTP (File Transfer Protocol) is a standard network protocol used to transfer files between a client and a server on a computer network. Although it is widely used for transferring files, FTP is known for its lack of security, as data, including credentials, are transmitted in plaintext. This makes FTP a common target for attackers who can exploit its vulnerabilities to gain unauthorized access to systems.

## Features
- **File Transfer:** Allows for uploading, downloading, renaming, deleting, and moving files on a remote server.
- **Anonymous Access:** Can be configured to allow anonymous users to access certain directories.
- **User Authentication:** Supports username and password authentication for access control.
- **Active and Passive Modes:** Supports both active and passive modes for file transfers.
- **Integration:** Commonly integrated into many operating systems and software applications.

## Website
- [RFC 959 - FTP](https://tools.ietf.org/html/rfc959)

## Common Vulnerabilities and Exploitation Techniques

### 1. **Cleartext Credentials**
   - **Description:** FTP transmits credentials in plaintext, making them easily intercepted by attackers using packet sniffers.
   - **Exploitation:**
     - **Tool:** [[Wireshark]]
     - **Technique:** Capture FTP traffic and filter for credentials:
     ```
     tcp.port == 21
     ```
   - **Mitigation:** Use secure alternatives like FTPS or SFTP, which encrypt credentials and data.

### 2. **Anonymous FTP Access**
   - **Description:** Some FTP servers are configured to allow anonymous access, potentially exposing sensitive files.
   - **Exploitation:**
     ```sh
     ftp anonymous@target_ip
     ```
   - **Technique:** Connect to the FTP server using the username `anonymous` and a random password, and list accessible directories and files.
   - **Mitigation:** Disable anonymous FTP access or restrict access to non-sensitive directories.

### 3. **Directory Traversal Attack**
   - **Description:** A vulnerability that allows attackers to access files and directories outside of the root folder by manipulating directory paths.
   - **Exploitation:**
     - **Tool:** [[Burp Suite]]
     - **Technique:** Manipulate FTP commands to traverse directories:
     ```
     RETR ../../../../etc/passwd
     ```
   - **Mitigation:** Properly configure FTP servers to restrict access to designated directories and validate file paths.

### 4. **Weak Permissions and Misconfigurations**
   - **Description:** Improper configuration of file and directory permissions can lead to unauthorized access and data exposure.
   - **Exploitation:**
     - **Tool:** [[Metasploit]]
     - **Module:** `unix/ftp/proftp_sploitshell`
   - **Technique:** Exploit misconfigured permissions to upload or modify sensitive files.
   - **Mitigation:** Regularly audit and enforce least privilege on file and directory permissions.

### 5. **Brute-Forcing FTP Credentials**
   - **Description:** Attackers use automated tools to guess username and password combinations to gain unauthorized access.
   - **Exploitation:**
     - **Tool:** [[Hydra]]
     - **Command:**
     ```sh
     hydra -l username -P /path/to/password_list.txt ftp://target_ip
     ```
   - **Mitigation:** Implement account lockout mechanisms and use strong, unique passwords.

### 6. **FTP Bounce Attack**
   - **Description:** An attack that exploits the PORT command in FTP to perform port scanning or connect to other hosts indirectly.
   - **Exploitation:**
     - **Tool:** [[Nmap.md|Nmap]]
     - **Command:**
     ```sh
     nmap -b anonymous:anonymous@target_ip -p 21 ftp-bounce
     ```
   - **Mitigation:** Disable FTP bounce by configuring the server to reject PORT commands to remote addresses.

## Tools for Exploiting FTP

- **[[Hydra]]:** Used to brute-force FTP credentials.
- **[[Nmap.md|Nmap]]:** Utilized for FTP bounce attacks and version detection.
- **[[Metasploit]]:** Provides various modules for exploiting FTP servers.
- **[[Wireshark]]:** Captures FTP traffic to intercept credentials and data.
- **[[FoxyProxy]]:** Assists in managing proxy settings while testing web applications with FTP components.

## Best Practices
- **Use Secure Alternatives:** Prefer FTPS (FTP Secure) or SFTP (SSH File Transfer Protocol) over FTP to ensure data and credentials are encrypted.
- **Disable Anonymous Access:** Disable anonymous access unless absolutely necessary, and restrict it to non-sensitive directories.
- **Enforce Strong Password Policies:** Use complex passwords and implement account lockout mechanisms to mitigate brute-force attacks.
- **Regular Audits and Updates:** Regularly audit FTP server configurations and update them to mitigate known vulnerabilities.
- **Monitor FTP Logs:** Regularly monitor FTP logs for unusual access patterns that may indicate an attempted attack or unauthorized access.

## References
- [RFC 959 - FTP](https://tools.ietf.org/html/rfc959)
- [NIST FTP Security Guidelines](https://csrc.nist.gov/publications/detail/sp/800-45/version-2/final)
- [OWASP FTP Security](https://owasp.org/www-community/attacks/FTP_Attacks)
- [Exploit-DB FTP Vulnerabilities](https://www.exploit-db.com/search?q=ftp)

