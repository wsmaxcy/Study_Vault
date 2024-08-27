## Overview
Nikto is an open-source web server scanner that performs comprehensive tests against web servers for multiple items, including over 6700 potentially dangerous files/CGIs, checks for outdated versions of over 1250 servers, and version-specific problems on over 270 servers. It is a valuable tool for web security assessments and penetration testing.

## Features
- Scans for over 6700 potentially dangerous files/CGIs
- Checks for outdated versions of over 1250 servers
- Identifies version-specific problems on over 270 servers
- Scans for server configuration issues
- Supports SSL
- Proxy support (with or without authentication)
- Reports in various formats including plain text, HTML, XML, and CSV

## Installation
Nikto can be installed on most Unix-based systems and Windows using Cygwin. The installation steps are as follows:

### On Unix-based systems:
1. **Update package list and install dependencies:**
```sh
sudo apt-get update
sudo apt-get install perl libnet-ssleay-perl libwhisker2-perl
```

2. **Download Nikto:**
```sh
git clone https://github.com/sullo/nikto.git
cd nikto/program
```

3. **Run Nikto:**
```sh
perl nikto.pl -h example.com
```

### On Windows using Cygwin:
1. **Install Cygwin from [Cygwin website](https://cygwin.com/install.html)**.
2. **During installation, ensure the following packages are selected:**
   - `perl`
   - `git`
   - `wget`

3. **Open Cygwin terminal and follow the Unix-based system steps from above**.

## Basic Usage
Nikto is run from the command line. Here are some common commands:

### Basic Scan
```sh
perl nikto.pl -h example.com
```

### Save Output to File
```sh
perl nikto.pl -h example.com -o outputfile.txt
```

### Scan Specific Port
```sh
perl nikto.pl -h example.com -p 8080
```

### Use SSL
```sh
perl nikto.pl -h example.com -ssl
```

### Scan Multiple Hosts
```sh
perl nikto.pl -h host1.com,host2.com,host3.com
```

### Scan with Proxy
```sh
perl nikto.pl -h example.com -useproxy http://proxyserver:port
```

## Advanced Options
Nikto offers a wide range of options for more advanced usage. Some key options include:

### Tuning Options
Specify the type of tests to include or exclude in the scan:
```sh
perl nikto.pl -h example.com -Tuning x
```
Where `x` is a string of numbers:
- `0` - File Upload
- `1` - Interesting File / Seen in logs
- `2` - Misconfiguration / Default File
- `3` - Information Disclosure
- `4` - Injection (XSS/Script/HTML)
- `5` - Remote File Retrieval – Inside Web Root
- `6` - Denial of Service
- `7` - Remote File Retrieval – Server Wide
- `8` - Command Execution / Remote Shell
- `9` - SQL Injection
- `a` - Authentication Bypass
- `b` - Software Identification
- `c` - Remote Source Inclusion
- `d` - Web Service
- `e` - Administrative Consoles
- `x` - Reverse Tuning Options (exclude the specified types)

### Reporting Options
Nikto supports various report formats:

#### HTML
```sh
perl nikto.pl -h example.com -Format html -output report.html
```

#### CSV
```sh
perl nikto.pl -h example.com -Format csv -output report.csv
```

#### XML
```sh
perl nikto.pl -h example.com -Format xml -output report.xml
```

### Plugin Options
Nikto can be extended with plugins. To list available plugins:
```sh
perl nikto.pl -list-plugins
```

To run a specific plugin:
```sh
perl nikto.pl -h example.com -Plugins plugin_name
```

## Best Practices
- **Run regular scans** to identify new vulnerabilities as they arise.
- **Combine with other tools**: Use Nikto in conjunction with other tools like Nmap for comprehensive assessments.
- **Update regularly**: Keep Nikto and its databases updated to ensure the latest checks are performed.
- **Review results carefully**: Not all findings are critical, so assess the impact and prioritize remediation accordingly.

## References
- [Nikto GitHub Repository](https://github.com/sullo/nikto)
- [Nikto Official Documentation](https://cirt.net/Nikto2)
