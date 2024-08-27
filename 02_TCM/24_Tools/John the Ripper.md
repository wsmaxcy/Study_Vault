## Overview
John the Ripper (often abbreviated as "John") is an open-source password cracking tool. It is widely used by penetration testers, security researchers, and system administrators to detect weak passwords and improve security. John the Ripper can perform various types of password attacks, including dictionary attacks, brute force attacks, and rainbow table attacks. It supports numerous hashing algorithms, including MD5, SHA-1, NTLM, and many more.

## Features
- **Multiple Hash Types:** Supports a wide range of hash algorithms, including MD5, SHA-1, SHA-256, NTLM, and bcrypt.
- **Wordlist and Brute Force Attacks:** Performs dictionary-based and brute force password cracking.
- **Custom Rules:** Allows users to define custom rules for password mutations to enhance cracking efficiency.
- **GPU Acceleration:** Supports GPU acceleration for faster cracking using OpenCL and CUDA.
- **Modular Architecture:** Extensible with custom modules and plugins for additional functionality.

## Website
- [John the Ripper Official Website](https://www.openwall.com/john/)

## Installation

### On Unix-based systems (Linux/macOS):
1. **Install John the Ripper:**
   - On Debian-based systems:
     ```sh
     sudo apt-get install john
     ```
   - On Red Hat-based systems:
     ```sh
     sudo yum install john
     ```
   - On macOS using Homebrew:
     ```sh
     brew install john
     ```

2. **Build from Source:**
   - Clone the repository and compile:
   ```sh
   git clone https://github.com/openwall/john.git
   cd john/src
   ./configure && make
   ```

### On Windows:
1. **Download the Binary:**
   - Download the latest Windows binaries from the [John the Ripper Download Page](https://www.openwall.com/john/).

2. **Extract and Run:**
   - Extract the downloaded files and run `john.exe` from the command prompt.

## Basic Usage
John the Ripper is run from the command line. Here are some common commands and usage examples:

### Cracking a Password Hash
To crack a password hash using a default wordlist:
```sh
john --wordlist=/usr/share/wordlists/rockyou.txt hashfile.txt
```

### Specify a Hash Format
To specify a particular hash format (e.g., MD5):
```sh
john --format=raw-md5 --wordlist=/usr/share/wordlists/rockyou.txt hashfile.txt
```

### Perform a Brute Force Attack
To perform a brute force attack using all possible characters:
```sh
john --incremental hashfile.txt
```

### Resume a Cracking Session
To resume a previous cracking session:
```sh
john --restore=session_name
```

### Save Cracked Passwords to a File
To save the output of cracked passwords:
```sh
john --show hashfile.txt > cracked_passwords.txt
```

## Advanced Features
John the Ripper offers several advanced features for more specific use cases:

### Custom Wordlists
To use a custom wordlist:
```sh
john --wordlist=/path/to/custom_wordlist.txt hashfile.txt
```

### Rules for Wordlist Mutations
To apply custom rules to mutate words in the wordlist:
```sh
john --wordlist=/usr/share/wordlists/rockyou.txt --rules hashfile.txt
```

### GPU Acceleration
To use GPU acceleration for faster cracking:
1. **Build with GPU Support:**
   - Ensure you have OpenCL or CUDA installed, then compile John the Ripper with GPU support.

2. **Run John with GPU Acceleration:**
   ```sh
   john --format=raw-md5-opencl --wordlist=/usr/share/wordlists/rockyou.txt hashfile.txt
   ```

### Cracking Windows Passwords (NTLM)
To crack Windows NTLM password hashes:
```sh
john --format=NT hashfile.txt
```

### Show Cracked Passwords
To display cracked passwords:
```sh
john --show hashfile.txt
```

### Create a Custom Rule
To create a custom rule for John the Ripper, edit the `john.conf` file and add a new rule under the `[List.Rules:Wordlist]` section. For example:
```
[List.Rules:Wordlist]
Az"@ - Memory of rockyou.txt wordlist (capitalize first letter)
```
Then run John with the custom rule:
```sh
john --wordlist=/usr/share/wordlists/rockyou.txt --rules:Wordlist hashfile.txt
```

## Tools for Password Cracking Using John the Ripper

- **Weak Password Detection:** Use John to identify weak passwords within a set of user accounts to improve security posture.
- **Hash Cracking for Red Teaming:** During red team engagements, use John to crack password hashes obtained through credential dumping or network sniffing.
- **Password Recovery:** Recover lost or forgotten passwords by cracking the associated hash.
- **Vulnerability Assessment:** Assess the strength of passwords and password policies in use within an organization.

## Best Practices
- **Use Appropriate Wordlists:** Start with well-known wordlists like `rockyou.txt` and expand with custom lists tailored to the target.
- **Leverage GPU Acceleration:** Use GPU acceleration to speed up the cracking process significantly.
- **Combine Attack Types:** Use a combination of wordlist attacks with rules and brute force to maximize the chances of cracking passwords.
- **Monitor System Resources:** Password cracking can be resource-intensive; monitor CPU and GPU usage to avoid overheating or crashing the system.
- **Keep John Updated:** Regularly update John the Ripper to benefit from new cracking algorithms and features.
- **Combine with Other Tools:** Use John the Ripper alongside other password cracking tools like [[Hashcat]], [[Hydra]], and [[Cain and Abel]] for comprehensive assessments.

## References
- [John the Ripper Official Website](https://www.openwall.com/john/)
- [John the Ripper GitHub Repository](https://github.com/openwall/john)
- [Cracking Passwords with John the Ripper](https://www.kali.org/tools/john/)
- [John the Ripper Community Wiki](https://github.com/openwall/john/wiki)

