## Overview
Hydra is a fast and flexible network logon cracker which supports numerous protocols to attack. It is used by penetration testers and security researchers to identify weak passwords in network services.

## Features
- **Multiple Protocol Support:** Supports many protocols including HTTP, FTP, SMTP, MySQL, SSH, Telnet, and more.
- **Parallelized:** Highly efficient with support for parallel connections.
- **Customizable:** Allows for custom modules and easy integration with other tools.
- **Flexible:** Supports dictionary attacks and brute-force attacks.
- **Open Source:** Free and open-source tool available under the GPL license.

## Website
- [Hydra GitHub Repository](https://github.com/vanhauser-thc/thc-hydra)

## Installation

### On Unix-based systems (Linux/macOS):
1. **Install Dependencies:**
   - On Debian-based systems:
```sh
sudo apt-get install hydra
```
   - On macOS using Homebrew:
```sh
brew install hydra
```

2. **Compile from Source:**
```sh
git clone https://github.com/vanhauser-thc/thc-hydra.git
cd thc-hydra
./configure
make
sudo make install
```

### On Windows:
1. **Using Cygwin:**
   - Install Cygwin from [Cygwin website](https://cygwin.com/install.html).
   - During installation, select Hydra and its dependencies from the package list.

## Basic Usage
Hydra is run from the command line. Here are some common commands and usage examples:

### Brute Forcing FTP
To brute force an FTP server:
```sh
hydra -l username -P /path/to/password/list.txt ftp://target_ip
```

### Brute Forcing SSH
To brute force an SSH server:
```sh
hydra -l username -P /path/to/password/list.txt ssh://target_ip
```

### Brute Forcing HTTP Form
To brute force a web login form:
```sh
hydra -l username -P /path/to/password/list.txt target_ip http-post-form "/login:username=^USER^&password=^PASS^:F=incorrect"
```

### Brute Forcing Multiple Services
To brute force multiple services at once:
```sh
hydra -l username -P /path/to/password/list.txt target_ip ftp ssh http-get
```

## Advanced Options
Hydra offers several advanced options for more specific use cases:

### Specifying Ports
To specify a custom port for the service:
```sh
hydra -s 2222 -l username -P /path/to/password/list.txt ssh://target_ip
```

### Using a Proxy
To route the attack through a proxy:
```sh
hydra -l username -P /path/to/password/list.txt -o output.txt -t 4 -w 3 -F -e nsr -u target_ip ssh -s 2222 -I -L userlist.txt -P passlist.txt -p 22 -o outfile.txt -vV -X -I
```

### Detailed Output
To get verbose output and log results:
```sh
hydra -vV -l username -P /path/to/password/list.txt ssh://target_ip
```

## Best Practices
- **Use Legal Authorization:** Ensure you have permission to perform brute force attacks on the target system.
- **Use Strong Password Lists:** Use comprehensive and updated password lists to increase the chances of success.
- **Monitor Resources:** Be aware of the resource consumption and potential impact on the target system and network.
- **Combine with Other Tools:** Use Hydra in combination with other tools like [[Nmap.md|Nmap]], [[Metasploit]], and [[Burp Suite]] for comprehensive assessments.

## References
- [Hydra GitHub Repository](https://github.com/vanhauser-thc/thc-hydra)
- [Hydra Documentation](https://tools.kali.org/password-attacks/hydra)
- [SecTools.org - Hydra](https://sectools.org/tool/hydra/)

