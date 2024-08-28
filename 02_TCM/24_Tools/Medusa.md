## Overview
**Medusa** is a powerful, fast, and flexible password-cracking tool designed for brute-force attacks on remote authentication services. It is commonly used by penetration testers, security researchers, and ethical hackers to assess the strength of passwords and authentication mechanisms across various protocols. Medusa is highly versatile and supports a wide range of protocols, including HTTP, FTP, SSH, SMTP, Telnet, and more. With its modular architecture, Medusa can be extended to include additional protocols and customized for specific needs.

Medusa is optimized for speed and parallelism, allowing it to perform multiple attacks simultaneously. It can be configured to target multiple hosts, usernames, and passwords, making it an effective tool for large-scale password auditing.

## Features
- **Multi-Protocol Support:** Supports numerous protocols, such as HTTP, FTP, SSH, Telnet, SMTP, and more.
- **Parallelism and Speed:** Optimized for high-speed, parallel brute-force attacks.
- **Modular Architecture:** Allows for easy addition of new protocols and customization for specific attack scenarios.
- **Flexible Targeting:** Can target multiple hosts, usernames, and passwords simultaneously.
- **Input File Support:** Supports input files for usernames, passwords, and targets, making it easy to automate large-scale attacks.
- **Cross-Platform Compatibility:** Available on Unix-based systems (Linux, macOS) and can be compiled for Windows.

