## Overview
**John the Ripper Jumbo** (often referred to simply as "John the Ripper" or "John") is an open-source password cracking tool that is widely used by security professionals, penetration testers, and cybersecurity researchers. The "Jumbo" version is a community-enhanced version that includes additional features, patches, and support for various hash types not found in the standard version. John the Ripper Jumbo is designed to detect weak passwords and ensure compliance with security policies by testing password hashes using various cracking methods, including brute-force, dictionary, and hybrid attacks.

The tool supports a wide range of hash and cipher types, making it versatile for cracking passwords across multiple platforms and applications, such as UNIX, Windows, macOS, ZIP files, and more.

## Features
- **Supports Multiple Hash Types:** Cracks passwords using various hash types, including MD5, SHA-1, SHA-256, bcrypt, and more.
- **Dictionary and Brute-Force Attacks:** Performs both dictionary-based and brute-force attacks to crack passwords.
- **Hybrid Attacks:** Combines dictionary and brute-force methods for more efficient password cracking.
- **Incremental Mode:** Uses character sets and rules to generate passwords in a highly optimized manner.
- **Customizable Rules and Masks:** Allows users to create custom rules and masks for targeted password cracking.
- **GPU Acceleration:** Supports cracking with GPU acceleration using OpenCL and CUDA for faster performance.
- **Multi-Platform Support:** Available on Unix-based systems (Linux, macOS) and Windows environments.

## Website
- [John the Ripper Jumbo GitHub Repository](https://github.com/openwall/john)

## Installation

### On Unix-based systems (Linux/macOS):

1. **Install John the Ripper Jumbo via GitHub:**

   - Clone the John the Ripper Jumbo repository from GitHub:

```sh
git clone https://github.com/openwall/john.git
cd john/src
```

2. **Compile John the Ripper Jumbo:**

   - Run the following commands to compile:

```sh
./configure
make -s clean && make -sj4
```

   - The `make -sj4` command uses four cores to speed up the compilation process. Adjust the number (`4`) according to your CPU.

3. **Run John the Ripper Jumbo:**

   - You can now run `john` from the `run` directory:

```sh
cd ../run
./john
```

### On Windows:

1. **Download John the Ripper Jumbo:**

   - Download the pre-built binaries from the [John the Ripper website](https://www.openwall.com/john/).

2. **Extract the ZIP File:**

   - Extract the ZIP file to a directory of your choice.

3. **Run John the Ripper Jumbo:**

   - Open Command Prompt, navigate to the directory where you extracted John, and run `john.exe`:

```cmd
john.exe
```

## Basic Usage
John the Ripper Jumbo can perform various types of attacks to crack passwords. Here are some common commands and usage examples:

### Cracking Passwords with a Dictionary Attack
To perform a dictionary attack on a password file:

```sh
./john --wordlist=/path/to/wordlist.txt /path/to/passwordfile
```

- **`--wordlist=/path/to/wordlist.txt`**: Specifies the path to the wordlist file.
- **`/path/to/passwordfile`**: Specifies the path to the file containing hashed passwords.

### Cracking Passwords with a Brute-Force Attack
To perform a brute-force attack:

```sh
./john /path/to/passwordfile
```

- This command uses John’s default mode (incremental) to perform a brute-force attack.

### Cracking Passwords with a Hybrid Attack
To perform a hybrid attack combining dictionary and brute-force methods:

```sh
./john --wordlist=/path/to/wordlist.txt --rules /path/to/passwordfile
```

- **`--rules`**: Applies rules to modify words in the wordlist (e.g., appending numbers or symbols).

### Resume a Cracking Session
To resume a previously interrupted session:

```sh
./john --restore
```

- **`--restore`**: Resumes the last session from where it left off.

### Cracking Passwords with GPU Acceleration
To use GPU acceleration for cracking:

```sh
./john --format=sha256crypt-opencl /path/to/passwordfile
```

- **`--format=sha256crypt-opencl`**: Specifies the format for GPU-accelerated cracking (adjust format as needed).

### Listing Supported Hash Formats
To list all supported hash formats in John the Ripper Jumbo:

```sh
./john --list=formats
```

- **`--list=formats`**: Lists all hash formats supported by John.

## Key Features and Commands

### Dictionary Attack
- **Description:** Uses a wordlist to attempt to crack passwords by testing each word against the hashes.
- **Usage:**
```sh
./john --wordlist=/path/to/wordlist.txt /path/to/passwordfile
```

### Brute-Force Attack
- **Description:** Uses incremental mode to attempt to crack passwords by testing all possible combinations within a defined character set.
- **Usage:**
```sh
./john /path/to/passwordfile
```

### Hybrid Attack
- **Description:** Combines dictionary and brute-force methods by applying rules to words in a wordlist to generate additional candidates.
- **Usage:**
```sh
./john --wordlist=/path/to/wordlist.txt --rules /path/to/passwordfile
```

### GPU Acceleration
- **Description:** Utilizes GPU acceleration through OpenCL or CUDA to speed up the password cracking process significantly.
- **Usage:**
```sh
./john --format=sha256crypt-opencl /path/to/passwordfile
```

### Resuming Sessions
- **Description:** Allows users to resume a cracking session from where it left off, preventing the loss of progress.
- **Usage:**
```sh
./john --restore
```

### Listing Supported Formats
- **Description:** Lists all the hash formats that John the Ripper Jumbo supports, helping users to identify the correct format for cracking.
- **Usage:**
```sh
./john --list=formats
```

## Tools for Password Cracking and Security Testing Using John the Ripper Jumbo

- **Password Auditing:** Use John the Ripper Jumbo to audit password hashes from various systems and applications to identify weak or compromised passwords.
- **Security Compliance:** Ensure compliance with organizational password policies by testing for easily crackable passwords.
- **Digital Forensics:** Assist in digital forensic investigations by recovering passwords from seized devices and data.
- **Data Recovery:** Recover lost or forgotten passwords for personal files, archives, and accounts.
- **Performance Benchmarking:** Benchmark different password cracking methods and hardware setups to optimize performance.

## Best Practices
- **Use John the Ripper Responsibly:** Always ensure that you have proper authorization before using John the Ripper for password cracking or security testing.
- **Stay Within Legal Boundaries:** Be aware of the legal implications of using password cracking tools and ensure compliance with local laws and regulations.
- **Combine with Other Tools:** Use John the Ripper Jumbo alongside other password recovery tools like [[Hashcat]], [[Hydra]], and [[Medusa]] for comprehensive assessments.
- **Regularly Update John the Ripper:** Keep John the Ripper Jumbo up-to-date to benefit from the latest features, security enhancements, and bug fixes.
- **Use Strong Passwords:** Encourage the use of strong, complex passwords to reduce the risk of unauthorized access.

## References
- [John the Ripper Jumbo GitHub Repository](https://github.com/openwall/john)
- [John the Ripper Documentation](https://www.openwall.com/john/)
- [John the Ripper Jumbo Tutorial](https://null-byte.wonderhowto.com/how-to/crack-passwords-john-ripper-0195087/)
- [John the Ripper Cheat Sheet](https://highon.coffee/blog/john-the-ripper-cheat-sheet/)
- [Using John the Ripper for Password Cracking](https://www.hackingarticles.in/comprehensive-guide-on-john-the-ripper-for-password-cracking/)

