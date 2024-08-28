## Overview
Fcrackzip is a fast, command-line utility designed for cracking password-protected ZIP archives. It is commonly used by penetration testers, security researchers, and digital forensic experts to recover lost or forgotten passwords on ZIP files. Fcrackzip uses brute-force and dictionary attacks to test various password combinations against the ZIP file until the correct one is found.

Fcrackzip supports several encryption methods used in ZIP files, including traditional PKZIP encryption and WinZip AES encryption, making it a versatile tool for ZIP file password recovery.

## Features
- **Brute-Force Attack:** Attempts to crack ZIP passwords by trying all possible combinations of characters.
- **Dictionary Attack:** Uses a wordlist to test passwords against the ZIP file for faster password recovery.
- **Customizable Character Sets:** Allows users to specify custom character sets for brute-force attacks.
- **Supports Multiple Encryption Methods:** Works with both traditional ZIP encryption and WinZip AES encryption.
- **Cross-Platform Compatibility:** Available for Unix-based systems (Linux, macOS) and Windows environments.
- **Speed Optimization:** Optimized for speed to efficiently crack passwords on ZIP files.

## Website
- [Fcrackzip GitHub Repository](https://github.com/hyc/fcrackzip)

## Installation

### On Unix-based systems (Linux/macOS):

1. **Install Fcrackzip via Package Manager:**

   - **On Debian-based systems:**

```sh
sudo apt-get install fcrackzip
```

   - **On macOS using Homebrew:**

```sh
brew install fcrackzip
```

2. **Install via GitHub:**

   - Clone the Fcrackzip repository from GitHub:

```sh
git clone https://github.com/hyc/fcrackzip.git
cd fcrackzip
```

   - Compile and install Fcrackzip:

```sh
./configure
make
sudo make install
```

### On Windows:

1. **Download Fcrackzip:**

   - Download the Fcrackzip executable from a trusted source or compile it from the [GitHub repository](https://github.com/hyc/fcrackzip).

2. **Run Fcrackzip:**

   - Open the command prompt and navigate to the directory where the executable is located.
   - Run `fcrackzip` using the command line.

## Basic Usage
Fcrackzip can perform both brute-force and dictionary attacks to recover passwords from ZIP files. Here are some common commands and usage examples:

### Brute-Force Attack
To perform a brute-force attack on a password-protected ZIP file:

```sh
fcrackzip -b -c a1 -l 1-8 -u file.zip
```

- **`-b`**: Specifies a brute-force attack.
- **`-c a1`**: Specifies the character set (lowercase letters and digits).
- **`-l 1-8`**: Specifies the length range of the passwords to try (from 1 to 8 characters).
- **`-u`**: Uses the unzip command to test each password (useful for checking if the password works).
- **`file.zip`**: Specifies the ZIP file to crack.

### Dictionary Attack
To perform a dictionary attack using a wordlist:

```sh
fcrackzip -D -p wordlist.txt -u file.zip
```

- **`-D`**: Specifies a dictionary attack.
- **`-p wordlist.txt`**: Specifies the path to the wordlist file.
- **`-u`**: Uses the unzip command to test each password.
- **`file.zip`**: Specifies the ZIP file to crack.

### Customizing Character Sets
To use a custom character set for a brute-force attack:

```sh
fcrackzip -b -c aA1! -l 1-6 -u file.zip
```

- **`-c aA1!`**: Specifies a custom character set (lowercase letters, uppercase letters, digits, and special characters).

### Specifying Password Length
To specify a fixed password length:

```sh
fcrackzip -b -c a1 -l 5 -u file.zip
```

- **`-l 5`**: Specifies that the password length is exactly 5 characters.

### Parallel Cracking
To use multiple cores or processes for cracking:

```sh
fcrackzip -b -c a1 -l 1-8 -u file.zip -m 4
```

- **`-m 4`**: Uses 4 threads for parallel processing.

## Key Features and Commands

### Brute-Force Attack
- **Description:** Attempts to crack ZIP passwords by testing all possible combinations within a specified character set and length.
- **Usage:**
```sh
fcrackzip -b -c a1 -l 1-8 -u file.zip
```

### Dictionary Attack
- **Description:** Uses a provided wordlist to attempt to crack ZIP passwords by testing each word against the file.
- **Usage:**
```sh
fcrackzip -D -p wordlist.txt -u file.zip
```

### Custom Character Sets
- **Description:** Allows users to specify custom character sets for more targeted brute-force attacks.
- **Usage:**
```sh
fcrackzip -b -c aA1! -l 1-6 -u file.zip
```

### Specifying Password Length
- **Description:** Allows users to specify a fixed password length or range for more efficient brute-force attacks.
- **Usage:**
```sh
fcrackzip -b -c a1 -l 5 -u file.zip
```

### Parallel Processing
- **Description:** Supports multi-threading for parallel processing to speed up the cracking process.
- **Usage:**
```sh
fcrackzip -b -c a1 -l 1-8 -u file.zip -m 4
```

## Tools for Password Cracking and Security Testing Using Fcrackzip

- **Password Recovery:** Use Fcrackzip to recover lost or forgotten passwords for ZIP files by performing brute-force or dictionary attacks.
- **Security Testing:** Evaluate the strength of passwords used to protect ZIP files and identify weak or default passwords that could be easily cracked.
- **Data Forensics:** Utilize Fcrackzip in digital forensic investigations to access ZIP files that may contain critical evidence or information.
- **Backup Auditing:** Test the security of ZIP archives used in backup processes to ensure that sensitive data is adequately protected.
- **Compliance and Policy Enforcement:** Verify that ZIP files within an organization adhere to password policies and standards for data security.

## Best Practices
- **Use Fcrackzip Responsibly:** Always ensure that you have proper authorization before using Fcrackzip for password recovery or security testing.
- **Stay Within Legal Boundaries:** Be aware of the legal implications of using password cracking tools and ensure compliance with local laws and regulations.
- **Combine with Other Tools:** Use Fcrackzip alongside other password recovery tools like [[John the Ripper]], [[Hashcat]], and [[Aircrack-ng]] for comprehensive assessments.
- **Regularly Update Fcrackzip:** Keep Fcrackzip up-to-date to benefit from the latest features, security enhancements, and bug fixes.
- **Use Strong Passwords:** Encourage the use of strong, complex passwords to protect ZIP files and reduce the risk of unauthorized access.

## References
- [Fcrackzip GitHub Repository](https://github.com/hyc/fcrackzip)
- [Fcrackzip Documentation](https://github.com/hyc/fcrackzip/blob/master/README.md)
- [Cracking ZIP Passwords with Fcrackzip](https://null-byte.wonderhowto.com/how-to/crack-passwords-zip-files-using-fcrackzip-0182099/)
- [Fcrackzip Cheat Sheet](https://highon.coffee/blog/fcrackzip-cheat-sheet/)
- [Fcrackzip Tutorial for Password Recovery](https://www.hackingarticles.in/cracking-zip-passwords-using-fcrackzip/)

