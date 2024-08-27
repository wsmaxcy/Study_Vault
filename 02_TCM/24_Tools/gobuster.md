## Overview
Gobuster is a tool used to brute force URIs (directories and files) in web sites and DNS subdomains. It is fast, written in Go, and can be used for directory/file busting and DNS subdomain enumeration.

## Features
- **Fast and efficient:** Written in Go, allowing for high performance.
- **Directory/File Brute Forcing:** Finds hidden directories and files on web servers.
- **DNS Subdomain Enumeration:** Identifies subdomains by brute forcing.
- **Custom Wordlists:** Supports custom wordlists for brute forcing.
- **Recursive Scanning:** Can recursively scan directories and subdirectories.
- **TLS/SSL Support:** Handles HTTPS URLs.
- **Proxy Support:** Supports scanning through a proxy server.

## Website
- [Gobuster GitHub Repository](https://github.com/OJ/gobuster)

## Installation

### On Unix-based systems:
1. **Install Go (if not already installed):**
```sh
sudo apt-get install golang
```

2. **Install Gobuster:**
```sh
go install github.com/OJ/gobuster/v3@latest
```

3. **Verify Installation:**
   Ensure `gobuster` is in your PATH. You can check by running:
```sh
gobuster -h
```

### On Windows:
1. **Install Go (if not already installed):**
   - Download and install Go from [golang.org](https://golang.org/).

2. **Install Gobuster:**
```sh
go install github.com/OJ/gobuster/v3@latest
```

3. **Verify Installation:**
   Ensure `gobuster` is in your PATH. You can check by running:
```sh
gobuster -h
```

## Basic Usage
Gobuster is run from the command line. Here are some common commands:

### Directory/File Brute Forcing
```sh
gobuster dir -u http://example.com -w /path/to/wordlist.txt
```

### DNS Subdomain Enumeration
```sh
gobuster dns -d example.com -w /path/to/wordlist.txt
```

### Use a Custom Wordlist
```sh
gobuster dir -u http://example.com -w /path/to/custom_wordlist.txt
```

### Scan with File Extensions
```sh
gobuster dir -u http://example.com -w /path/to/wordlist.txt -x php,html,txt
```

### Recursive Scanning
```sh
gobuster dir -u http://example.com -w /path/to/wordlist.txt -r
```

### Save Output to a File
```sh
gobuster dir -u http://example.com -w /path/to/wordlist.txt -o output.txt
```

### Scan Through a Proxy
```sh
gobuster dir -u http://example.com -w /path/to/wordlist.txt -p http://proxyserver:port
```

## Advanced Options
Gobuster offers several options for more advanced usage:

### Using HTTP Headers
Specify custom HTTP headers in the request:
```sh
gobuster dir -u http://example.com -w /path/to/wordlist.txt -H "User-Agent: MyCustomUserAgent"
```

### Custom HTTP Methods
Use a custom HTTP method for the scan:
```sh
gobuster dir -u http://example.com -w /path/to/wordlist.txt -m POST
```

### Verbose Output
To get more detailed output:
```sh
gobuster dir -u http://example.com -w /path/to/wordlist.txt -v
```

## Best Practices
- **Use Relevant Wordlists:** Choose wordlists that are relevant to the target application to increase the chances of finding hidden directories and files.
- **Analyze HTTP Status Codes:** Focus on HTTP status codes that indicate the presence of valid resources (e.g., 200, 301, 302).
- **Adjust Scan Intensity:** Be mindful of the number of requests to avoid overloading the target server.
- **Combine with Other Tools:** Use Gobuster in combination with other scanning tools like [[Nmap.md|Nmap]], [[Burp Suite]], and [[WhatWeb.md|WhatWeb]] for comprehensive assessments.

## References
- [Gobuster GitHub Repository](https://github.com/OJ/gobuster)
- [Gobuster Documentation](https://github.com/OJ/gobuster/wiki)
