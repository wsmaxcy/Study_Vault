## Overview
`rockyou.txt` is a widely known wordlist used for password cracking and security testing. Originally created from the leaked passwords of the RockYou.com breach in 2009, this wordlist contains over 14 million common passwords. `rockyou.txt` has become a standard tool in cybersecurity for testing password strength, conducting penetration tests, and performing security audits.

The popularity of `rockyou.txt` in hacking and cybersecurity stems from its comprehensive compilation of real-world passwords, making it an effective tool for brute-force attacks, dictionary attacks, and password recovery.

## Features
- **Real-World Passwords:** Contains millions of passwords obtained from the RockYou.com breach, reflecting actual user choices.
- **Comprehensive Coverage:** Includes a wide variety of password types, including common passwords, names, phrases, and numbers.
- **Optimized for Cracking:** Ordered by frequency of use, making it more effective for quick dictionary attacks.
- **Widely Supported:** Compatible with many password-cracking tools, such as [[John the Ripper]], [[Hashcat]], [[Hydra]], and [[Cain and Abel]].

## Sources
- **Download Location:** `rockyou.txt` is included in many security distributions like Kali Linux. It can also be downloaded from various online repositories.
- **Kali Linux Path:** On Kali Linux, you can typically find `rockyou.txt` in the `/usr/share/wordlists/` directory. If it is not yet uncompressed, you can use the following command:
```sh
gunzip /usr/share/wordlists/rockyou.txt.gz
```

## Installation

### On Unix-based systems (Linux/macOS):
1. **Install `rockyou.txt` via Kali Linux (or other security distributions):**
   - `rockyou.txt` is usually pre-installed in `/usr/share/wordlists/`.

2. **Download Directly:**
   - Use `wget` or `curl` to download `rockyou.txt` directly:
```sh
wget https://github.com/brannondorsey/naive-hashcat/releases/download/data/rockyou.txt
```
   or
```sh
curl -O https://github.com/brannondorsey/naive-hashcat/releases/download/data/rockyou.txt
```

### On Windows:
1. **Download Directly from GitHub or Other Repositories:**
   - Use your browser to navigate to a repository hosting `rockyou.txt`, such as [this link](https://github.com/brannondorsey/naive-hashcat/releases/download/data/rockyou.txt).

2. **Extract if Necessary:**
   - If the file is compressed (`.gz`), extract it using a tool like 7-Zip or WinRAR.

## Basic Usage
`rockyou.txt` is used with many password-cracking tools for dictionary attacks. Here are some common commands and usage examples:

### Using rockyou.txt with John the Ripper
To use `rockyou.txt` with John the Ripper:
```sh
john --wordlist=/usr/share/wordlists/rockyou.txt hashfile.txt
```

### Using rockyou.txt with Hashcat
To use `rockyou.txt` with Hashcat:
```sh
hashcat -a 0 -m 0 hashfile.txt /usr/share/wordlists/rockyou.txt
```
- **`-a 0`**: Specifies the attack mode (0 = dictionary attack).
- **`-m 0`**: Specifies the hash type (0 = MD5, for example).

### Using rockyou.txt with Hydra
To use `rockyou.txt` with Hydra for online password attacks:
```sh
hydra -l username -P /usr/share/wordlists/rockyou.txt ssh://target_ip
```
- **`-l`**: Specifies the username.
- **`-P`**: Specifies the path to the wordlist.

## Key Features and Techniques

### Dictionary Attacks
- **Description:** `rockyou.txt` is primarily used for dictionary attacks, where each word in the wordlist is tried as a password to crack hashes or authenticate to services.
- **Effectiveness:** Due to the large number of common passwords included, it is often highly effective against weak passwords.

### Mask Attacks and Hybrid Attacks
- **Mask Attacks:** Combine `rockyou.txt` with masks to add additional characters, such as numbers or special symbols, to the passwords.
- **Hybrid Attacks:** Combine dictionary words with other cracking techniques, such as appending common suffixes, to increase the chances of finding a match.

### Password Recovery
- **Password Recovery Tools:** `rockyou.txt` is commonly used with password recovery tools to recover forgotten or lost passwords by matching hash values.

## Use Cases in Cybersecurity

- **Penetration Testing:** Assess the strength of passwords by simulating attacks using a wordlist that reflects common user behaviors.
- **Password Auditing:** Evaluate the effectiveness of password policies and enforce stronger passwords.
- **Credential Stuffing:** Test the reusability of leaked passwords across multiple platforms.
- **Training and Education:** Provide realistic examples in cybersecurity training and competitions to teach password-cracking techniques.

## Best Practices
- **Use for Authorized Testing Only:** Always ensure that you have permission before using `rockyou.txt` for password cracking or penetration testing.
- **Keep Wordlists Updated:** Supplement `rockyou.txt` with additional wordlists to cover specific targets or add more recent passwords.
- **Combine with Other Attacks:** Use `rockyou.txt` alongside rule-based attacks, masks, or hybrid techniques to increase cracking effectiveness.
- **Use Responsibly:** Avoid using `rockyou.txt` for unauthorized access or malicious purposes.
- **Store Securely:** Keep sensitive wordlists secure and limit access to authorized personnel.

## References
- [RockYou Password List (GitHub)](https://github.com/brannondorsey/naive-hashcat/releases/download/data/rockyou.txt)
- [Using rockyou.txt for Password Cracking](https://www.hackingarticles.in/rockyou-txt-file-password-cracking/)
- [Password Cracking Tools Comparison](https://www.offensive-security.com/metasploit-unleashed/password-attacks/)

