## Overview
DirB is a command-line tool designed to brute force directories and files on web servers. It helps penetration testers find hidden resources by using wordlists to scan for directory and file names. DirB is known for its simplicity, speed, and effectiveness.

## Features
- **Fast and Simple:** Easy to use with a command-line interface.
- **Custom Wordlists:** Supports custom wordlists for directory and file name brute forcing.
- **Recursive Scanning:** Can recursively scan directories and subdirectories.
- **File Extension Brute Forcing:** Allows brute forcing of multiple file extensions.
- **Proxy Support:** Supports scanning through a proxy server.
- **HTTP Status Codes:** Displays HTTP status codes for better analysis.

## Website
- [DirB GitHub Repository](https://github.com/v0re/dirb)

## Installation

### On Unix-based systems:
1. **Install DirB:**
```sh
sudo apt-get install dirb
```

### On macOS using Homebrew:
1. **Install Homebrew (if not already installed):**
```sh
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```

2. **Install DirB:**
```sh
brew install dirb
```

### On Windows using Cygwin:
1. **Install Cygwin from [Cygwin website](https://cygwin.com/install.html)**.
2. **Install DirB via Cygwin setup:**
   - During the installation, select DirB from the package list.

## Basic Usage
DirB is run from the command line. Here are some common commands:

### Basic Scan
```sh
dirb http://example.com
```

### Use a Custom Wordlist
```sh
dirb http://example.com /path/to/wordlist.txt
```

### Scan with File Extensions
```sh
dirb http://example.com -X .php,.html,.txt
```

### Recursive Scanning
```sh
dirb http://example.com -r
```

### Save Output to a File
```sh
dirb http://example.com -o output.txt
```

### Scan Through a Proxy
```sh
dirb http://example.com -p http://proxyserver:port
```

## Advanced Options
DirB offers several options for more advanced usage:

### Using HTTP Headers
Specify custom HTTP headers in the request:
```sh
dirb http://example.com -H "User-Agent: MyCustomUserAgent"
```

### Custom HTTP Methods
Use a custom HTTP method for the scan:
```sh
dirb http://example.com -X POST
```

### Brute Force with Additional Extensions
Combine multiple file extensions and wordlists:
```sh
dirb http://example.com -X .php,.html -w /path/to/wordlist.txt
```

## Best Practices
- **Use Relevant Wordlists:** Choose wordlists that are relevant to the target application to increase the chances of finding hidden directories and files.
- **Analyze HTTP Status Codes:** Focus on HTTP status codes that indicate the presence of valid resources (e.g., 200, 301, 302).
- **Adjust Scan Intensity:** Be mindful of the number of requests to avoid overloading the target server.
- **Combine with Other Tools:** Use DirB in combination with other scanning tools like [[Nmap.md|Nmap]], [[Burp Suite]], and [[WhatWeb.md|WhatWeb]] for comprehensive assessments.

## References
- [DirB GitHub Repository](https://github.com/v0re/dirb)
- [DirB Official Documentation](https://tools.kali.org/web-applications/dirb)
- [SecTools.org - DirB](https://sectools.org/tool/dirb/)
