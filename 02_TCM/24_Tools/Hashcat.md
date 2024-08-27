## Overview
Hashcat is a powerful password-cracking tool that leverages the processing power of CPUs and GPUs to perform highly optimized attacks against hashed passwords. Known as one of the fastest and most versatile password crackers available, Hashcat supports a wide range of hashing algorithms and attack modes, making it a favorite among penetration testers, cybersecurity professionals, and hackers for cracking passwords and recovering encrypted data.

## Features
- **Support for Multiple Hash Types:** Hashcat supports numerous hash algorithms, including MD5, SHA-1, SHA-256, NTLM, bcrypt, and more.
- **Multi-Device Support:** Can utilize both CPU and GPU (via OpenCL or CUDA) for increased speed and efficiency.
- **Various Attack Modes:** Supports multiple attack modes, including brute force, dictionary, mask, hybrid, and rule-based attacks.
- **Cross-Platform:** Runs on Linux, Windows, and macOS.
- **Highly Configurable:** Offers extensive configuration options to fine-tune attacks for specific needs.

## Website
- [Hashcat Official Website](https://hashcat.net/hashcat/)

## Installation

### On Unix-based systems (Linux/macOS):
1. **Install Hashcat:**
   - On Debian-based systems:
```sh
sudo apt-get install hashcat
```
   - On Red Hat-based systems:
     ```sh
sudo yum install hashcat
     ```
   - On macOS using Homebrew:
```sh
brew install hashcat
```

2. **Build from Source:**
   - Clone the repository and compile:
```sh
git clone https://github.com/hashcat/hashcat.git
cd hashcat
make
sudo make install
```

### On Windows:
1. **Download the Binary:**
   - Download the latest Windows binaries from the [Hashcat Download Page](https://hashcat.net/hashcat/).

2. **Extract and Run:**
   - Extract the downloaded files and run `hashcat.exe` from the command prompt.

## Basic Usage
Hashcat is run from the command line interface (CLI). Here are some common commands and usage examples:

### Cracking a Password Hash with a Wordlist
To crack a password hash using a dictionary attack with a wordlist (e.g., `rockyou.txt`):
```sh
hashcat -m 0 -a 0 -o cracked.txt hash.txt /usr/share/wordlists/rockyou.txt
```
- **`-m 0`**: Specifies the hash type (0 = MD5).
- **`-a 0`**: Specifies the attack mode (0 = dictionary attack).
- **`-o cracked.txt`**: Output file to save cracked passwords.
- **`hash.txt`**: File containing hashes to crack.
- **`/usr/share/wordlists/rockyou.txt`**: Path to the wordlist file.

### Brute Force Attack
To perform a brute force attack using all possible characters:
```sh
hashcat -m 1000 -a 3 hash.txt ?a?a?a?a?a
```
- **`-m 1000`**: Specifies the hash type (1000 = NTLM).
- **`-a 3`**: Specifies the attack mode (3 = brute force).
- **`?a?a?a?a?a`**: Mask specifying the password length and character set (?a = all characters).

### Rule-Based Attack
To perform a rule-based attack:
```sh
hashcat -m 0 -a 0 -r rules/best64.rule hash.txt /usr/share/wordlists/rockyou.txt
```
- **`-r rules/best64.rule`**: Specifies a rules file to use for the attack.

### Hybrid Attack
To perform a hybrid attack combining a wordlist and mask:
```sh
hashcat -m 0 -a 6 hash.txt /usr/share/wordlists/rockyou.txt ?d?d?d
```
- **`-a 6`**: Specifies the hybrid attack mode (6 = wordlist + mask).

### Resume a Cracking Session
To resume a previous cracking session:
```sh
hashcat --session=session_name --restore
```

## Key Features and Options

### Hash Types Supported
Hashcat supports various hash algorithms, including:
- **MD5 (0):** Commonly used for simple checksums and file verification.
- **SHA-1 (100):** A slightly more secure hashing algorithm, but still vulnerable to attacks.
- **SHA-256 (1400):** A more secure version of SHA-1, widely used for digital signatures and certificates.
- **NTLM (1000):** Commonly used in Windows environments for password hashing.
- **bcrypt (3200):** A password hashing function designed to be computationally expensive, making it resistant to brute-force attacks.

### Attack Modes
Hashcat supports several attack modes, including:
- **Dictionary Attack (`-a 0`):** Uses a wordlist to guess passwords.
- **Combinator Attack (`-a 1`):** Combines two wordlists to form potential passwords.
- **Brute Force Attack (`-a 3`):** Tries all possible combinations of characters.
- **Mask Attack (`-a 3`):** Uses masks to specify character sets and positions.
- **Hybrid Attack (`-a 6` and `-a 7`):** Combines a dictionary with a mask.

### Using Masks
Masks are used to define character sets and lengths for brute force or hybrid attacks:
- **`?l`**: Lowercase letters (a-z)
- **`?u`**: Uppercase letters (A-Z)
- **`?d`**: Digits (0-9)
- **`?s`**: Special characters (!, @, #, etc.)
- **`?a`**: All characters (lowercase, uppercase, digits, and special characters)

### Optimizing Performance
To optimize performance using GPU acceleration:
1. **Select the Best OpenCL or CUDA Device:**
```sh
hashcat -I
```
2. **Run Hashcat on Specific Device:**
```sh
hashcat -m 0 -a 0 -d 1 hash.txt /usr/share/wordlists/rockyou.txt
```

### Saving and Restoring Sessions
To save a session for later resumption:
```sh
hashcat --session=mycrack -m 0 -a 0 hash.txt /usr/share/wordlists/rockyou.txt
```
To restore a session:
```sh
hashcat --session=mycrack --restore
```

## Tools for Password Cracking Using Hashcat

- **Password Recovery:** Use Hashcat to recover lost or forgotten passwords by cracking the associated hash.
- **Weak Password Detection:** Identify weak passwords within a set of user accounts to improve security posture.
- **Penetration Testing:** Crack password hashes obtained through credential dumping or network sniffing during penetration tests.
- **Vulnerability Assessment:** Assess the strength of passwords and password policies in use within an organization.

## Best Practices
- **Use Appropriate Wordlists:** Start with well-known wordlists like `rockyou.txt` and expand with custom lists tailored to the target.
- **Leverage GPU Acceleration:** Use GPU acceleration to speed up the cracking process significantly.
- **Combine Attack Types:** Use a combination of wordlist attacks with rules and brute force to maximize the chances of cracking passwords.
- **Monitor System Resources:** Password cracking can be resource-intensive; monitor CPU and GPU usage to avoid overheating or crashing the system.
- **Keep Hashcat Updated:** Regularly update Hashcat to benefit from new cracking algorithms and features.
- **Combine with Other Tools:** Use Hashcat alongside other password-cracking tools like [[John the Ripper]], [[Hydra]], and [[RainbowCrack]] for comprehensive assessments.

## References
- [Hashcat Official Website](https://hashcat.net/hashcat/)
- [Hashcat GitHub Repository](https://github.com/hashcat/hashcat)
- [Hashcat Wiki and Documentation](https://hashcat.net/wiki/)
- [Hashcat Example Hashes](https://hashcat.net/wiki/doku.php?id=example_hashes)