## Website
- [Medusa GitHub Repository](https://github.com/jmk-foofus/medusa)

## Installation

### On Unix-based systems (Linux/macOS):

1. **Install Medusa via Package Manager:**

   - **On Debian-based systems:**

```sh
sudo apt-get install medusa
```

   - **On macOS using Homebrew:**

```sh
brew install medusa
```

2. **Install via GitHub:**

   - Clone the Medusa repository from GitHub:

```sh
git clone https://github.com/jmk-foofus/medusa.git
cd medusa
```

   - Compile and install Medusa:

```sh
./configure
make
sudo make install
```

### On Windows:

1. **Download Medusa:**

   - Download the Medusa source code from the [GitHub repository](https://github.com/jmk-foofus/medusa).

2. **Compile Medusa:**

   - Use a compatible C compiler (such as MinGW or Cygwin) to compile Medusa for Windows.

3. **Run Medusa:**

   - Open Command Prompt, navigate to the directory where Medusa is compiled, and run `medusa.exe`.

## Basic Usage
Medusa is a flexible tool that can perform brute-force attacks on various services. Here are some common commands and usage examples:

### Brute-Force Attack on an SSH Server
To perform a brute-force attack on an SSH server:

```sh
medusa -h <target-ip> -u username -P /path/to/passwordlist.txt -M ssh
```

- **`-h <target-ip>`**: Specifies the target IP address.
- **`-u username`**: Specifies the username to attack.
- **`-P /path/to/passwordlist.txt`**: Specifies the path to the password list file.
- **`-M ssh`**: Specifies the module to use (in this case, SSH).

### Brute-Force Attack on an FTP Server
To perform a brute-force attack on an FTP server:

```sh
medusa -h <target-ip> -U /path/to/userlist.txt -P /path/to/passwordlist.txt -M ftp
```

- **`-U /path/to/userlist.txt`**: Specifies the path to the user list file.
- **`-P /path/to/passwordlist.txt`**: Specifies the path to the password list file.
- **`-M ftp`**: Specifies the module to use (in this case, FTP).

### Brute-Force Attack on a Web Login
To perform a brute-force attack on a web login form:

```sh
medusa -h <target-ip> -U /path/to/userlist.txt -P /path/to/passwordlist.txt -M http -m DIR:/login.php -m FORM:"user=^USER^&pass=^PASS^:F=incorrect"
```

- **`-m DIR:/login.php`**: Specifies the directory path to the login form.
- **`-m FORM:"user=^USER^&pass=^PASS^:F=incorrect"`**: Specifies the form fields and failure message for the web login form.

### Brute-Force Attack with Multiple Hosts
To perform a brute-force attack on multiple hosts:

```sh
medusa -H /path/to/hostlist.txt -U /path/to/userlist.txt -P /path/to/passwordlist.txt -M ssh
```

- **`-H /path/to/hostlist.txt`**: Specifies the path to the host list file.

### Specifying Number of Parallel Threads
To specify the number of parallel threads for the attack:

```sh
medusa -h <target-ip> -u username -P /path/to/passwordlist.txt -M ssh -t 10
```

- **`-t 10`**: Specifies the number of parallel threads (10 in this example).

### Verbose Mode
To enable verbose output during the attack:

```sh
medusa -h <target-ip> -u username -P /path/to/passwordlist.txt -M ssh -v 6
```

- **`-v 6`**: Sets verbosity level to 6 for detailed output.

## Key Features and Commands

### Brute-Force Attack
- **Description:** Performs brute-force attacks on remote authentication services to test password strength and identify weak credentials.
- **Usage:**
```sh
medusa -h <target-ip> -u username -P /path/to/passwordlist.txt -M ssh
```

### Multi-Protocol Support
- **Description:** Supports multiple protocols, including SSH, FTP, HTTP, Telnet, SMTP, and more, for versatile password cracking.
- **Usage:**
```sh
medusa -h <target-ip> -U /path/to/userlist.txt -P /path/to/passwordlist.txt -M ftp
```

### Parallelism and Speed
- **Description:** Optimized for high-speed attacks with parallelism, allowing multiple simultaneous connections to target services.
- **Usage:**
```sh
medusa -h <target-ip> -u username -P /path/to/passwordlist.txt -M ssh -t 10
```

### Customizable Attacks
- **Description:** Provides customizable options for targeting specific authentication mechanisms, such as web login forms and directory paths.
- **Usage:**
```sh
medusa -h <target-ip> -U /path/to/userlist.txt -P /path/to/passwordlist.txt -M http -m DIR:/login.php -m FORM:"user=^USER^&pass=^PASS^:F=incorrect"
```

### Input File Support
- **Description:** Supports input files for usernames, passwords, and targets, making it easy to automate large-scale attacks.
- **Usage:**
```sh
medusa -H /path/to/hostlist.txt -U /path/to/userlist.txt -P /path/to/passwordlist.txt -M ssh
```

### Verbose Mode
- **Description:** Provides detailed output during attacks, helping users to monitor progress and analyze results.
- **Usage:**
```sh
medusa -h <target-ip> -u username -P /path/to/passwordlist.txt -M ssh -v 6
```

## Tools for Password Cracking and Security Testing Using Medusa

- **Password Auditing:** Use Medusa to audit passwords across various services and identify weak or compromised credentials.
- **Security Compliance:** Test the strength of authentication mechanisms to ensure compliance with organizational security policies.
- **Penetration Testing:** Perform brute-force attacks on exposed services to evaluate the resilience of authentication systems.
- **Data Recovery:** Assist in recovering lost or forgotten passwords for services and accounts.
- **Performance Benchmarking:** Benchmark different authentication mechanisms and hardware setups to optimize performance for large-scale password cracking.

## Best Practices
- **Use Medusa Responsibly:** Always ensure that you have proper authorization before using Medusa for password cracking or security testing.
- **Stay Within Legal Boundaries:** Be aware of the legal implications of using password-cracking tools and ensure compliance with local laws and regulations.
- **Combine with Other Tools:** Use Medusa alongside other password-cracking tools like [[John the Ripper]], [[Hydra]], and [[Hashcat]] for comprehensive assessments.
- **Regularly Update Medusa:** Keep Medusa up-to-date to benefit from the latest features, security enhancements, and bug fixes.
- **Use Strong Passwords:** Encourage the use of strong, complex passwords to reduce the risk of unauthorized access.

## References
- [Medusa GitHub Repository](https://github.com/jmk-foofus/medusa)
- [Medusa Documentation](https://github.com/jmk-foofus/medusa/blob/master/README.md)
- [Medusa Tutorial for Brute-Force Attacks](https://www.hackingarticles.in/medusa-tutorial-for-brute-force-attacks/)
- [Medusa Cheat Sheet](https://highon.coffee/blog/medusa-cheat-sheet/)
- [Using Medusa for Password Cracking](https://null-byte.wonderhowto.com/how-to/use-medusa-brute-force-password-cracker-0197641/)

